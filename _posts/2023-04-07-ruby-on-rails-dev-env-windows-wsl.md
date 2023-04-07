---
layout: post
title: Ambiente de desenvolvimento Ruby on Rails usando o Windows + WSL
tags:
- beginner
- wsl
- dev
- ruby
---
A primeira barreira de aprendizado do Ruby é a dificuldade de instalar o ambiente de desenvolvimento
na computador do desenvolvedor que usa Windows. Isso é especialmente mais crítico no caso de iniciantes.

Algumas dependências populares do Ruby, e do Rails, tem um  historico de complicações
para instalar no Windows. O que levava a muito programador mais experientes orientar aos iniciantes
a simplesmente instalar um Linux. E, aceitar como taxa pra usar Ruby. ¯\\_(ツ)_/¯

Com o advento do [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/about)
é possível ter um Linux rodando no Windows. Resolvendo a necessidade de migrar para outro Sistema Operacional.

Nesse texto eu procuro explicar como instalar o ambiente de desenvolvimento Ruby on Rails no Windows
usando o WSL. A alternativa é um dual-boot ou uso de ferramentas de vitualização que exige a instalação
e configuração do Sistema Operacional Linux.

Tem esse canal do YouTube que tem o video [How I Run Rails 7 On Windows 11 | Ruby On Rails WSL With GUI Setup Guide](https://youtu.be/Hwou03YqH4I).
Mas, o lance de rodar as coisas como root me incomodou ao ponto de me motivar a escrever esse texto.

O resumo do processo é:

{:toc}
1. TOC


# Habilitar o WLS no Windows

1. Clique no botão iniciar e busque por "Ativar ou Desativar recursos do Windows"
1. Habilite as seguintes funcionalidades:
  - Virtual Machine Platform
  - Windows Hypervisor Platform
  - Windows Subsystem for Linux
1. Reinicie o computador
1. Abra o terminal e define a versão padrão do WSL para a 2
  - `$ wsl.exe --set-default-version 2`

# Instalar o Windows Terminal

Acessa a Windows Store e busca por "Windows Terminal". Que é um emulador de terminal que vou usar pra acessar a parte Linux do sistema.

# Instalar uma distribuição Linux(aqui eu vou usar o Debian)

Depois que o WSL é instalado você tem disponíveis algumas distribuições Linux na Window Store como aplicativos.

1. Acesse a Windows Store e busca por Debian
1. Clique no botão de instalar
1. Aguarde terminar de baixar e instalar o sistema
1. Clique em abrir. Ele vai abrir usando o Windows Terminal
  1. Aqui pode mostrar um erro `0x800701bc`. Basta seguir as instruções de acessar o link [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel), instalar e reiniciar a máquina.
1. Ao abrir o console com o Debian ele vai pedir pra criar um usuário e senha.
1. Depois de confirmar a senha ele vai finalizar a instalação e te deixar no bash. Nesse momento você já tem um Linux pronto pra usar. \o/

# Instalar as dependências do Sistema Operacional

Com o sistema operacional vitualizado, agora precisamos das ferramentas de desenvolvimento. Que por sua vez possuem algumas dependências.
Nessa sessão eu pretento colocar todas as dependências de uma vez. Caso escolha outra Distribuição Linux esse passo aqui vai ser diferente.

{% highlight bash %}
$ sudo apt update
$ sudo apt install gpg gnupg2 curl git postgresql libpq-dev bash-completion
{% endhighlight %}

Dependências:

| Ferramenta  | Depende do pacote      |
| ---         | ---                    |
| RVM         | gpg, gnupg2, curl, git |
| PostgreSQL  | postgresql             |
| Gem pg      | libpq-dev              |



# Configurar o PostgreSQL

O Postgres foi instalado no passo de dependências. Eu costumo configurar a versão de desenvolvimento da aplicação para usar o nome do usuário
logado na máquina como usuário do Postgres. Assim, evita de compartilhar senha entre a equipe. Pra isso, basta criar um usuário com o mesmo
nome do usuário logado.


## Criar o usuário e dar permissão

E, para criar a base e carregar fixtures é necessário que o usuário tenha permissão SUPERUSER.

{% highlight bash %}
$ sudo service postgresql start
$ sudo -u postgres psql -c "CREATE ROLE `whoami` WITH LOGIN SUPERUSER"
{% endhighlight %}

O `whoami` vai passar o nome do usário logado para a query no `psql`.

## Mudar o encoding padrão para UTF8

Encoding é um problema recorrente. Especialmente pra quem vem de um idioma com acentuação.
Facilita muito a vida se você [mudar o encoding padrão do PostgreSQL pra UTF8](https://www.shubhamdipt.com/blog/how-to-change-postgresql-database-encoding-to-utf8/) e seguir a vida.

{% highlight sql %}
$ sudo -u postgres psql
postgres=# UPDATE pg_database SET datistemplate = FALSE WHERE datname = 'template1';
postgres=# DROP DATABASE template1;
postgres=# CREATE DATABASE template1 WITH TEMPLATE = template0 ENCODING = 'UTF8';
postgres=# UPDATE pg_database SET datistemplate = TRUE WHERE datname = 'template1';
postgres=# \c template1;
You are now connected to database "template1" as user "postgres".
template1=# VACUUM FREEZE;
template1=# \q
{% endhighlight %}



# Instalar o RVM

De acordo com a [página de instalação do RVM](https://rvm.io/rvm/install):

Pra evitar erro de SSL com o RubyGems instala esses certificados e atualiza o RubyGems

{% highlight bash %}
$ gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
$ gpg2 --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
$ gpg2 --refresh-keys
$ gem update --system
{% endhighlight %}

Agora, instala o RVM:

{% highlight bash %}
$ \curl -sSL https://get.rvm.io | bash
{% endhighlight %}

Ao tentar acessar o RVM vai dizer que não existe. Abre uma aba nova do Window Terminal que vai estar lá.
É que precisa executar novamente o `~/.bashrc`. Por isso que funciona na nova aba.


## Instalar uma versão do Ruby

Esse passo depende do projeto que você está trabalhando. No exemplo, aqui estou usando a versão 3.2.2

{% highlight bash %}
$ rvm install ruby-3.2.2
{% endhighlight %}

O RVM vai tentar instalar qualquer dependência do sistema operacional que ainda não esteja instalada.
Se você abriu uma nova aba do Window Terminal, vai precisar digitar a senha de `sudo` novamente.



# Pronto \o/

A partir daqui o ambiente está pronto pra clonar o projeto com o git, instalar dependências específicas como NodeJS,
criar a base de dados, as tabelas, subir as fixtures e rodar o servidor.

- Faltou alguma coisa? Alguma sugestão de melhoria?
- Sabe alguma forma mais fácil de lidar com o erro de SSL da RubyGems?
- Alguma forma de instalar o PostgreSQL já em UTF8?
- Precisa de um [projeto para testar a configuração do ambiente Ruby on Rails](https://github.com/acdesouza/demo_rails_7)?
