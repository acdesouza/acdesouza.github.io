---
layout: post
title: "Aprendendo a cozinhar"
tags:
- beginner
- infra
- chef
- berkshelf
- devops
---
Minha história com o [Chef](http://docs.getchef.com/chef_solo.html) começa em 2010, quando eu trabalhei numa grande empresa de mídia
do Brasil com sede na Barra da Tijuca(entendedores, entenderão...).

Nesta época, a área de Infra estava buscando minimizar os erros em produção, que tinham como
causa diferenças do ambiente de desenvolvimento.

A sugestão era que os desenvolvedores trabalhassem em ambiente igual ao de produção,
na própria máquina. Para isso, teriam que simular a sequinte arquitetura:

  * Máquina de banco de dados: MySQL
  * Máquina com o projeto....: Nginx + Unicorn ou Tomcat (sim! Eu trabalho com Ruby e Java, lembra?)
  * Máquina de cache.........: Varnish

Agora, imagina o inferno de instalar isso na máquina de mais de cinqüenta desenvolvedores.

Claro que o ambiente precisava ser virtualizado, para isso usamos o VirtualBox
com o Vagrant que é uma interface linha de comando para o VirtualBox e, de quebra,
oferece integração com ferramentas de provisionamento para a máquina virtual.

A solução é perfeita: os desenvolvedores poderão trabalhar em um ambiente igual ao de produção.
E, o time de Infra utilizaria os mesmas ferramentas para montar o ambiente de produção.

A Infra definiu o uso de uma ferramenta de provisionamento, que é, basicamente, um
programa que instala e configura uma máquina a partir de um conjunto de arquivos descrevendo o que precisa
ser feito, não como.

A empresa, decidiu usar o [Puppet](http://puppetlabs.com/), então ao invés de termos:

arquivo_bash_script.sh

```bash
sudo apt-get install nginx --yes
```

Teremos:

arquivo_descritor_do_ambiente

```ruby
include nginx
```

Ah! Mas, qual a vantagem? Os dois são uma linha...

É, só que pensa que o apt não roda no CentOS, nem no MacOS. Já o Puppet pode
instalar o nginx nos dois.

No final, achei muito positivo porque dava ao desenvolvedor conhecimento sobre onde
a aplicação estava sendo executada. E, quais os desafios que ele gerava para Infra.

Desde que saí de lá, eu venho tentando trabalhar de forma que o ambiente de desenvolvimento
seja igual ao de produção.

Na primeira oportunidade, em outro projeto, decidi usá-lo. E, pensei: O que poderia dar errado?

É, como esperado, foi aí que os problemas começaram...

Começa que não poderia usar o Puppet, porque este depende(ia) de um servidor central.

Por influência do [Akita](http://www.akitaonrails.com/2010/02/20/cooking-solo-with-chef) e do
[Nando Vieira](http://simplesideias.com.br/usando-o-vagrant-como-ambiente-de-desenvolvimento-no-windows)

Bom... O Chef tem uma versão solo, tem toda uma alegoria com culinária, o que eu acho
divertido. Então, seria o que eu estava procurando. Certo?

Então... Eu venho tentando usar o Chef há algum tempo. Mas, sempre caio no mesmo problema:

  * O trabalho que está dando para fazer isso, eu tinha feito um BashScript.

E, isso me perseguiu de forma tão intensa que quando tive que montar um ambiente, para um projeto,
fiz um [BashScript que instala um servidor Rails na Amazon](https://gist.github.com/acdesouza/3555100).
Mas, só depois de perder um dia de trabalho brigando com o Chef :(

Fiz as contas e descobri que já tentei usar o ambiente de desenvolvimento virtualizado, em uns sete
projetos diferentes. Em todos eles eu tentei usar o Chef-solo, em todos eu abandonei quando vi que
o esforço era maior do que escrever um BashScript.

Essa semana no trabalho, tive que levantar um projeto legado em PHP, na minha máquina. O ambiente
consiste em:
  * Nginx
  * PHP-FMP
  * MySQL
  * Capistrano, para fazer a configuração da máquina, restart do Nginx e deploy

Como não quero zoar com meu ambiente, pensei:

  * E, lá vou eu me f**** com o Chef, de novo...

Só que desta vez, foi diferente!

Pra começar, peguei um texto do [Akita, sobre o Chef-solo](http://www.akitaonrails.com/2014/07/28/small-bites-vagrant-ubuntu-14-04-chef-solo),
menos desatualizado.

Um problema que eu ~~tenho~~ tinha com o Chef é que eu ~~tenho~~ tinha que baixar
cada uma das receitas para uma pasta cookbooks no projeto. Ou, escrever minhas
próprias receitas(!).

Cacete, se eu fosse escrever minhas receitas, eu não precisava do Chef,
era só eu escrever em BashScript, não?

Pois é... Eis que surge: [Berkshelf](http://berkshelf.com), agora parte do ChefDK.
Ele será usado para baixar as receitas do [Supermerket](https://supermarket.getchef.com/)
(já falei que eu gosto dessa associação com gastronomia?). Para um programador Ruby,
é próximo de como o [Bundler](http://bundler.io/) funciona.

Pra finalizar, o [Reginaldo Sousa](https://github.com/reginaldosousa/vagrant_chef),
me ajudou a instalar o RVM e um Ruby, para rodar o Capistrano. Observa como ele
colocou o a [receita RVM como um submodulo Git](https://github.com/reginaldosousa/vagrant_chef/tree/master/cookbooks),
no projeto. É isso que eu quero evitar.

Minha proposta é que o desenvolvedor tenha que configurar o ambiente com:

```bash
git clone <url_projeto>
vagrant up
```

Neste caso, ele teria que inicializar os submodulos. Simplesmente chato :/

## Ferramentas

Começamos instalando as ferramentas que serão usadas:

  1. Instala o [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  1. Instale o [Vagrant](http://www.vagrantup.com/downloads)
  1. Instale o [Chef](http://downloads.getchef.com/chef-dk),
    * Eu usei o [Homebrew Cask](http://caskroom.io/): brew cask install chefdk
  1. vagrant plugin install vagrant-berkshelf # Para o Vagrant baixar as receitas.
  1. vagrant plugin install vagrant-omnibus # Para manter o chef-solo atualizado, no box.

* Eu uso o MacOSX, o que significa que a instalação do ChefDK, usando Homebrew é específica para o meu sistema operacional:

## Como configurar uma máquina usando Chef-solo

Começando do zero, esses foram os passos que tive que seguir:

  1. mkdir myapp
  1. cd myapp
  1. vagrant init
  1. vagrant up
  1. Adicione as receitas no Berksfile
  1. Adicione configurações das receitas no Vagrantfile
  1. vagrant reload && vagrant provision

\o/

Isso deve fazer você se questionar: "Por que, diabos, eu preciso fazer o vagrant up antes das receitas?"
Então.... É por conta do problema que faz com que o [Berkshelf não ache o diretório com os cookbooks](https://github.com/berkshelf/vagrant-berkshelf/issues/78).

Depois que consegui fazer funcionar, vi o post no blog da empresa do Bruno Pereira,
a [Rivendel, sobre virtualização do ambiente local](http://blog.rivendel.com.br/2014/08/20/vagrant-as-vantagens-da-virtualizacao-em-ambiente-local/).
Nele o autor, João Vagner, cita a ferramenta [librarian-chef](https://github.com/applicationsonline/librarian-chef).
Só a comparação que ele faz com entre Chef, Puppet e um BashScript já valem a leitura.

Para finalizar, o link para o projeto onde virtualizo o [ambiente usando Vagrant + VirtualBox + Chef-solo](https://github.com/acdesouza/dev-php-chef).
