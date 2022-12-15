# Problema #

Existem `100` buracos em linha e um coelho, o coelho está dentro de um dos buracos, após cada verificação, o coelho muda para um buraco
à esquerda ou à direita, aleatoriamente

A ideia é achar a solução otima `O(n)` sendo o pior caso

Entretanto isso não significa que verificar 2x os buracos não seja uma solução `O(n)`, visto que em notação:
`O(2n) = O(n)`

## Hipótese ## 
Existe forma garantida de verificar apenas uma vez os buracos e necessariamente achar o coelho

Considere $B=\Set{B_1,B_2...,B_{100}}$ o conjunto de buracos.

$B_c$ tal que $1<=c<=100$, $c$ é onde o coelho está

Vamos dividir o conjunto $B$ em dois subconjuntos:

$Bi = \set{B_1, B_3, B_5..., B_{99}}$, buracos impares

$Bp = \set{B_2, B_4, B_6..., B_{100}}$, buracos pares

$k$ será nossa variável de iteração, representa qual buraco estamos olhando

### O pior caso é descrito por: ###

$B_c$ sendo $c$ par ($B_c \in B_p $)


### Iteração 1:  ###
$k_1$ ) Verificamos $B_k$, não encontramos o coelho
- $B_c \neq B_k$ 

Coelho muda para buraco impar:
- $B_c \in B_i $
- $B_c \notin B_p $

### Iteração 2: ###
$k_2$ ) Verificamos $B_k$, não encontramos o coelho
- $B_c \neq B_k$ 

Coelho muda para buraco par:
- $B_c \notin B_i $
- $B_c \in B_p $

E assim por diante, nunca encontraremos o coelho, pois em nossas verificações em um $B_k$ impar ele estará em $B_c$ par e vice-versa, esta estratégia falha

## Incremento à estratégia anterior ##

Chegamos à ultima iteração $k=100$ e não encontramos o coelho, com isso, sabemos que o coelho está em uma paridade diferente da que começamos verificar (começamos na paridade impar e ele estava na paridade par) 
Portanto, o que podemos fazer é começar novamente as iterações, mas agora na paridade par, checando primeiro a casa $B_2$

Não existe o risco de começarmos a verificar a casa $B_2$ e o coelho estar na casa $B_1$ pois nossa ultima iteração foi $B_100$ que é um $k_100$ que é par, e portanto o coelho está em um buraco par, necessariamente

Com isso, no pior caso teremos feito 200 verificações, mas ainda teremos o melhor algoritmo, considerando que $O(2n) = O(n)$

> Todo este raciocinio foi feito para tentar "provar" que não é possível um algoritmo que faça apenas 100 iterações, para ESTA estratégia descrita, em que verificamos uma casa de cada vez, de maneira sequencial
