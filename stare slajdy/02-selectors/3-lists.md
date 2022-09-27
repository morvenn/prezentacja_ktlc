# DRY CSS


## ...czyli jak unikać powtórzeń

 * <!-- .element: class="fragment fade-in" -->zdarza się, że ten sam zestaw reguł trzeba zaaplikować w kilku miejscach
 * <!-- .element: class="fragment fade-in" -->zdarza się, że selektory tych miejsc różnią się tylko jednym elementem
 * <!-- .element: class="fragment fade-in" -->...dochodzi do nieładnych powtórzeń:
   ```css
   .main section p.selected,
   .main aside p.selected,
   .main article p.selected {
    font-weight: bold;
   }
   ```


## To samo, ale w wersji DRY:

```css
.main :is(section, aside, article) p.selected {
 font-weight: bold;
}
```
<!-- .element: class="fragment fade-in" -->

albo<!-- .element: class="fragment fade-in" -->

```css
.main :where(section, aside, article) p.selected {
 font-weight: bold;
}
```
<!-- .element: class="fragment fade-in" -->

\* a czym się różni `:is()` od `:where()`?
<!-- .element: class="fragment fade-in footnote" -->

notes: :is() ma specyficzność najsilniejszego selektora w nawiasach,
podczas gdy :where() ma specyficzność 0, niezależnie od zawartości w nawiasach


a może nieco "wymowniejszy" przykład?


```css
/* lista na 3 poziomie ma używać kwadracików */
ol ol ul,     ol ul ul,     ol menu ul,     ol dir ul,
ol ol menu,   ol ul menu,   ol menu menu,   ol dir menu,
ol ol dir,    ol ul dir,    ol menu dir,    ol dir dir,
ul ol ul,     ul ul ul,     ul menu ul,     ul dir ul,
ul ol menu,   ul ul menu,   ul menu menu,   ul dir menu,
ul ol dir,    ul ul dir,    ul menu dir,    ul dir dir,
menu ol ul,   menu ul ul,   menu menu ul,   menu dir ul,
menu ol menu, menu ul menu, menu menu menu, menu dir menu,
menu ol dir,  menu ul dir,  menu menu dir,  menu dir dir,
dir ol ul,    dir ul ul,    dir menu ul,    dir dir ul,
dir ol menu,  dir ul menu,  dir menu menu,  dir dir menu,
dir ol dir,   dir ul dir,   dir menu dir,   dir dir dir {
  list-style-type: square;
}
```


![Spocony superbohater nie wie, co wybrać](gifs/sweat.png)


```css
/* lista na 3 poziomie ma używać kwadracików */
:is(ol,ul,menu,dir) :is(ol,ul,menu,dir) :is(ul,menu,dir) {
  list-style-type: square;
}
```


<!-- .slide: data-background-image="gifs/link-yes.gif" -->


### Bonusy używania `:is()` / `:where()`

 * <!-- .element: class="fragment fade-in" -->
   upraszczają listę selektorów
 * <!-- .element: class="fragment fade-in" -->
   wprowadzają _forgiving selectors list_
 * <!-- .element: class="fragment fade-in" -->
   upraszczają manipulowanie specyficznością

 notes: forgiving selectors list polega na tym, że jeśli którykolwiek
 z selektorów użytych w liście nie jest obsługiwany przez przeglądarkę,
 cała lista nadal jest poprawnie używana. Jest to zachowanie odwrotne
 do zwykłej listy rozdzielonej przecinkami, gdzie jeden niepoprawny selektor
 powoduje odrzucenie całej listy.
