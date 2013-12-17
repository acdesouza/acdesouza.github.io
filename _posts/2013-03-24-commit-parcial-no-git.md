---
layout: post
title: Commit parcial no Git
tags:
- skilled
- git
---
Sabe quando você está alterando um arquivo e chega em um ponto que gostaria de fazer o commit de apenas parte do arquivo?
Então, o Git possui uma funcionalidade chamada Interactive Staging que pode te ajudar.

Usando o parâmetro -i o git irá executar o add no modelo interativo.


Usarei como exemplo o arquivo.txt. Nele eu removi uma linha e adicionei duas. E, eu farei commit apenas da remoção da linha,
ignorando a adição das duas linhas.

{% highlight bash %}
$ git add arquivo.txt -i
{% endhighlight %}

Como resposta ele irá apresentar os comandos disponíveis:

{% highlight bash %}
           staged     unstaged path
  1:    unchanged       +2/-1 arquivo.txt

*** Commands ***
  1: status	  2: update	  3: revert	  4: add untracked
  5: patch	  6: diff	  7: quit	  8: help
What now>
{% endhighlight %}

Escolhendo o comando 5

{% highlight bash %}
What now> 5
{% endhighlight %}

O git irá te perguntar qual arquivo você quer adicionar, parcialmente, no stage.

{% highlight bash %}
           staged     unstaged path
  1:    unchanged       +2/-1 arquivo.txt
Patch update>>
{% endhighlight %}

Selecione o arquivo que você irá adicionar, no stage, informando o número do arquivo. No caso, só tenho um arquivo para adicionar.

{% highlight bash %}
patch update>> 1
{% endhighlight %}

Selecionado o arquivo o git mostra sua seleção

{% highlight bash %}
           staged     unstaged path
* 1:    unchanged        +2/-1 Gemfile
Patch update>>
{% endhighlight %}

Neste ponto, precione a tecla Enter para o ser apresentado a primeira diferença do arquivo e decidir o que fazer com ela.

{% highlight bash %}
diff --git a/arquivo.txt b/arquivo.txt
index 5199dfd..aa2b489 100644
--- a/arquivo.txt
+++ b/arquivo.txt
@@ -1,1 +1,1 @@
-Linha deletada
+Primeira linha adicionada
+Segunda linha adicionada
Stage this hunk [y,n,q,a,d,/,s,e,?]?
{% endhighlight %}

Se você observar ele está mostrando as duas alterações feitas:
 * Remoção da linha 1
 * Adição das linhas 2 e 3

Como você que adicionar, apenas, a remoção da linha 1, vamos pedir ao git que separe as duas alterações, opção: "s".

{% highlight bash %}
Stage this hunk [y,n,q,a,d,/,s,e,?]? s
{% endhighlight %}

Esta opção fará o git responder com a primeira modificação, isto é, a remoção da primeira linha:

{% highlight bash %}
Split into 2 hunks.
@@ -1,1 +1,1 @@
-Linha deletada
Stage this hunk [y,n,q,a,d,/,j,J,g,e,?]?
{% endhighlight %}

Para adicionar essa modificação selecionamos a opção: "y"

{% highlight bash %}
Stage this hunk [y,n,q,a,d,/,s,e,?]? s
{% endhighlight %}

Assim, o git adiciona a modificação e apresenta a próxima, no caso a
adição das duas linhas:

{% highlight bash %}
@@ -2,2 +1,3 @@
+Primeira linha adicionada
+Segunda linha adicionada
Stage this hunk [y,n,q,a,d,/,K,g,e,?]?
{% endhighlight %}

A adição das duas linhas podem ser divididas, mas neste caso, não irei
adicionar essa modificação.
Para sair iremos usar a opção: "q", para sair da adição interativa do
arquivo.txt e depois usar o "q", de novo, para sair da adição interativa.

Assim, o git adiciona a modificação e apresenta a próxima, no caso a
adição das duas linhas:

{% highlight bash %}
@@ -2,2 +1,3 @@
+Primeira linha adicionada
+Segunda linha adicionada
Stage this hunk [y,n,q,a,d,/,K,g,e,?]? q

*** Commands ***
  1: status	  2: update	  3: revert	  4: add untracked
  5: patch	  6: diff	  7: quit	  8: help
What now> q
Bye.
$
{% endhighlight %}

Feito isso, se você não tiver adicionado todas as diferenças no stage, o git
status irá informar que o arquivo arquivo.txt está no stage e está modificado.

Pronto!

Agora temos apenas parte do arquivo adicionado no stage, usando
a adição interativa ao stage do git.

Fonte:

 * [Git's Interactive Staging](http://git-scm.com/book/en/Git-Tools-Interactive-Staging)
