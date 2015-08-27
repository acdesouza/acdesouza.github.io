---
layout: post
title: "Testando sua rack app com Capybara e Poltergeist"
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
Testes de interface para sua aplicação [Rack](https://github.com/rack/rack) usando o [Capybara](https://github.com/jnicklas/capybara)
rodando através de uma rake task. Sem necessidade de suporte a interface gráfica, graças ao [Poltergeist](https://github.com/teampoltergeist/poltergeist).
Olha! Tá rodando no [Travis-CI](https://travis-ci.org/acdesouza/rack_tested_by_capybara)! \o/

Trabalho em uma solução de auto-atendimento que é feita usando tecnologias Web.
O terminal é uma Single Page Application feita com HTML, JavaScript e compass/SASS e que funciona offline
por conta do HTML5 AppCache e o [IndexedDB]({% post_url 2014-08-02-indexeddb-banco-de-dados-js-client-side %}).

Nós poderíamos ter usando apenas um servidor web, como Apache ou Nginx, para servir páginas estáticas.
Optamos por uma solução com server-side script para poder separar a página em partials,
usar require e juntar todos os arquivos do JavaScript e compilar o SASS.

Para os testes automatizados avaliamos as ferramentas JavaScript tipo Jasmine e QUnit, mas
não conseguimos usar. E, é aí que entra o Capybara.

Por conta da falta de documentação, vejo que seria muito mais fácil fazer um rails new, mas
acreditamos que podemos economizar recursos do servidor.

Extraí do projeto o que seria útil para alguém com as mesmas intensões que nós.

O projeto mostrando o passo-a-passo para criar uma [rack app testada com minitest e o Capybara](https://github.com/acdesouza/rack_tested_by_capybara), está no GitHub.

Como é uma aplicação de estudo, cada commit é um passo que executei. Por isso tenho commits
com o teste quebrando, para em seguida, um commit que faz o teste passar.

Dúvidas, sugestões ou solicitações de funcionalidades que você queira ver nesse
projeto, deixe um comentário.
