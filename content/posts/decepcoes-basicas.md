+++
title = "decepções básicas"
author = ["santi"]
lastmod = 2021-02-22T00:08:21-03:00
tags = ["matematica", "bases-numericas"]
draft = true
subtitle = "se 77 + 33 fosse 100..."
katex = true
+++

## tristezas e mais tristezas {#tristezas-e-mais-tristezas}

ah! que belo o mundo seria se

\\[ 77 + 33 = 100\\]

mas infelizmente não é o que acontece. vivemos num mundo falho e imperfeito, a vida é arbitrária e sem sentido, não há motivo para sequer procurar estender nossa estadia aqui, tudo é fútil e inóquo e devemos todos cometer suicídio.

ou será que não acontece?

bases numéricas são um assunto extremamente arbitrário: na maior parte do tempo usamos bases decimais, mas inconscientemente utilizamos outras bases em outros contextos, seja para o tempo (já reparou como 0.5 horas são 30 minutos?), seja para contar ovos (de 12 em 12) ou mesmo na linguagem mística dos computadores: binário.

fato é que, para toda base numérica \\(x\\), podemos calcular o valor de seus digitos com a formula geral:

\\[ valor = a\_k x^{k} + a\_{k-1} x^{k-1} + ... + a\_2 x^{2} + a\_1 x^{1} + a\_0 x^{0} \\]

ou, simplificando

\\[ valor = \sum\_{i=0}^{k} a\_i x^{i} \\]

para o caso decepcionante supracitado, podemos dissecá-lo como

\\[ 7 \cdot 10^{1} +  7 \cdot 10^{0} + 3 \cdot 10^{1} + 3 \cdot 10^{0} =  1 \cdot 10^{3} \\]

e, interessantemente re-agrupá-lo como

\\[ 7 (10^{1} + 10^{0}) + 3 (10^{1} + 10^{0}) = 1 (10^{2})\\]

curiosamente, ou não curiosamente, muitos alunos do _ótimo_ sistema de educação brasileiro já se encontraram de frente com a expressão entre parênteses: sim, é a soma de uma progressão geométrica. e para os que não lembram, podemos facilmente achar a fórmula fechada para tal com:

\\[ S\_{pg} = x^{k} + x^{k-1} + x^{k-2} + ... + x^{2} + x^{1} + x^{0} \\]

\\[ x \cdot S\_{pg} = x^{k+1} + x^{k} + x^{k-1} + ... + x^{3} + x^{2} + x^{1} \\]

\\[ x \cdot S\_{pg} - S\_{pg} = x^{k+1} - x^{0} \\]

\\[ S\_{pg} = \frac{x^{k+1} - x^{0}}{x - 1}\\]

E vemos que, não surpreendentemente,

\\[  \frac{10^{2} - 1}{10 - 1} = \frac{99}{9} = (10^1 + 10^0) = 11\\]

> ok, entendi, matemática chata, e dai?

acalme-se jovem padawan, estamos apenas começando.


## subvertendo a realidade {#subvertendo-a-realidade}

> quando a verdade doi, ignore-a e crie a sua própria

provavelmente ninguém nunca disse isso. mas é verdade: quando os fatos não estão a seu favor, apenas os ignore. é simples assim. portanto, definemos aqui a base \\(b\\) tal que

\\[ 77\_b + 33\_b = 100\_b \\]

onde a notação \\(número\_b\\) indica que \\(número\\) é calculado na base \\(b\\). sabemos que, para nossa base ser válida, precisa satisfazer

\\[ 7(b^{1} + b^{0}) + 3(b^{1} + b^{0}) = b^{2} \\]

\\[ (b^{1} + b^{0})(7 + 3) = b^{2} \\]

e, portanto, pela fórmula da soma de pg,

\\[ 10 \left( \frac{b^{2} -1}{b - 1} \right) = b^2 \\]

resolvendo um pouco mais,

\\[ 10b^2 - 10 = b^3 - b^2 \\]

\\[ b^3 + 11b^2 - 10 = 0\\]

essa fórmula nos dá, então, três possíveis valores para \\(b\\). um deles é trivial: \\(b=1\\), visto que \\(1 + 11 - 10\\) realmente _é igual_ a 0. entretanto, as outras duas soluções são muito mais interessantes: \\(b = 5 \pm \sqrt{35}\\)

e, ainda mais entusiasticamente, _apenas um_ desses valores é de fato positivo: \\(5 + \sqrt{35}\\), e portanto sabemos que

\\[ 77\_{5 + \sqrt{35}} + 33\_{5 + \sqrt{35}} = 100\_{5 + \sqrt{35}}\\]

**eureka!**


## generalizando... {#generalizando-dot-dot-dot}

por quê parar com \\(77 + 33 = 100\\)? por quê não \\(777 + 333 = 1000\\)? ou \\(7777 + 3333 = 10000\\)? realmente, não precisamos parar nessas quantidades de dígitos arbitrários, podemos ir **além**. Portanto, seja \\(B(n)\\) a base necessária para que

\\[ 77...7 (n~digitos) + 33...3 (n~digitos) = 10....0(n+1~digitos) \\]

sabemos que a fórmula

\\[ 7 (B(n)^{n} + ... + B(n)^1 +B(n)^0) + 3 (B(n)^{n} + ... +B(n)^1 +B(n)^0) =B(n)^{n+1}\\]

deve ser satisfeita. portanto

\\[ 10 \left( \frac{B(n)^{n+1} - 1}{B(n)- 1} \right) =B(n)^{n+1}\\]

logo, organizando a equação, e usando a fórmula da soma de pg, achamos nossa fórmula geral para \\(B(n)\\):

\\[ B(n)^{n+2} - 11 B(n)^{n+1} + 10 = 0\\]

**eureka!\\(^2\\)**

desse modo, para qualquer quantidade de dígitos \\(n\\), podemos calcular, _dada suficiente quantidade de magia negra_, sua respectiva **base ideal**. por essa fórmula, podemos, por exemplo, achar a resposta para a \\(B(2)\\):

\\[ B(2) = \frac{1}{3} \left(10 + \sqrt[3]{1585 - 15 \sqrt{1401}} + \sqrt[3]{5 (317 + 3 \sqrt{1401})} \right)\\]

para o caso \\(B(3)\\), apesar de o wolfram alpha encontrar _de maneira mística_ a solução exata, não irei incluí-la pois é **enorme**

e não respondo para o caso de \\(B(4)\\) em diante pois nem o wolframalpha foi capaz de empregar _magia negra_ suficiente para encontrar a solução exata, apesar de serem equações relativamente simples.


## adendos finais {#adendos-finais}

alguns podem já ter notado que a base \\(b\\) não funcionará _apenas_ para o caso \\(77\_b + 33\_b = 100\_b\\). de fato, quaisquer dois números que somem para 10 irão funcionar nessa equação, portanto \\(66\_b + 44\_b = 100\_b\\) ou \\(88\_b + 22\_b = 100\_b\\).

além disso, deixei propositalmente escondido um fato bem importante: as equações possuirão graus cada vez maiores e eu não provei que \\(B(n)\\) será sempre um número real (pois pode muito bem acontecer que todas as soluções de \\(B(n)\\) sejam imaginárias, até então). pois bem, apesar de acreditar que tal fato seja verdadeiro, **eu não sei como provar isso**, e portanto deixo aqui a **conjectura de santi**:

\\(\forall n \in \mathbb{N}, n \geq 0\\), \\(\exists! k \in \mathbb{R}, k > 0\\) tal que

\\[k^{n+2} - 11 k^{n+1} + 10 = 0 \\]

onde \\(k\\) é a _única_ solução real positiva para a fórmula geral de \\(B(n)\\). apesar de não saber provar, realmente acredito que essa afirmação seja verdadeira.

e sim, eu também ainda não sei bem como definir _uma base não inteira_, mas isso fica como dever de casa para àqueles que acreditam que matemática deve sempre ser aplicável à vida real.
