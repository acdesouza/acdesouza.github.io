---
layout: post
title: Como usar o vim como ferramenta de diff do git
tags:
- beginners
- git
- vim
- vimdiff
---
Como fazer git diff, ou merge, de forma gráfica?
Como colocar os arquivos, ou versões deles, lado a lado para ver as diferenças?
O [Vim](http://www.vim.org/), e sua funcionalidade vimdiff, pode fazer isso por você.
Veja como configurar o git para exibir as diferenças no arquivo lado-a-lado.

O git permite que você defina qual a ferramenta será usada para fazer o diff:

{% highlight bash %}
git difftool --tool=vimdiff --no-prompt
{% endhighlight %}

Para definir o vimdiff como a ferramenta padrão de diff:

{% highlight bash %}
git config --global diff.tool vimdiff
git config --global difftool.prompt false
git config --global alias.d difftool
{% endhighlight %}

Assim, toda vez que você quiser ver as diferenças usando o vimdiff, use o comando:

{% highlight bash %}
git difftool
{% endhighlight %}

Ok. Metade do planeta já perguntou como fazer isso.

 * http://usevim.com/2012/03/21/git-and-vimdiff/
 * http://stackoverflow.com/questions/3713765/viewing-all-git-diffs-with-vimdiff
 * http://amjith.blogspot.com.br/2008/08/quick-and-dirty-vimdiff-tutorial.html



Ah.... Mas, eu não quero escrever isso tudo. Quero abrir direto usando o git diff! :(
Aaff.. O-k... :/

Para isso, você usará a opção external diff helper. Para isso crie um arquivo,
no seu $PATH, que será usado pelo git. E, dê permissão de execução para ele
No meu caso irei criar o arquivo "git_diff_external_helper_vimdiff" no diretório
"/usr/local/bin"

{% highlight bash %}
cat > /usr/local/bin/git_diff_external_helper_vimdiff <<CONTEUDO
#!/bin/sh

# $2 - BASE.....: Original file
# $5 - MERGED...: Workspace file
vimdiff "$2" "$5"
CONTEUDO

chmod +x /usr/local/bin/git_diff_external_helper_vimdiff
{% endhighlight %}

Agora edita o ~/.gitconfig para usar esse arquivo que acabamos de criar.

Para isso, adicione, na seção [diff] a linha:

```
external = git_diff_external_helper_vimdiff
```

E, adicione a seção [pager], para evitar o erro: the output is not to a terminal

```
[pager]
  diff =
```

No final, seu ~/.gitconfig deve ficar assim:

```
# Deve ter alguma coisa por aqui...
[diff]
  external = git_diff_external_helper_vimdiff
# Pode ter mais alguma coisa por aqui...
[pager]
  diff =
```

Pronto! A partir de agora, seu git diff irá abrir o vimdiff e colocar as duas
versões do arquivo lado-a-lado para comparar.

De onde eu tiro essas coisas?

 * http://technotales.wordpress.com/2009/05/17/git-diff-with-vimdiff/
