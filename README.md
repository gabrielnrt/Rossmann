# Rossmann


## Introdução

  Este problema pode ser encontrado no [Kaggle](https://www.kaggle.com/competitions/rossmann-store-sales/overview).

  A Rossmann é uma drogaria com mais de 3 mil lojas presentes em 7 países da Europa. Nossa tarefa é elaborar um modelo que preveja as vendas diárias nas próximas 6 semanas.

  Boa parte do nome das colunas é auto-explicativa, mas as que não são assim estão abaixo (tirado do site):

  * Id - an Id that represents a (Store, Date) duple within the test set

  * Store - a unique Id for each store

  * Sales - the turnover (volume de negócio) for any given day **(this is what you are predicting)**

  * Customers - the number of customers on a given day

  * Open - an indicator for whether the store was open: 0 = closed, 1 = open

  * StateHoliday - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None

  * SchoolHoliday - indicates if the (Store, Date) was affected by the closure of public schools

  * StoreType - differentiates between 4 different store models: a, b, c, d

  * Assortment - describes an assortment level (como os produtos estão organizados): a = basic, b = extra, c = extended

  * CompetitionDistance - distance in meters to the nearest competitor store

  * CompetitionOpenSince(Month/Year) - gives the approximate year and month of the time the nearest competitor was opened

  * Promo - indicates whether a store is running a promo on that day

  * Promo2 - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating

  * Promo2Since(Year/Week) - describes the year and calendar week when the store started participating in Promo2

  * PromoInterval - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store


  A ideia é aplicar o método científico para resolver este problema. Nos próximos tópicos, cada um dos passos do método será abordado com mais detalhes.

  Obs 1: Não coloquei os dados de treino e teste pois o GitHub possui um limite no tamanho dos arquivos para fazer upload.

  Obs 2: Alguns trechos aparecerão comentados, sejam porque o tempo de execução é muito grande, ou porque é mais adequado se executado no Google Colab.

## Descrição dos Dados

  Nesta etapa é realizado um renomeamento das colunas, visão sobre as tipagens de cada uma dela, identificação e preenchimento de células vazias. Por fim, é feita uma descrição estatística tanto de atributos numéricos quanto categóricos. Para os atributos numéricos, são calculados os seguintes parâmetros:

    * Média

    * Mediana

    * Desvio Padrão

    * Valor mínimo

    * Valor máximo

    * Variação

    * Skew

    * Kurtosis

  Já para os atributos categóricos, é feito um boxplot com a finalidade de identificar outliers.

## Extração de características

  Feita a descrição, começamos esta seção formulando hipóteses sobre o que poderia influenciar nas vendas (incluindo essencialmente fatores da loja, produto e o tempo), e logo em seguida extraímos essas características das colunas originais para serem verificadas depois.

## Filtragem dos Dados

  Aqui basicamente filtramos as linhas da tabela que tiveram alguma venda não-nula e que no dia estavam abertas.

## Análise Exploratória

  É aqui que verificamos a veracidade de cada uma das hipóteses formuladas. Para isso, calculamos médias, realizamos gráficos de dispersão, linha, mapa de calor dentre outras ferramentas para checar as hipóteses. Vale ressaltar que alguns resultados são contra intuitivos no que diz respeito à determinados fatores que poderiam diminuir as vendas.

## Preparação dos Dados

  Nesta seção aplicamos algumas operações a fim de otimizar a performance dos algoritmos de aprendizado de máquina. Isso inclui reescalonamento de atributos numéricos e transformações de atributos categóricos em numéricos.

## Seleção das Características

  Primeiramente descartamos as colunas que já foram usadas. Logo em seguida, fazemos o particionamento dos dados que serão usados como treino e os que serão usados como teste. Depois disso, usamos o algoritmo Boruta para selecionar as melhores colunas para uma melhora nos métodos de aprendizagem de máquina.

## Aplicação dos modelos de Machine Learning

  Aqui que de fato aplicamos os modelos de previsão de aprendizado de máquina. Começamos pelo cálculo de média simples, que serve como comparativo para podermos descartar modelos que tenham performance menor que ela. Depois disso, implementamos a Regressão Linear, seguida da Regressão Linear Regularizada. Como as performances desses 2 últimos modelos foi menor que o modelo de média, então executamos modelos de aprendizagem não lineares, que são o Random Forest e o XGBoost. Dado que o XGBoost possui um custo computacional menor que o Random Forest, acabamos por optar por ele, embora tenha uma performance um pouco menor que o Random Forest.

## Ajuste Fino de Hiperparâmetros

  Nesta seção efetuamos o ajuste de parâmetros do modelo XGBoost através de uma busca aleatória tendo em vista que este método é mais rápido que o "grid search", por exemplo.

## Tradução e Interpretação do Erro

  Aqui explicamos com mais detalhes como as métricas usadas em problemas de regressão são convertidas em resultado de negócio, isto é, quanto de receita a mais o modelo de aprendizado de máquina pode gerar para a empresa. Em particular, usamos o erro absoluto médio e o erro percentual absoluto médio.
