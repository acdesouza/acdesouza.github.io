---
layout: post
title: Git - Guia para apressados
tags:
- beginner
- git
---
Escrevi este texto para ajudar um Time, em que trabalhei,
durante a adoção do Git.
Procuro ser bem direto sobre o uso da ferramenta. A idéia é descrever
o cenário de uso e o comando que atende ao cenário.

# Apresentar-se para o Git

Depois de instalado, o Git espera que você configure seu usuário e email.

{% highlight bash %}
$ git config --global user.name "Antonio Carlos da Graça Mota Durão de Souza"
$ git config --global user.email "acdesouza@example.com"
{% endhighlight %}

  * O que fazer se eu esqueci de me apresentar, e acabei de commitar?

{% highlight bash %}
$ git commit --amend --reset-author
{% endhighlight %}

# Criar um repositório novo

{% highlight bash %}
$ git init
{% endhighlight %}

# Controlando as modificações no repositório

## Preparando o commit

O git tem o conceito de stage, que é o buffer onde se prepara o commit.
Sendo assim, para gravar uma versão dos arquivos,
devemos adicioná-los ao stage.

{% highlight bash %}
$ git add caminho_para_arquivo
{% endhighlight %}

Caso deseje remover um arquivo, para informar esta remoção, ao git use:

{% highlight bash %}
$ git rm caminho_para_arquivo
{% endhighlight %}

### Ops! Adicionei quem não devia

Para remover um arquivo do stage, use:

{% highlight bash %}
$ git reset caminho_para_o_arquivo
{% endhighlight %}

### Desistindo de uma modificação, não versionada

Caso não tenha feito um commit, você ainda pode desfazer as modificações
feitas desde o último commit.

#### Reverter as modificações feitas em um arquivo já versionado

{% highlight bash %}
$ git checkout path_para_o_arquivo
{% endhighlight %}

#### Reverter todas as modificações feitas em todos os arquivo já versionados

{% highlight bash %}
$ git checkout .
{% endhighlight %}

#### Remover arquivos criados, que não estejam versionados, e não serão mais necessários.

{% highlight bash %}
$ git clean -df
{% endhighlight %}

## Versionar as modificações, adicionadas ao stage - Commit

{% highlight bash %}
$ git commit -m "Mensagem de commit"
{% endhighlight %}

### Fiz besteira no último commit! /o\

Existem alguns casos em que é interessante desfazer um commit. Mas, lembre-se
de só desfazer commits que não foram publicados para o Time. Neste caso, faça
um novo commit revertendo as mudanças.

__Nunca faça isso para commits que já foram publicados por git push.__

### Para desfazer, o último commit e voltar as alterações para o stage:

{% highlight bash %}
$ git reset HEAD~1 --soft
{% endhighlight %}

### Para desfazer, de vez, o último commit:

Observe que esse comando irá mudar o histórico de commits apagando o último
commit, como se este nunca tivesse sido feito.

{% highlight bash %}
$ git reset HEAD~1 --hard
{% endhighlight %}

#### Apaguei um commit que não devia /o\

Então, queria apagar um commit, daí usei o "git reset --hard HEAD~1"

Só que apaguei o commit errado. Como eu recupero um commit apagado?

  * Liste as últimas ações no repositório local, o que inclui o commit apagado.
    {% highlight bash %}
    $ git reflog
    85a1f7d HEAD@{0}: reset: moving to HEAD~1
    ade91cd HEAD@{1}: commit: Escreve alguma coisa em a.txt <--- É esse que quero recuperar
    85a1f7d HEAD@{2}: commit (initial): Cria o primeiro arquivo
    {% endhighlight %}
  * Encontre o commit perdido, pela mensagem de commit.
    E, copiar o sha1 que o representa, é a primeira coluna na lista do reflog.
  * Para recuperar o commit perdido, será necessário fazer um cherry-pick
    {% highlight bash %}
    $ git cherry-pick ade91cd
    $ git reflog
    d2da560 HEAD@{0}: cherry-pick: Escreve alguma coisa em a.txt
    85a1f7d HEAD@{1}: reset: moving to HEAD~1
    ade91cd HEAD@{2}: commit: Escreve alguma coisa em a.txt
    85a1f7d HEAD@{3}: commit (initial): Cria o primeiro arquivo
    {% endhighlight %}

Pronto! Commit recuperado.

# Compartilhando as modificações com o Time

Neste caso, o Time decidiu que teriam um repositório comum,
para compartilhar o código.

Para enviar suas modificações para esse local remoto, use:

{% highlight bash %}
git push
{% endhighlight %}


E, é isso. Esses são os fluxos básicos pelos quais um usuário deverá passar
ao usar o git no dia-dia.
