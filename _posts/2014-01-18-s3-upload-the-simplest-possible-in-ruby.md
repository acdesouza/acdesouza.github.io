---
layout: post
title: "S3 Upload: the simplest possible in Ruby"
tags:
- beginner
- ruby
- aws
- s3
- iam
---
Seguindo a [série de artigos que visam mostrar a forma mais simples de subir um arquivo para a Amazon S3 em diferentes linguagens e tecnologias](http://blog.rivendel.com.br/tag/s3-upload/).
Neste artigo vou mostrar como fazer usando Ruby. Ruby, não Rails. Esse é o próximo artigo. ;)

Para a versão TL;DR, [fork no github](https://github.com/acdesouza/ruby-s3-simplest).

A forma mais simples, presupõe que teremos a menor quantidade de dependências
no projeto. Por conta disso achei justo fazer uma [aplicação Rack](http://rack.rubyforge.org/doc/Rack/Builder.html)

Neste caso teremos duas dependências, que não estão no Ruby:

  * [Rack](http://rack.github.io/)
    * [Rack Wiki, no github](https://github.com/rack/rack/wiki)
  * [aws-sdk]()

Como eu tenho carinho com meus projetos, eu declarei as dependências em um Gemfile
e, uso o [Bundler para colocar as gems no "classpath" da aplicação](http://bundler.io/v1.5/bundler_setup.html) Rack.

A [AWS-SDK em ruby](http://aws.amazon.com/documentation/sdkforruby/) é uma gem,
criada pela Amazon, para acessar os seus serviços de forma simplificada.

A [documentação do aws-sdk](http://docs.aws.amazon.com/AWSRubySDK/latest/frames.html)
descreve todos os módulos disponíveis.

Neste artigo irei utilizar o modulo [AWS::S3](http://docs.aws.amazon.com/AWSRubySDK/latest/AWS/S3.html),
que é o client para o serviço Amazon S3.

# Recebendo um arquivo usando Ruby.

A página com o formulário, não tem nada de mais. Ela é simples, o suficiente,
para ser apenas um arquivo html.

{% highlight html %}
<form action="upload" method="post" enctype="multipart/form-data">
  <input type="file" name="arquivo_para_upload" />
  <input type="submit" value="Enviar"/>
</form>
{% endhighlight %}

O campo file, deste formulário, quando enviado, irá gerar o seguinte parâmetro:

{% highlight ruby %}
{
  "arquivo_para_upload" => {
    :filename => "earth.jpg",
    :type     => "image/jpeg",
    :name     => "file",
    :tempfile => #,
    :head     => "Content-Disposition: form-data; name=\"file\"; filename=\"earth.jpg\"\r\nContent-Type: image/jpeg\r\n"
  }
}
{% endhighlight %}

Basicamente, o Rack se encarrega de criar um arquivo temporário e te dá uma
forma trivial de recuperar o arquivo. Basta acessar o valor, pela Hash:

{% highlight ruby %}
request.params["arquivo_para_upload"][:tempfile]
{% endhighlight %}

# Enviando para o Amazon S3

Para mandar o arquivo enviado para a Amazon S3, usamos o arquivo temporário,
criado pelo Rack ao receber a requisição POST com o form multi-part.
Mas, antes temos que fazer o login e recuperar um bucket:

{% highlight ruby %}
filename = request.params["arquivo_para_upload"][:filename]
filepath = request.params["arquivo_para_upload"][:tempfile]

s3 = AWS::S3.new(
  :access_key_id     => your_access_key_id,
  :secret_access_key => your_secret_access_key)

bucket = s3.buckets[your_bucket_name]

object = @bucket.objects["#{Time.now}-#{filename}"] # Do not replace existing files.
object.write(Pathname.new(filepath))
{% endhighlight %}

Pronto! Arquivo na Amazon! \o/

# Sobre a organização do código

Para facilitar a compreensão do código, separei em arquivos com
responsabilidades distintas:

  * _Gemfile_: contem as dependências do projeto
  * _config.ru_: configura o rack e chama o objeto que irá tratar as requisições
  * _app/simplest_ruby_s3.rb_: gerencia o roteamento de requisições:
    * GET  /: apresenta a página com o formulário para subir o arquivo.
    * POST /upload: chama o objeto que irá interagir com a AWS::S3.
    * Qualquer outra requisição: retorna um 404.
  * _app/uploader_s3.rb_: interage com o client AWS::S3 para subir o arquivo.

Sugestões? Opiniões? Deixem nos comentários.
