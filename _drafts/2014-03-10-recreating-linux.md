---
layout: post
title: Recriando o Linux
tags:
---

A dúvida começa no Tanenbaum–Torvalds debate:
http://en.wikipedia.org/wiki/Tanenbaum%E2%80%93Torvalds_debate
http://oreilly.com/catalog/opensources/book/appa.html
https://www.ibm.com/developerworks/community/blogs/6e6f6d1b-95c3-46df-8a26-b7efd8ee4b57/entry/linux_is_obsolete_a_must_read_debate_between_andrew_s_tanenbaum_and_linus_torvalds34?lang=en

Daí, o [Eric S. Raymond](http://en.wikipedia.org/wiki/Eric_S._Raymond), dá um puchão de orelha no Linus:
http://www.vanadac.com/~dajhorn/novelties/ESR%20-%20Curse%20Of%20The%20Gifted.html
"
 * Linux nasceu com 10k LOCs, monolitico, com o Torvalds chingando deus e o mundo que essa era a coisa mais linda do universo
 * Quando essa licao de moral do Eric Raymond foi dada ele tinha lah seus 3M LOCs (nessa ehpoca eu conheci ele, num sentido quase biblico... naquela ehpoca qqr gurizao com cabelo esquisito e que curtise C metia a mao e se fudia mas achava a duras penas um caminho pra fazer un driverzinho aqui, uma coisinha acola, uma empresinha de milhoes mais a diante)
 * Quando o Rails nascia ele tinha jah 6M LOCs e ninguem com um minimo de sanidade jah se atrevia a achar divertido estudar ele... nessa ehpoca a galera que antes defendia o Linux como base para qqr um aprender bem sobre SO comecou a desistir e surgiram muitos projetos educacionais... a galera que pregava que ele era foda pq era o mais rapido comecou a calar a boca pq rapidinho a performance tava se indo e nessa ehpoca qqr BSD jah tinha mais portes que ele.
 * Depois veio o Git.. e as coisas nao pararam mais, cada release era milhoes de LOCs a mais...
 * Ano passado passou das 15M e agora, finalmente, o finlandes percebeu que o buraco tah um pouco mais embaixo...
 * O futuro eh obvio, amanha serao 20M, daqui uma decada centenas e os bracos nao vao mais dar conta pq programadores nao se reproduzem exponencialmente
 * Pelomenos ele parece mais consciente de que as coisas tao andando um "pouquinho" fora do previsto:
 * http://www.zeit.de/digital/internet/2011-11/linux-thorvalds-interview

Nada disso eh de se adimirar, os caras como o Kay tao falando que vai dar merda a decadas e ninguem quer ouvir... O linux eh um trabalho bracal de caras q se acham na maioria fodas pq conseguem escrever mais... ele mesmo se orgulha de quantos patchs consegue aplicar (eu me envergonharia de que qqr release do Linux precisa de tanta mudanca depois de 20 anos).
Se tu mostrar o trabalho que o Kay tah fazendo recriando isso, eles vao rir pq esses caras sao na maioria filhos de uma geracao que comprou (da SUN) o modelo UNIX de pensar, onde a unica forma de programar eh sentar a mao e escrever milhares e milhares de linhas de C para poder quebrar um arrayzinho de dados e se achar foda...
Se nada mais explicar o que isso significa, basta esse video: http://vimeo.com/71278954"
Crédito: @everton_carpes

E, em algum momento ele viu que o Linux está inchado:
http://www.theregister.co.uk/2009/09/22/linus_torvalds_linux_bloated_huge/
http://www.linux-mag.com/id/7536/

Minha máquina demora 30m para rodar os testes. Os mesmos que meus colegas demoram 8m.
Isso tudo faz com que eu pense sobre o quanto de desperdício, de hardware, existe nos sistemas atuais.

Baseado neste objetivo:
http://www.vpri.org/html/work/ifnct.htm

E, com isso em mente:
http://www.vpri.org/pdf/tr2006003a_objmod.pdf
http://braythwayt.com/2013/12/22/wrong.html
https://computinged.wordpress.com/2010/04/23/alan-kay-on-hoping-that-simple-is-not-too-simple/
http://techland.time.com/2013/04/02/an-interview-with-computing-pioneer-alan-kay/
http://www.vpri.org/pdf/tr2007008_steps.pdf

Ainda, com esse cenário de definição do que é OO, pelo [Alan Kay](http://en.wikipedia.org/wiki/Alan_Kay), em mente:
"OOP to me means only messaging, local retention and protection and
hiding of state-process, and extreme late-binding of all things. It
can be done in Smalltalk and in LISP. There are possibly other
systems in which this is possible, but I'm not aware of them."
Fonte: http://userpage.fu-berlin.de/~ram/pub/pub_jf47ht81Ht/doc_kay_oop_en

Daí o [Joe Armstrong](http://www.codersatwork.com/joe-armstrong.html) comenta:
"Erlang as the only OO language" Cittation needed
http://harmful.cat-v.org/software/OO_programming/why_oo_sucks
http://www.infoq.com/news/2010/07/objects-smalltalk-erlang
http://www.erlang.org/faq/academic.html#id56929

Seria possível partir daqui?
 * http://www.freertos.org/
 * http://www.erlang.org/faq/implementations.html
 * http://elixir-lang.org/


Ou, talvez, dar uma chance ao Minix3:
http://www.cs.vu.nl/~ast/reliable-os/
http://www.minix3.org/
