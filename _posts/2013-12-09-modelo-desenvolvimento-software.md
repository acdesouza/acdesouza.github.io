---
layout: post
title: Como eu trabalho nos meus projetos
tags:
- beginners
- skilled
- expert
- developer
- designer
- user
- agile
- software development
---

Venho trabalhando, desde Maio de 2013, por conta própria. Isto quer dizer que não tenho mais como
culpar o gerente pelas decisões que erradas nos projetos.

Só não sou o único responsável, porque trabalho em equipes de 3 pessoas: 1 Designer/Client-side + 2 Developers.

O trabalho é dividido da seguinte forma:

  * Interagir com o cliente para levantar as necessidades dele no projeto: Designer e os dois Devs
  * Auxiliar o cliente a concretizar, em fluxos de telas, a idéia dele: Designer e os dois Devs
  * Layout das telas: Designer
  * Implementar os layouts criados pelo Designer: Designer e os dois Devs
  * Implementação, no nosso caso em Ruby+Rails: os dois Devs

Como fica claro, nesta divisão de trabalho, todo mundo mete a mão em tudo.
Sendo que as especialidades de cada um define quais são suas responsabilidades. Responsabilidade no sentido
de que é o que se espera que ele faça, não que ele não possa ajudar no que não é especialista.


# Vendendo projetos de escopo aberto, mas preço e tempo definido

A venda de um projeto de software deveria ser focada em quanto tempo o Cliente está interessado
em investir para a próxima, ou primeira, versão do software.

Uma vez definido esse tempo de investimento, o custo é o valor da alocação da equipe de
desenvolvimento.

Portanto duas premissas devem ser estabelecidas:

  * Velocidade do Time de Desenvolvimento
  * TimeBox de execução do projeto.

Isto é: Quanto de esforço a equipe consegue realizar em um tempo determinado.
Por exemplo: 80 pontos em 1 semana.

O método desejado de descobrir a Velocidade do Time é rodando algumas iterações.
Lembrando que a Velocidade deve se tornar constante com o amadurecimento do Time.

# Os 10 passos para o sucesso dos projetos de software ;)

**É óbvio que isso não é uma bala de prata**. E, mesmo que fosse, não serveria para nada, dado que
Projetos de Software não são Lobisomens.

No cenário que tenho trabalhado, os desenvolvedores tem contato direto com o cliente que,
em geral, estão criando um projeto novo.
Nosso ambiente defende que devemos ter uma equipe técnica muito experiente,
como responsáveis pelo projeto.

Tenho acompanhado a aplicação deste processo na criação de aplicações web, com sucesso.

As premissas desse modelo de trabalho:

  * Tempo fixo de 1 semana, isto é, 5 dias.
  * Custo fixo. Time de Desenvolvedores composta por 2 Desenvolvedores, no meu caso Ruby, e um Designer/Client-side
  * Cliente disponível para um dia de reunião, no primeiro dia do projeto, e 3 horas no último dia.
  * O Time tem uma velocidade. E, essa velocidade determina o quanto de
    esforço o Time pode se comprometer, no tempo

## Dia 1

### Objetivo

Concretizar o projeto, no sentido de traduzir do plano das idéias
para a realidade.

Esse processo é feito a partir da definição de Hipóteses de Negócio que
guiarão a confecção de um método, no formato de um software, para validação dessas hipóteses.

Ao final do dia, é esperado que tenhamos as perguntas a serem respondidas, Hipóteses de Negócio,
e um desenho com todas as funcionalidades, do software, que serão implementadas, que
representa o método usado na validação.

### Tarefas do dia

  1. Devs são expostos a idéia do projeto pelo Cliente
  1. Devs auxiliam o Cliente a definir o projeto como hipóteses, testáveis, de negócio.
     Sugestão do Chef: Descrever as hipóteses em formato de perguntas.
  1. Todos devem desenhar, individualmente, um experimento que exercite as hipóteses. Isto é,
     cada um desenhará, cada uma, das telas que servirão para testar as hipóteses. Com fluxos
     claros para cada papel que terá no Web App.
  1. Todos devem apresentar, individualmente, os fluxos dos papéis descritos na sua própria
     solução. E, apontar como respondem as hipóteses.
  1. Dev-Designer deve unificar todas as soluções, em uma, com decisões fechada pelo(s) Cliente(s)

 -- Almoço --

  1. Devs devem quebrar as telas em tarefas, executaveis por apenas uma pessoa ao mesmo tempo.
  1. Devs estimam as tarefas.
     Sugestão do Chef: Ache a tarefa mais simples e atribua o valor 2. Usando a escala: [1, 2, 4, 8] atribua valores
     as outras tarefas comparando-as com a que você atribuiu 2.
  1. Devs apresentam ao Cliente as funcionalidade e o quanto cada uma vai custar.
  1. Devs auxiliam o Cliente a fazer cortes nas funcionalidades para que o total de pontos caibam no TimeBox,
     previamente acordados.
     Esse corte deve usar como guia as Hipóteses de Negócio. Isto é, remover das funcionalidades, levantadas,
     o que não é obrigatório para conseguir responder as perguntas.
  1. Dev-Designer faz o Desenho Final com as funcionalidades já reduzidas.


## Dia 2-4

### Objetivo

Implementar o software descrito pelo Desenho Final

### Tarefas

  1. [Programming, Motherfucker](http://programming-motherfucker.com/): Executar as tarefas descritas e
     estimadas no Dia 1


## Dia 5 - Último dia

### Objetivo

Entregar o software funcionando em ambiente de produção, finalizando o projeto.

### Tarefas

  1. [Programming, Motherfucker](http://programming-motherfucker.com/) Até terminar a pontuação acordada.
  1. Review com o cliente, mostrando para ele as funcionalidades implementadas no servidor de produção.
  1. Cliente faz as considerações sobre o que precisa mudar
  1. Devs estimam as tarefas e apresentam ao cliente o que pode ser feito até o final do dia.
  1. Clientes ordenam a tarefa colocando as de maior importância primeiro
  1. [Programming, Motherfucker](http://programming-motherfucker.com/) até o final do dia
  1. Reunião final, com o Cliente, de entrega. Apresentar as tarefas que puderam ser realizadas e as que não foram possíveis.
