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
  * Fiz uma pós, <a title="IS-Expert, NCE - UFRJ" href="http://portal.nce.ufrj.br/index.php?option=com_content&amp;view=category&amp;layout=blog&amp;id=78&amp;Itemid=59">IS-Expert, na UFRJ/NCE</a> em 2004,
    desesti por ter que escrever uma monografia e o trabalho estava me consumindo.
  * Retomei a pós em 2012. Quase desisti. Na época estava estudando Smalltalk,
    por conta própria, e acabei esbarrando em vários assuntos da época, isto é,
    decadas de 60 à 80. Respirei fundo, parei meus estudos, terminei a
    monografia e conclui a pós.
  * Os estudos sobre as décadas de 60 à 80 me inspiraram a refletir sobre
    a formação de um programador. E, tive a idéia de descrever uma faculdade que
    ensinasse a minha visão sobre como um programador deveria ser formado.

Desde então, tenho levantado informações sobre a computação desta época.
Até me deparar com a apresentação de [Bred Victor](http://worrydream.com/#!/cv/bret_victor_resume.pdf),
Mestre em Engenharia Elétrica por Berkeley, fez, em Julho deste ano(2013) uma palestra sobre
<a title="O Futuro da Programação" href="http://vimeo.com/71278954">o futuro da programação</a>, do ponto de vista de um acadêmico em 1973.

- "Mimimi, mas isso é acadêmico, não dá pra usar no dia-dia."

Ok. Então pode me explicar isso? [Introduction to the Wolfram Language](http://www.youtube.com/watch?v=_P9HqHVPeik)

Pretendo começar a escrever sobre como a faculdade deveria ser. E, se tudo der certo,
um dia abro um instituição de ensino que aplique minha visão.

# Guia para o Programa do curso e bibliografia

https://medium.com/javascript-scene/want-to-code-a-university-degree-might-be-a-huge-waste-of-time-81e1817a2ef0#.cwrc7s9l6
http://www.akitaonrails.com/2014/05/02/off-topic-carreira-em-programacao-codificar-nao-e-programar#.U2Pwb61dVy9
http://bsi.uniriotec.br/disciplinas/as.html
http://prog21.dadgum.com/210.html

## Introdução a computação

  * Como chegamos no computador? http://meiobit.com/292520/ibm-e-apple-anunciam-parceria/
    * http://www.blinkenlights.com/pc.shtml
  * O que é um computador? Mostrar um PC por dentro como ele funciona e explicar a arquitetura(Citar a arquitetura de John von Neumann: Processador --- Memória)
  * Apresenta o computador como uma ferramenta multi-uso e multi-propósito. Um simulador de tudo.
  * (The Mother of All Demos)[http://arstechnica.com/the-multiverse/2015/04/from-the-vault-watching-and-re-watching-the-mother-of-all-demos/]
  * Assumir que não sabemos a melhor forma de usá-lo: Demoramos umas décadas até ligarmos uma tela, por exemplo
    * http://blog.enfranchisedmind.com/2009/04/return-of-the-real-programmer/
  * (The Legend of John von Neumann)[http://stepanov.lk.net/mnemo/legende.html?hn]
  * (As calculadoras da NASA)[http://meiobit.com/350003/katherine-johnson-sera-retratada-no-hidden-figures-filme-sobre-calculadoras-que-voce-nao-pode-perder/]
  * (Margaret Hamilton e a Apolo 11)[http://meiobit.com/304884/margaret-hamilton-a-mulher-que-salvou-a-apollo-11/]
  * (Programmers Don't Read Books -- But You Should)[http://blog.codinghorror.com/programmers-dont-read-books-but-you-should/]
  * História do Unix:
    * O que tinhamos antes?
    * O que motivou a criação?
    * Quem fez?
    * Como fez?
	* Mostrar a evolução do Eniac, até o Smalltalk
    * Criação do Unix: 1969 http://www.unix.org/what_is_unix/history_timeline.html
    * Criação do Smalltalk 1972
    * Plan 9: Levando o SO de volta para a área de pesquisa:
      * http://www.plan9.bell-labs.com/wiki/plan9/plan_9_wiki/
      * http://doc.cat-v.org/plan_9/1st_edition/designing_plan_9


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
  * [How can we communicate programs to a computer over a spatial channel?](http://tobyschachman.com/Shadershop/)
	* http://jsmaker.com/jsmaker/
  * [1999/2000 Developer Desktops.](http://www.reddit.com/r/programming/comments/1tg1jp/19992000_developer_desktops/)
    * http://imgur.com/a/Fh0zu
  * [A importância de escolher uma linguagem que defina o curso de programação](http://www.cs.berkeley.edu/~bh/proglang.html)
  * [Structure and Interpretation of Computer Programs](http://xuanji.appspot.com/isicp/)
    * http://www.reddit.com/r/programming/comments/r1wj/demise_of_6001_legendary_computer_science_class
    * http://vedantk.tumblr.com/post/8424437797/sicp-is-under-attack-updated
    * https://news.ycombinator.com/item?id=2843715
  * [The Parable of the Two Programmers](http://www.csd.uwo.ca/staff/magi/personal/humour/Computer_Audience/The%20Parable%20of%20the%20Two%20Programmers.html)
    * Você não é promovido por corrigir os bugs que você não gerou
    * Diminuir a complexidade do problema não é avaliado como um grande feito


## Programação 101 - Elixir

  * [Programming Elixir](http://pragprog.com/book/elixir/programming-elixir)
  * Introduz poucos conceitos desconhecidos
  * Mais parecido com algo que as pessoas já viram: Funções matemáticas
    * [A practical introduction to functional programming](http://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming)
    * [Functional Programming in Javascript](http://jhusain.github.io/learnrx/)
    * [Returning self or void suggests mutability](https://aphyr.com/posts/320-returning-self-or-void-suggests-mutability)
  * [Design of LISP-based processors](http://dspace.mit.edu/bitstream/handle/1721.1/5731/AIM-514.pdf)
  * http://www.buildyourownlisp.com/contents
  * https://gitorious.org/lambdapi
  * https://twitter.com/joeerl/status/577584432183451648
  * [Why don't more programmers use Haskell?](http://www.quora.com/Why-dont-more-programmers-use-Haskell)


## Programação 102 - Smalltalk

  * [OOP to me means only messaging, local retention and protection and hiding of state-process, and extreme late-binding of all things. It can be done in Smalltalk and in LISP.](http://userpage.fu-berlin.de/~ram/pub/pub_jf47ht81Ht/doc_kay_oop_en)
    * messaging
    * local retention
    * protection
    * hiding of state-process
    * extreme late-binding(Late binding, or dynamic binding, is a computer programming mechanism in which the method being called upon an object is looked up by name at runtime)
  * [The Deep History of Your Apps: Steve Jobs, NeXTSTEP, and Early Object-Oriented Programming](http://www.computerhistory.org/atchm/the-deep-history-of-your-apps-steve-jobs-nextstep-and-early-object-oriented-programming/)
  * [Why is Object-Oriented Programming Useful? (With a Role Playing Game Example)](http://inventwithpython.com/blog/2014/12/02/why-is-object-oriented-programming-useful-with-an-role-playing-game-example/)
  * [You Could Invent Object-Oriented Programming](http://robots.thoughtbot.com/you-could-invent-objectoriented-programming)
    * [REPL Scheme](http://repl.it/languages/Scheme/)
  * [A conversation with Alan Kay](http://queue.acm.org/detail.cfm?id=1039523)
  * [The Early History Of Smalltalk](http://propella.sakura.ne.jp/earlyHistoryST/EarlyHistoryST.html)
	* [Squeak: Learn Programming with Robots](http://www.amazon.com/dp/B001G0OAO0)
    * Uma versão menos infantil -[Pharo](http://www.pharo-project.org/)
    * Open-Source VM e Linguagem derivado do Smalltalk-80: [Self](http://blog.selflanguage.org/about)
	* O que temos em 1972:
    * Um ambiente gráfico, base do que se tornou o OSX
    * Testes automatizados
    * Ferramenta de desenvolvimento integrada - IDE
  * [Por que não bomba?](http://c2.com/cgi/wiki?WhyIsSmalltalkDead)
    * [RailsConf 09: Robert Martin, "What Killed Smalltalk Could Kill Ruby"](https://www.youtube.com/watch?v=YX3iRjKj7C0)
    * [Where Smalltalk Went Wrong](http://www.ianbicking.org/where-smalltalk-went-wrong.html)
      * ""
        * http://chimeracoder.github.io/docker-without-docker
  * [On object-oriented programming, Yin Wang](http://yinwang0.wordpress.com/2013/12/24/oop/)
  * [OOD Principles](http://principles-wiki.net/collections:ood_principle_language)
  * [Was Alan Kay wrong? And why does that matter?](http://www.reddit.com/r/programming/comments/1th3sa/was_alan_kay_wrong_and_why_does_that_matter/)
  * No final, essa é a forma certa de programar? Lembrar do inicio da palestra The Future of Programming, in 1973
  * Dá pra programar em Smalltalk em JavaScript
    * http://peter.michaux.ca/articles/smalltalk-mvc-translated-to-javascript
    * http://amber-lang.net/

  * Testes automatizados
    * [Growing Object-Oriented Software, Guided by Tests](http://www.amazon.com/dp/0321503627)
    * [Writing Sensible Tests for Happiness](http://fredwu.me/post/59395419899/writing-sensible-tests-for-happiness)
    * [A Guide for Writing Maintainable Rails Tests](http://littlelines.com/blog/2013/12/17/a-guide-for-writing-maintainable-rails-tests)

## Algoritimo 101

  * [Dança ensina sobre ordenação](https://www.youtube.com/user/AlgoRythmics/videos)
  * [Visualização de Algoritimos](http://www.comp.nus.edu.sg/~stevenha/visualization/index.html)

## Verificação e validação
  * [IBM Black Team](http://www.t3.org/tangledwebs/07/tw0706.html#)

### Validação

  * [Why-Most-Unit-Testing-is-Waste](http://www.rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf)
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

### Avaliação de desempenho

  * http://www.joelonsoftware.com/articles/fog0000000319.html
  * https://medium.com/@argentinomota_59914/leite-com-p%C3%AAra-computing-complexidade-de-algoritmos-parte-1-176acd84de3c#.cq5l46p6k
  * [COMPLEXIDADE CICLOMÁTICA – PORQUE USAR EARLY RETURN](http://wcalderipe.com/complexidade-ciclomatica-early-return/)

## Arquitetura de computadores

  * https://people.freebsd.org/~lstewart/articles/cpumemory.pdf
  * http://www.extremetech.com/extreme/171678-intel-unveils-72-core-x86-knights-landing-cpu-for-exascale-supercomputing
  * http://www.qualcomm.com/media/blog/2014/04/07/introducing-snapdragon-810-and-808-processors-ultimate-connected-computing
  * http://highscalability.com/blog/2014/5/1/paper-can-programming-be-liberated-from-the-von-neumann-styl.html
  * http://www.hpl.hp.com/research/systems-research/themachine/
  * http://en.wikipedia.org/wiki/Transputer
  * http://www.transputer.net/fbooks/tarch/tarch.html
  * [x86 Assembly Guide](http://www.cs.virginia.edu/~evans/cs216/guides/x86.html)

## Sistemas operacionais

### Microkernel
  * [http://blog.darknedgy.net/technology/2016/01/01/0/](http://blog.darknedgy.net/technology/2016/01/01/0/)

### Unix
#### Command-line tools
  * [find, grep, sed, and awk](https://wilsonericn.wordpress.com/2011/08/25/find-grep-sed-and-awk/)

## Linguagem de programação e Compiladores
  * [Debunking the "expensive procedure call" myth](http://repository.readscheme.org/ftp/papers/ai-lab-pubs/AIM-443.pdf)
  * http://scheme2006.cs.uchicago.edu/11-ghuloum.pdf

### Compiladores
  * [Computer Science 164 - UCBerkeley](https://www.youtube.com/watch?v=MjR7tQTIWbc&list=PL3A16CFC42CA6EF4F)
  * [CS1 Compilers - Stanford](https://lagunita.stanford.edu/courses/Engineering/Compilers/Fall2014/info)

### Type Theory
  * [So you want to learn type theory...](http://purelytheoretical.com/sywtltt.html)

### Gerenciamento de memória

#### Garbage collector
  * http://www.lshift.net/blog/2013/09/19/the-great-gc-vs-reference-counting-debate/
  * http://patshaughnessy.net/2013/10/24/visualizing-garbage-collection-in-ruby-and-python
  * http://patshaughnessy.net/2013/10/30/generational-gc-in-python-and-ruby
  * http://php.net/manual/en/features.gc.collecting-cycles.php
  * http://researcher.watson.ibm.com/researcher/files/us-bacon/Bacon01Concurrent.pdf
  * https://www.erlang-solutions.com/blog/erlang-19-0-garbage-collector.html

## Bancos de dados
  * http://www.seas.upenn.edu/~zives/03f/cis550/codd.pdf
  * https://modelviewculture.com/pieces/i-can-text-you-a-pile-of-poo-but-i-cant-write-my-name
  * Bancos de dados relacionais
    * (A Tiny Intro to Database Systems)[http://blog.dancrisan.com/a-tiny-intro-to-database-systems]
    * (SQL)[http://sqlzoo.net/wiki/SQL_Tutorial]


## Organização de código

  * [What Is Software Design?](http://www.developerdotstar.com/mag/articles/reeves_design.html)
  * Sobre a importância de separar as responsabilidades de cada grupo de artefatos do projeto
    * Responda a pergunta: Se a regra X mudar, onde tenho que mexer? E, se mudar a forma de apresentar o dado Y?
    * [Single Responsibility Principle](http://www.objectmentor.com/resources/articles/srp.pdf)
  * Composição sobre Herança: https://twitter.com/theburningmonk/status/575306966551126017
  * [Understanding Model-View-Controller](http://blog.codinghorror.com/understanding-model-view-controller/)
  * [MVC](http://st-www.cs.illinois.edu/users/smarch/st-docs/mvc.html)
  * [A cookbook fo using the Model-View-Controller User Interface paradigm in Smalltalk-80](http://www.ics.uci.edu/~redmiles/ics227-SQ04/papers/KrasnerPope88.pdf)
  * [A Generation Lost in the Bazaar](https://queue.acm.org/detail.cfm?id=2349257&ref=fullrss)
  * [Is it really "Complex"? Or did we just make it "Complicated"?](https://www.youtube.com/watch?v=ubaX1Smg6pY&=)
  * [Sobre complexidade: Linus Torvalds vs Eric S. Raymond](https://lwn.net/2000/0824/a/esr-sharing.php3)
  * [How Software Gets Bloated: From Telephony to Bitcoin](http://hackingdistributed.com/2016/04/05/how-software-gets-bloated/)

## Sistemas distribuídos

  * http://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed
  * http://preshing.com/20120612/an-introduction-to-lock-free-programming/

### Web

 * http://www.mysliderule.com/web-dev
 * [A Web é o BitTorrent, não o Facebook.](http://hapgood.us/2014/08/14/the-web-is-broken-and-we-should-fix-it)

### REST
 * [Choosing HTTP status code](http://racksburg.com/choosing-an-http-status-code/)

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
    * http://blogs.wsj.com/accelerators/2014/10/10/weekend-read-the-imminent-decentralized-computing-revolution/
  * [Over engineered: Pq vc precisa de um problema, antes da solução](http://nsainsbury.svbtle.com/java-developers)
  * [Sobre a importância da automação do processo de deploy](http://dougseven.com/2014/04/17/knightmare-a-devops-cautionary-tale/)
  * [Evolução das perguntas ao cliente](https://twitter.com/BenedictEvans/status/573160185470029824)
    * As tech matures the questions evolve:
      * What does it do?
      * Who will do that?
      * Who will want that?
      * Who will like that?
      * Does it make me smile?

## Organização do Time de desenvolvimento

  * [The Joel Test: 12 Steps to Better Code](http://www.joelonsoftware.com/articles/fog0000000043.html)
  * [Getting Things Done When You're Only a Grunt](http://www.joelonsoftware.com/articles/fog0000000332.html)
  * [How Developers Stop Learning: Rise of the Expert Beginner](http://www.daedtech.com/how-developers-stop-learning-rise-of-the-expert-beginner/)

## Enterprisey bullshit

  * [How Enterprise Devs messed up JavaScript environment](http://codeofrob.com/entries/you-have-ruined-javascript.html)
  * [Docker Container bullshit](http://blog.circleci.com/its-the-future/)
  * [The Flaw at the Heart of Bimodal IT](http://continuousdelivery.com/2016/04/the-flaw-at-the-heart-of-bimodal-it/)

## Segurança de dados

  * http://codahale.com/how-to-safely-store-a-password/
  * [Undeterred by its own complete ignorance about how crypto works, @TheEconomist joins those advocating magical keys](https://twitter.com/segphault/status/556925012465446912?s=09)
    * Criptografia não é como uma fechadura de uma porta.
  * [Writing buffer overflow exploits - a tutorial for beginners](http://www.eecis.udel.edu/~bmiller/cis459/2007s/readings/buff-overflow.html)
  * [The sad state of sysadmin in the age of containers](http://www.vitavonni.de/blog/201503/2015031201-the-sad-state-of-sysadmin-in-the-age-of-containers.html)


## Infraestrutura

  * [Bootstrapping an Infrastructure](http://www.infrastructures.org/papers/bootstrap/bootstrap.html)
  * [60.000 miliseconds analysis](http://techblog.netflix.com/2015/11/linux-performance-analysis-in-60s.html)
