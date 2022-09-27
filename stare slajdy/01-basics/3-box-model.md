# Model pudełkowy
![Hanka Mostowiak - pamiętamy](gifs/hanka-box.png)


## Rodzaje elementów

1. liniowe
2. blokowe

notes: mamy coś takiego jak flow layout (a.k.a. normal flow).
w zasadzie rozmawiamy o display:inline/display:block
omówić różnice między inline a block
element można wyjąć z flow i wtedy jest on niezależny


## Liniowe

* zwykle jest to tekst lub elementy, których pozycjonowaniem zarządza przeglądarka
* honoruje marginesy i paddingi tylko w poziomie (lewa/prawa)


## Blokowe

* blok zajmuje całą dostępną szerokość strony
* można dla niego ustawić wszystkie paddingi, marginesy oraz obramowanie
* własności `width` i `height` odnoszą się do rozmiaru najbardziej wewnętrznego pudełka

![przykład modelu pudełkowego](gifs/box-model.png)

notes: można oczywiście przełączyć obliczanie szerokości i wysokości elementu tak,
żeby te wielkości określały rozmiary widocznego pudełka, czyli razem
z paddingami i obramowaniem


## `display: ???`

Własnością `display` można ustawić elementowi, czy ma być blokowy czy liniowy.
Własność ta ma jednak więcej wartości do wyboru niż tylko `inline` i `block`,
ale każda z nich jest albo blokowa, albo liniowa, choć służą do nieco innych rzeczy.

notes: możliwe wartości display: block, inline, inline-block, table*, list-item, flex, inline-flex, grid, inline-grid, flow-root, none, contents, revert, revert-layer
