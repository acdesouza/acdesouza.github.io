---
layout: post
title: Faculdade para Programador
tags:
- beginners
- developer
---
Como deveria ser a faculdade, na minha visão.

No momento que comecei a escrever isso:
  * estou em 2013;
  * me formei em 2002, na [UniverCidade](http://www.univercidade.br);
  * Fiz uma pós, <a title="IS-Expert, NCE - UFRJ" href="http://portal.nce.ufrj.br/index.php?option=com_content&amp;view=category&amp;layout=blog&amp;id=78&amp;Itemid=59">IS-Expert, na UFRJ/NCE</a> em 2004, desesti por ter que escrever uma monografia e o trabalho estava me consumindo.
  * Retomei a pós em 2012. Quase desisti. Na época estava estudando Smalltalk,
    por conta própria, e acabei esbarrando em vários assuntos da época, isto é,
    decadas de 60 à 80. Respirei fundo, parei meus estudos, terminei a
    monografia e conclui a pós.
  * Os estudos sobre as décadas de 60 à 80 me inspiraram a refletir sobre
    a formação de um programador. E, tive a idéia de abrir uma faculdade que
    ensinasse a minha visão sobre como um programador deveria ser formado.

Desde então, tenho levantado informações sobre a computação desta época.
Até me deparar com a apresentação de [Bred Victor](http://worrydream.com/#!/cv/bret_victor_resume.pdf), Mestre em Engenharia Elétrica por Berkeley, fez, em Julho deste ano(2013) uma palestra sobre <a title="O Futuro da Programação" href="http://vimeo.com/71278954">o futuro da programação, do ponto de vista de um acadêmico em 1973</a>
Mimimi, mas isso é acadêmico, não dá pra usar no dia-dia. Ok. Então pode me explicar isso? [Introduction to the Wolfram Language](http://www.youtube.com/watch?v=_P9HqHVPeik)

Pretendo começar a escrever sobre como a faculdade deveria ser. E, se tudo der certo, um dia abro um instituição de ensino que aplique minha visão.

# Guia para o Programa do curso e bibliografia

http://www.akitaonrails.com/2014/05/02/off-topic-carreira-em-programacao-codificar-nao-e-programar#.U2Pwb61dVy9
http://bsi.uniriotec.br/disciplinas/as.html

## Introdução a computação

  * Como chegamos no computador? http://meiobit.com/292520/ibm-e-apple-anunciam-parceria/
  * O que é um computador? Mostrar um PC por dentro como ele funciona e explicar a arquitetura(Citar a arquitetura de von Neumann - Processador --- Memória)
  * Apresenta o computador como uma ferramenta multi-uso e multi-propósito
  * Assumir que não sabemos a melhor forma de usá-lo: Demoramos umas décadas até ligarmos uma tela, por exemplo
    * http://blog.enfranchisedmind.com/2009/04/return-of-the-real-programmer/


## Introdução a programação
	* O que é programação? - Não sabemos.
    Seguir o inicio da apresentação e mostrar o que já foi considerado programar.
    Inicialmente, a idéia é descrever um conjunto de tarefas que o
    programador deseja que o computador execute. Mas, a forma de programar
    evolui para um formato de descrição de metas a serem alcançadas.
    Deixando o passo a passo ser descoberto pela máquina.
    * Apresentar Prolog, como exemplo
  * [Gerald Jay Sussman -- We Really Don't Know How To Compute!](http://www.infoq.com/presentations/We-Really-Dont-Know-How-To-Compute)
  * (Macros no lugar de compiladores)[http://jlongster.com/Stop-Writing-JavaScript-Compilers--Make-Macros-Instead]
	* Mostrar a evolução do Eniac, até o Smalltalk
	* Mostrar Smalltalk. Todo o ambiente, e sempre citar o quando foi feito. E, por quem.
	* http://blog.existentialize.com/you-are-not-a-10x-developer.html
	* Escrever programas parece com escrever: http://www.artima.com/weblogs/viewpost.jsp?thread=255898
	* Escrever programas pode parecer com desenhar um labirinto/geometria/grafo:
    * http://www.reddit.com/r/programming/comments/1oht2s/graphical_programming_can_it_be_better_that/
    * https://blockly-demo.appspot.com/static/apps/index.html
	* Escrever programas pode parecer com fazer perguntas(SQL, Prolog): http://www.reddit.com/r/programming/comments/1qlk4e/is_wolfram_language_gonna_be_a_new_programming/
	* Escrever programas pode parecer com descrever fluxos
    * http://en.wikipedia.org/wiki/Flow-based_programming
    * http://www.infoq.com/news/2013/08/noflow-kickstarter
    * http://noflojs.org/documentation/
	* Veja o Facebook por exemplo, front-end simples e intuitivo, cheio de imagens, ai as pessoas acham que já que é fácil usar, é fácil fazer. A maioria das pessoas acham que construir software é um processo totalmente visual e com comandos, como se fosse um jogo. Vc monta as imagens e aperta botões (comandos) para dizer para as imagens o que elas devem fazer. Zaca, corrija-me se eu estiver errado, mas existem donos de empresa de software que pensam assim.
	* http://jsmaker.com/jsmaker/
  * [1999/2000 Developer Desktops.](http://www.reddit.com/r/programming/comments/1tg1jp/19992000_developer_desktops/)
    * http://imgur.com/a/Fh0zu

## Metodologias para desenvolvimento de sistemas

	* [Paper sobre a The NATO Software Engineering Conferences](http://homepages.cs.ncl.ac.uk/brian.randell/NATO)
	* [Structured Analysis and System Specification](http://www.unt.edu/cdit/3.0/demarco.htm">Tom DeMarco</a>, 1978: http://www.industriallogic.com/blog/tech-safety-in-demarco-classic)
	* [The Father of Waterfall, Winston W Royce, Isn’t](http://www.stephenonsoftware.com/2010/11/winston-w-royce-father-of-waterfall.html, http://ultimatesdlc.com/father-waterfall/)
	* Focar no quão inseguro é:
    * shoot once for perfection
    * write giant specifications
    * define behavior via ambiguous language
    * let software maintenance costs soar
    * produce poorly designed code
    * perform insufficient testing
	* Associar o negócio do desenvolvimento com um restaurante e escrever um livro
    * [100 Curse Free Lessons From Gordon Ramsay On Building Great Software](http://highscalability.com/blog/2013/8/12/100-curse-free-lessons-from-gordon-ramsay-on-building-great.html)
    * [Boring Systems Build Badass Businesses](https://devopsu.com/blog/boring-systems-build-badass-businesses/)
  * http://www.slideshare.net/josenaldomatos/programao-orientada-a-gambiarra-30097904
  * Simplesmente, não fazemos idéia do que estamos fazendo
    * http://pindancing.blogspot.com.au/2009/09/let-agile-fad-flow-by.html
    * http://pragdave.me/blog/2014/03/04/time-to-kill-agile/
    * http://highscalability.com/blog/2014/4/3/leslie-lamport-to-programmers-youre-doing-it-wrong.html

## Programação 000 - Elixir

  * [Programming Elixir](http://pragprog.com/book/elixir/programming-elixir)
  * Mais parecido com algo que as pessoas já viram: Funções matemáticas
  * Introduz poucos conceitos
  * http://www.buildyourownlisp.com/contents

## Programação 001 - Smalltalk

	* [Squeak: Learn Programming with Robots](http://www.amazon.com/dp/B001G0OAO0)
    * Uma versão menos infantil -[Pharo](http://www.pharo-project.org/)
    * Open-Source VM e Linguagem derivado do Smalltalk-80: [Self](http://blog.selflanguage.org/about)
	* O que temos em 1972:
    * Um ambiente gráfico, base do que se tornou o OSX
    * Testes automatizados
    * Ferramenta de desenvolvimento integrada - IDE
  * [Por que não bomba?](http://c2.com/cgi/wiki?WhyIsSmalltalkDead)
  * No final, essa é a forma certa de programar? Lembrar do inicio da palestra The Future of Programming, in 1973
  * [On object-oriented programming, Yin Wang](http://yinwang0.wordpress.com/2013/12/24/oop/)
  * [Was Alan Kay wrong? And why does that matter?](http://www.reddit.com/r/programming/comments/1th3sa/was_alan_kay_wrong_and_why_does_that_matter/)

  * Testes automatizados
    * [Growing Object-Oriented Software, Guided by Tests](http://www.amazon.com/dp/0321503627)
    * [Writing Sensible Tests for Happiness](http://fredwu.me/post/59395419899/writing-sensible-tests-for-happiness)
    * [A Guide for Writing Maintainable Rails Tests](http://littlelines.com/blog/2013/12/17/a-guide-for-writing-maintainable-rails-tests)

## Verificação e validação

### Validação
  * http://www.rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf
  * http://david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html
  * http://david.heinemeierhansson.com/2014/test-induced-design-damage.html
  * https://www.facebook.com/notes/kent-beck/rip-tdd/750840194948847
  * http://david.heinemeierhansson.com/2014/slow-database-test-fallacy.html
  * https://www.destroyallsoftware.com/blog/2014/tdd-straw-men-and-rhetoric

  * https://twitter.com/HashNuke/status/461507198237949952
  * https://twitter.com/KentBeck/status/461175937892356096
  * https://twitter.com/dhh/status/461491174751342592
  * https://twitter.com/unclebobmartin/status/461473097238204416
  * https://twitter.com/martinfowler/status/461517619066335232
  * https://twitter.com/dhh/status/461491858066403329

## Arquitetura de computadores

 * http://www.extremetech.com/extreme/171678-intel-unveils-72-core-x86-knights-landing-cpu-for-exascale-supercomputing?utm_medium=referral&amp;utm_source=t.co</li>
 * http://www.qualcomm.com/media/blog/2014/04/07/introducing-snapdragon-810-and-808-processors-ultimate-connected-computing
 * http://highscalability.com/blog/2014/5/1/paper-can-programming-be-liberated-from-the-von-neumann-styl.html

## Web
 * http://www.mysliderule.com/web-dev
