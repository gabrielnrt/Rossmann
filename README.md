# Rossmann


## Introdução

  Este problema pode ser encontrado no [Kaggle](https://www.kaggle.com/competitions/rossmann-store-sales/overview).

  A Rossman é uma drogaria com mais de 3 mil lojas presentes em 7 países da Europa. Nossa tarefa é elaborar um modelo que preveja as vendas diárias nas próximas 6 semanas.

  Boa parte do nome das colunas é auto-explicativa, mas as que não são estão abaixo (tirado do site):

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
