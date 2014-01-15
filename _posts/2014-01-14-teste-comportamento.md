---
layout: post
title: Verifique o que estou fazendo, não como!
tags:
- beginners
- developer
- test
---
A Engenharia de Software tem uma disciplina chamada [Verificação e Validação de Software]("http://en.wikipedia.org/wiki/Verification_and_validation_(software)").
Sua intenção é responder as perguntas:
Estamos contruindo o produto corretamente?(Verificação) e
Estamos contruindo o produto correto?(Validação).
Textos como: [Growing Object-Oriented Software, Guided by Tests](http://www.amazon.com.br/dp/B002TIOYVW),
ou o texto do Scott Ambler, que apresenta várias técnicas de teste, [The Full Life Cycle Object-Oriented Testing (FLOOT) Method](The Full Life Cycle Object-Oriented Testing (FLOOT) Method)
é reforçado que o objetivo dos testes é verificar se o software está
se comportando conforme o esperado.


Influenciado por essa linha de pensamento, eu tenho, um certo,
nojinho de testes que quebram quando o comportamento _não_ foi alterado,
mas a implementação mudou.

# Sobre testes que testam implementação

Recentemente, passei pela seguinte situaçõa:

## Modelo

Temos 3(três) classes: A, B e C.

Classe A é antecessora de B. Isto é, B herda de A suas propriedades.
Classe B tem uma associação com muitos objetos da classe C.

Em Ruby, fica assim:

{% highlight ruby %}
class A; end

class B < A
  has_many :c
end

class C; end
{% endhighlight %}

## O Teste

{% highlight ruby %}
describe B
  it { should have_many :c }
end
{% endhighlight %}

## A mudança

A associação subiu na hierárquia, indo de B para A.

### Antes

{% highlight ruby %}
class A; end

class B < A
  has_many :c
end
{% endhighlight %}

### Depois

{% highlight ruby %}
class A
  has_many :c
end

class B < A; end
{% endhighlight %}

Na minha opinião, o teste não tem motivo para quebrar,
uma vez que não há mudança no comportamento de B.

Evoluindo a análise, esse matcher, do RSpec, parece
não ser feito para esse propósito.

Penso que a utilidade dele, é
testar uma gem, por exemplo, que *crie* uma associação. E, por isso
precise verificar se a associação está presente.

Me pergunto: Por que testar a implementação, ao invés do comportamento?

Qual a opinião de vocês sobre o assunto?
