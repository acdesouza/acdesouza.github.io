---
layout: post
title: Como manter a sanidade da suite de testes
tags:
- beginners
- developer
- test
- ruby
- rails
---
O Rails oference tudo o que é necessário, na maior parte dos casos,
para um suite de testes funcional. Mas, nego insiste em usar ferramentas
por moda.

Histórico de testes de software: http://www.testingreferences.com/testinghistory.php

A base sobre como testar softwares pode ser encontrada no [http://www.computer.org/portal/web/swebok/html/contentsch5#ch5](capítulo 5 do Software Engineering Body of Knowledge (SWEBOK))

A mairo parte das ferramentas de teste são todas baseadas em http://www.xprogramming.com/testfram.htm

http://littlelines.com/blog/2013/12/17/a-guide-for-writing-maintainable-rails-tests/?utm_source=rubyweekly

http://blog.codeclimate.com/blog/2013/10/09/rails-testing-pyramid/
 * "[...]instead of just shipping with the 40-50 acceptance tests you used
    while building out the stories, you should replace those with maybe 3-5 user
    journeys covering the major flows through the registration system[...]"

- Ah! Mas, Capybara é imprescindível
- Sim... Claro... Já leu isso? http://guides.rubyonrails.org/testing.html#integration-testing
- Ou, isso: http://api.rubyonrails.org/classes/ActionDispatch/IntegrationTest.html
- Não!
- :/

 * http://david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html

# #Protip`s de quem é mais famoso do que eu:

http://stackoverflow.com/questions/153234/how-deep-are-your-unit-tests/153565#153565
http://37signals.com/svn/posts/3159-testing-like-the-tsa
https://semaphoreapp.com/blog/2014/01/14/rails-testing-antipatterns-fixtures-and-factories.html
http://6brand.com/time-your-rails-tests.html
http://stackoverflow.com/questions/3663075/speeding-up-rspec-tests-in-a-large-rails-application
http://www.rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf
http://pragdave.me/blog/2008/03/10/the-language-in-domainspecific-language-doesnt-mean-english-or-french-or-japanese-or-/
http://www.akitaonrails.com/2011/04/17/a-controversia-test-unit-vs-rspec-cucumber#.U1pv3K1dVy-
http://www.xprogramming.com/testfram.htm

# Discussão sobre o assunto

https://twitter.com/KentBeck/status/461175937892356096
https://twitter.com/dhh/status/461491174751342592
https://twitter.com/unclebobmartin/status/461473097238204416
https://twitter.com/martinfowler/status/461517619066335232
https://twitter.com/dhh/status/461491858066403329

http://andrzejonsoftware.blogspot.com.br/2014/04/be-careful-with-rails-way.html
http://www.rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf
http://david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html
http://david.heinemeierhansson.com/2014/test-induced-design-damage.html
http://blog.8thlight.com/uncle-bob/2014/03/28/The-Corruption-of-Agile.html
https://www.facebook.com/notes/kent-beck/rip-tdd/750840194948847
http://david.heinemeierhansson.com/2014/slow-database-test-fallacy.html
https://www.destroyallsoftware.com/blog/2014/tdd-straw-men-and-rhetoric
http://blog.8thlight.com/uncle-bob/2014/05/02/ProfessionalismAndTDD.html
http://rubylove.io/2014/04/25/why-i-can-tdd-and-why-dhh-cant/
