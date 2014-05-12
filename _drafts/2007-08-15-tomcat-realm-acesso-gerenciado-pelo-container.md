---
layout: post
title: Tomcat Realm: Controle de acesso gerenciado pelo Container Web
tags:
- beginner
- java
- tomcat
---
Neste exemplo explicarei como configurar uma aplicação web para ser
autenticada pelo Container Web, que neste texto será o Tomcat.
Caso você use outro, dá olhada em como fazer um Realm nele.

ATUALIZADO para o [Tomcat 8](http://tomcat.apache.org/tomcat-8.0-doc/index.html)

Vou aproveitar o post do Urubatan ensinando como fazer um login com JSF para explicar como delegar, para o container web, o serviço de autenticação e autorização.

Ah?! Como assim, o que é um Realm?
<conceito>
Realm: é uma base de dados que contém a informação de usuário, senha e as roles deste usuário no sistema
</conceito>

Não sabe o que é role?
<conceito>
Role: Lembra da parte de modelagem de sistema? Mais precisamente, lembra da definição dos casos de uso? Lembram que para executar um UC é necessário informar o ator que o executa? Ótimo. Cada um desses atores é uma role, ou melhor, um papel que um usuário precisa ter para executar o UC.
</conceito>

Para começar, vou demonstrar a configuração de um Realm do Tomcat. O Realm que eu estou usando prevê que os dados estão em um banco de dados relacional, neste caso o PostgreSQL. Para isso é necessário a criação das tabelas no postgre.
-------------------------------------------------------------------------------------------------------------
tabela_usuario
------------------
coluna_login texto ficará o nome do usuário
coluna_senha texto ficará a senha do usuário

tabela_roles
------------------
coluna_nome_role texto ficará o nome da role
coluna_login texto ficará o nome do usuário com acesso a role
-------------------------------------------------------------------------------------------------------------
Não precisa de uma tabela de roles, porque as roles são fixas, lembra? Elas representam os atores do caso de uso, certo?
Eu sei (cof) que, às vezes, (cof, cof) não dá tempo de fazer casos de uso(cof, cof, cof). Então pega o caderno, onde você escreveu a analise do sistema, e vê quem é que pode executar esta funcionalidade. Simples, não?

Neste caso, o ream Esta configuração deve ficar em um arquivo chamado context.xml na pasta META-INF, que fica na raiz do seu WAR:

/META-INF/context.xml -------------------------------------------------------------------------

<?xml version="1.0" encoding="utf-8"?>
<Context displayName="reteste" reloadable="true">
<Resource name="jdbc/stripessec"
auth="Container"
type="javax.sql.DataSource"
maxActive="10"
maxIdle="3"
username="nome_de_usuario_do_banco"
password="senha_do_usuario_do_banco"
driverClassName="org.postgresql.Driver"
url="jdbc:postgresql://localhost:5432/database_criado_no_postgre"/>

<Realm className="org.apache.catalina.realm.DataSourceRealm" debug="99"
dataSourceName="jdbc/stripessec" localDataSource="true"
userTable="tabela_usuario"
userNameCol="coluna_login"
userCredCol="coluna_senha"
userRoleTable="table_permissao"
roleNameCol="coluna_nome_permissao" />

</Context>
---------------------------------------------------------------------------------------------

No exempo eu criei um DataSource, para um database no banco PostgreSQL, que também servirá para o resto da aplicação. E criei um Realm JDBC. Que, basicamente é falar o quais as tabelas e quais as colunas que representa os usuários e as permissões dele.

Depois do context.xml criado, escrevo, no web.xml, as informações necessárias para a aplicação usar o Realm e o DataSource:

/WEB-INF/web.xml --------------------------------------------------------------------------

<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="http://java.sun.com/xml/ns/j2ee"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee
http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"
version="2.4">

<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
<!-- Configuração do DataSource. -->
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
<resource-ref>
<description>Web Database</description>
<res-ref-name>jdbc/stripessec</res-ref-name>
<res-type>javax.sql.DataSource</res-type>
<res-auth>Container</res-auth>
</resource-ref>

<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
<!-- Configuração da autenticação e autorização. -->
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

<security-constraint>
<display-name>Área Restrita</display-name>
<web-resource-collection>
<web-resource-name>Arquivos protegidos por login</web-resource-name>
<url-pattern>/jsp/*</url-pattern>
</web-resource-collection>
<auth-constraint>
<role-name>systemuser</role-name>
</auth-constraint>
</security-constraint>
<login-config>
<auth-method>FORM</auth-method>
<realm-name>StripesSecRealm</realm-name>
<form-login-config>
<form-login-page>/login.jsp</form-login-page>
<form-error-page>/error.jsp</form-error-page>
</form-login-config>
</login-config>
<security-role>
<role-name>systemuser</role-name>
</security-role>

</web-app>

---------------------------------------------------------------------------------------------

Estou disponibilizando o DataSource para o resto da aplicação e declarando o Realm, com configurado para proibir o acesso, para usuário não autenticados, aos arquivos dentro da pasta jsp, que por sua vez está na raiz do WAR. Aqui é um bom lugar para colocar uma URL comum as Actions do seu framework MVC, desta forma o acesso a elas também será proibido.

Estas são as páginas de login e de erro, respectivamente, que ficarão na raiz do meu WAR:

/login.jsp -----------------------------------------------------------------------------------
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<html lang="pt-br">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />

<title>.:: Autenticação ::.</title>

</head>
<body>
<form method="POST" action="<%= response.encodeURL("j_security_check") %>" >
<fieldset title="Informe login e senha">
<legend>Login</legend>

<label for="j_username">Login:</label>
<input type="text" name="j_username" class="textBox"/><br/>

<label for="j_password">Senha:</label>
<input type="password" name="j_password" class="textBox"/><br/>

</fieldset>
<p align="center">
<input type="submit" value="Log In"/>
</p>
</form>
</body>
</html>
---------------------------------------------------------------------------------------------

Notem a falta total de TagLibs. Se não fosse a preocupação em garantir que vai funcionar, independente do contexto em que será feito o deploy, poderia ser um arquivo HTML.



/error.jsp ------------------------------------------------------------------------------------

<html
<head>
<title>Erro ao tentar autenticar usuário</title>
</head>
<body>

<p>

Usuário ou senha inválidos.<br/>

Verifique o nome de usuário e a senha e <a href="<%= response.encodeURL("login.jsp") %>">tente novamente</a>.

</p>

</body>
</html>

---------------------------------------------------------------------------------------------

Outra vantagem é que mesmo que seja tentado acessar a url diretamente, o container irá redirecionar para a página de login.

Após a autenticação, o container se encarrega de abrir a URL solicitada inicialmente. Este comportamento é perfeito para permitir seus usuários a colocar as partes do sistema que ele mais utiliza em seus favoritos(a.k.a. bookmarks).



Esta é a página protegida pelo Realm. :
/jsp/home.jsp -------------------------------------------------------------------------------
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
</head>
<body>
<h1>Página protegida pelo Realm.</h1>
</body>
</html>
---------------------------------------------------------------------------------------------
Para acessar esta página, o usuário precisa da permissão "systemuser", isto é, no banco de dados, na tabela de associação entre o usuário e as roles tem que ter o login dele e o systemuser como role.

Para essa autenticação, a única dependência é o driver JDBC para o PostgreSQL, neste caso, na pasta $TOMCAT_HOME/common/lib.

Alguma sugestão de melhoria nas explicações? Ficou alguma dúvida?
Poderiam contribuir com formas de burlar esta autenticação? Se elas existirem?
Alguma outra sugestão para o texto?
Atualmente eu tenho usado a autenticação apenas em meus freelances, uma vez que no trabalho a aplicação é desktop. Mais um motivo para eu preferir aplicações web... :D

P.S.: Caso dê alguma caca neste post, dá um desconto, porque é o primeiro que eu publico usando o Google Docs :)

