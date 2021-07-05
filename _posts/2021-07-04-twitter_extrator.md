---
layout: post
title: Extrator de Opinião no Twitter
subtitle: Extraindo, selecionando e analisando tweets sobre temas específicos
thumbnail-img: "https://img.icons8.com/fluent/48/000000/twitter.png"
share-img: "https://img.icons8.com/fluent/48/000000/twitter.png"
tags: [linguagem natural, python, mineracao de dados]
---

Devido à semana corrida (e parte do fds), resolvi aproveitar o Extrator feito no projeto anterior e combiná-lo com um scrapping do Twitter. Além disso, resolvi usar o módulo **TextBlob** para fazer uma análise de sentimento simples (decidir se o tweet tem conteúdo positivo ou negativo).
Para isso usar o [*twint*](https://github.com/twintproject/twint) para buscar um determinado assunto. Em seguida, apliquei o Extrator para selecionar as frases mais significativas, como o usual. Por fim, utilizei o **texblob** para filtrar ainda mais e recuperar apenas os tweets não-neutros.

O *jupyter notebook* pode ser encontrado [aqui](https://github.com/wandgibaut/one_weekeed_projects/blob/master/twitter_opinion/twitter_opinion.ipynb).

Como aplicação-exemplo, utilizei termos relacionados à política nacional na atualidade. Com o *twint* busquei o termo 'Bolsonaro' e recuperei 10k tweets que contém esse termo. Aparentemente, a menos que especificada outra coisa, o *twint* retorna as ocorrências mais recentes.
Ou seja, peguei 10k tweets mais recentes na noite de domingo, 4 de julho de 2021. Em seguida apliquei o Extrator usando como palavras-chave 'impeachment', 'genocida' e 'manifestação', cadeias de 2 palavras e 40 sentenças por palavra-chave.

Escolhi aleatoriamente 4 dessas 120 sentenças para ver em tela:

- '@jairbolsonaro @henriquelorezo Se fosse uma manifestação descente ninguém seria atingido.'
- 'Às ruas foram tomadas por milhares de manifestantes pedindo o impeachment do atual presidente genocida!'
- '@jairbolsonaro Bozo genocida !!!!'
- '@freire_roberto Bolsonaro é um ladrão genocida.. @senadorhumberto Por que vcs nao apuram a corrupção e também a corrupção do governo bolsonaro?'


Como pode-se perceber, escolher aleatoriamente essa sentenças-chave pode ainda trazer algumas dúvidas (bom, nesse caso ai não da margem pra dúvida não, mas vamos fingir que dá).
Nesse ponto, a aplicação do *Textblob* estabelecendo um limiar de **0.35** para sentimentos postivos e **-0.35** (numa escala que vai de **-1** a **1**) para negativos nos ajuda a filtrar ainda mais.

Dentre as sentenças-chave, essas foram todas aquelas que ficaram de fora da margem da neutralidade. Junto com a sentença, também o respectivo valor de polaridade:


- (0.48828125, 'Positive') Eu acho engraçado quando eu vejo uma pessoa com a camisa do che guevara, gritando Bolsonaro genocida.. @taliriapetrone @marinairisvoz @TeresaCristina IMPEACHMENT URGENTE!!!
- (0.39285714285714285, 'Positive') Em partes o Lula não quer que tenha impeachment do bolsonaro né, pq ele sabe que se o Bolsonaro sair e não disputar as eleições, as chances de dar um Ciro ou outro são maiores.
- (0.5, 'Positive') @jairbolsonaro mais de 520 mil mortes de brasileiros inocentes e tu seu VERME GENOCIDA MALDITO debochando teu lugar e da tua família e tua quadrilha vai ser na CADEIA NA SELA MAIS IMUNDA  #LadrãodeVacina.
- (0.5, 'Positive') @jairbolsonaro mais de 520 mil mortes de brasileiros inocentes e tu seu VERME GENOCIDA MALDITO debochando teu lugar e da tua família e tua quadrilha vai ser na CADEIA NA SELA MAIS IMUNDA  #LadrãodeVacina.
- (-0.5, 'Negative') Imaginem que os caras que cansaram de xingar Bolsonaro de genocida dizendo que ele não queria vacinas, agora o chamam de ladrão de vacinas como se fosse maníaco por vacinas!
- (-0.625, 'Negative') Só não tem coragem de admitir pois sabe que ele não passa de um canalha, genocida e corrupto!
- (-0.6, 'Negative') É muita burrice.. @jairbolsonaro Chamam isso de manifestação?
- (-0.5, 'Negative') Só Bolsonaro, de resto ninguém falando dessa manifestação violenta que quebrou e tocou o terror!
- (-0.4, 'Negative') Mas a preocupação dele é com as vidraças quebradas na manifestação.
- (-0.5, 'Negative') @marlonsaul_ @Metropoles @jairbolsonaro É triste que a segurança seja meu maior medo cobrindo uma manifestação.
- (0.7, 'Positive') Até agora aguardando pra ver se o #Fantástico vai passar a matéria da aglomeração e vandalismo ontem na cidade de São Paulo   Olhando a mídia ignorar a "manifestação do bem" da #EsquerdaCriminosa @alertario24hrs #GloboLixo @jairbolsonaro #Fantástico #GloboNews  https://t.co/Gzs1i3FgVm.
- (1.0, 'Positive') sobre a manifestação do dia 3  Ato incrível!!!
- (0.44727272727272727, 'Positive') @OGloboPolitica @jairbolsonaro conflito pontual é o novo "marido errático".. as fotos do protesto de ontem (03 de julho) foi animal a experiência de fotografar a manifestação, vou deixar aqui algumas que eu gostei mais, mas espero que gostem, espero ter feito jus ao ato.
- (0.55, 'Positive') bom demais saber que o fiofó do Bolsonaro tá com as prega lisa essa hora de domingo.
- (-0.5, 'Negative') @marlonsaul_ @Metropoles @jairbolsonaro É triste que a segurança seja meu maior medo cobrindo uma manifestação.

Lembrando que a *Análise de Sentimento* não é perfeita e depende muito de contexto. De qualquer forma pode-se inferir um pouco da situação política do país nesse momento do ano e da pandemia.

Espero que tenham gostado! :)
