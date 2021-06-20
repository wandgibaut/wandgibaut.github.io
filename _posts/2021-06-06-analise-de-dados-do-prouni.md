---
layout: post
title: Analise Simples de Dados Públicos do ProUni
subtitle: Pequena exploração sobre a distribuição racial dos beneficiários do prouni
cover-img: /assets/img/prouni-300x147.png
thumbnail-img: /assets/img/prouni-300x147.png
share-img: /assets/img/prouni-300x147.png
tags: [dados publicos, python, dados]
---

Nesse primeiro mini projeto, resolvi explorar um pouco os dados públicos sobre os beneficiários do ProUni, que podem ser encontrados [aqui](https://dados.gov.br/dataset/fundo-de-financiamento-estudantil-fies). O *notebook* com o código pode ser encontrado [aqui](https://github.com/wandgibaut/one_weekeed_projects/blob/master/dados_prouni/data_notebook.ipynb). Nessa análise foquei em observar a distribuição racial ao longo dos anos e no percentual de pessoas negras contempladas em cada estado. Dois gráficos ilustrativos foram gerados e podem ser vistos abaixo.

![serie historica](/assets/img/serie_historica_prouni.png "serie historica prouni")

Nesse primeiro gráfico (perdão pela resolução), pode-se observar a evolução do número total de beneficiários (cinza claro) e de negros (pretos e pardos, em marrom). Pode-se obervar um crescimento no percentual de pessoas negras em relação ao número total de bolsas.


![distribuicao geografica](/assets/img/dist_prouni_2020.png "distribuição do percentual de negros")

Já na segunda imagem está ilutrada o percentual de beneficiários negros em relação ao total para cada estado. Quanto mais escuro, maior o percentual daquele estado. Note que, como era de se esperar, estados com menor prevalência de negros na população apresentam valor menor (não equivalente ao perfil racial do estado, mas isso fica pra outro momento).

Lembrando que a ideia aqui foi ser algo simples que pudesse ser feito em um fim de semana ou menos. Fiquem a vontade pra sugerir novas análises :)
