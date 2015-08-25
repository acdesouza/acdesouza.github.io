---
layout: post
title: "Testando sua rack app com Capybara e Poltergist"
tags:
- beginner
- dev
- ruby
- rake
- rack
- minitest
- capybara
- poltergeist
- phantomJS
---
Trabalho em uma solução de auto-atendimento que é feita usando tecnologias Web.

Para servir páginas estáticas eu poderia usar o Apache, mas como tem um bocado de código
JavaScript e SASS ajuda um bocado, resolvemos fazer uma rack app.

Para os testes automátizados avaliamos as ferramentas JavaScript tipo Jasmine e QUnit, mas
não conseguimos usar.

É aí que entra o Capybara.

O projeto mostrando o passo-a-passo para criar uma [rack app testada com minitest e o Capybara](https://github.com/acdesouza/rack_tested_by_capybara), está no GitHub.
Os commits detalham bem o processo.
