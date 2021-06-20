---
layout: post
title: Extrator de Opinião em Empresas - parte 1
subtitle: Uma Implementação do Extrator de Conhecimento Coletivo visto em (Angelo, 2014)
cover-img: /assets/img/extrator.png
thumbnail-img: /assets/img/extrator.png
share-img: /assets/img/extrator.png
tags: [linguagem natural, python, mineracao de dados]
---


Para esse segundo projeto várias coisas vieram em mente, desde postar coisas que ja fiz e ficaram esquecidas por ai até explorar APIs do twitter e coisa assim. No entanto conversando com amigos sobre vagas de emprego, me deparei com a situação de haver uma discrepância entre a autodescrição da empresa em redes sociais e percepção de seus funcionários, muito mais próximos da realidade.
Nesse ponto eu comecei a observar o Glassdoor para além do fator salário, comecei a ver as avaliações que fazem sobre as empresas. Algumas empresas tem MUITAS avaliações, chegando a ser impraticável ler todas elas. A própria plataforma do Glassdoor tem um "sumarizador de opiniões" mas eu achei essa uma boa oportunidade de trablalhar como projeto e, quem sabe, fazer algo legal.


Pensei então em usar um algoritmo apresentado na dissertação de mestrado de Tiago Novaes Angelo, a qual inclusive assisti e muito interessou. E é sobre que é essa primeira parte.
A Figura 1 ilustra a estrutura do Extrator


![serie historica](/assets/img/extrator.png "extrator")
Figura 1: Etapas de processamento da informação no ECC segundo abordagem KDD
(FAYYAD et al., 1996) conforme visto em (ANGELO, 2014).


Em resumo: dada uma ou mais palavras de entrada, um número de passos num grafo direcionado que o algoritmo deve percorrer de adjacências e um número **m** de sentenças, o Extrator encontra  para cada palavra de entrada **m** sentenças que representam a opinião geral das avaliações.
O método é probabilístico e pode retornar resultados diferentes a cada execução mas, em média, retornará as sentenças com maior densidade de probabilidade de ocorrência. A dissertação completa pode ser encontrada [aqui](http://repositorio.unicamp.br/handle/REPOSIP/259820).


Para implementar esse algorítmo, utilizei o módulo **[nltk](https://www.nltk.org/)** que conta ja com diversas classes e métodos para manipulação de linguagem natural (em vários idiomas, incluindo português) e testei com avaliação de restaurantes do [tripadvisor](https://www.tripadvisor.com.br/) encontrados como banco de dados no *[Kaggle](https://www.kaggle.com/jkgatt/restaurant-data-with-100-trip-advisor-reviews-each)*.

A implementação pode ser vista no **notebook** disponível [aqui](https://github.com/wandgibaut/one_weekeed_projects/blob/master/ecc_nlp/nlp.ipynb). Algumas estruturas estão faltantes (não há diretório '/data' no repositório, por exemplo) pois impedi o rastreamento pelo **git** pra evitar dores de cabeça.

Abaixo, um exemplo de saída ao se utilizar a palavra 'food' nas avaliações do primeiro restaurante do banco de dados e a nota média do restaurante:

1:'The beers are great - best in the city in my opinion, food is excellent and the service is great!'
2: 'But per my travel experiences: compared to other brew pubs (in general), the food here is better than what I usually find in a brew pub; the price, relative to food value/quality, is better than I find in brew pubs (in general); and the price for a meal is very fair compared to most San Francisco dining establishments of this caliber.'

4.0

Pode-se notar que o Extrator funciona bem o suficiente pra capturarmos uma opinião representativa, quando comparamos revisão e notas. 

