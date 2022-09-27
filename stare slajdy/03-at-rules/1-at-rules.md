<!-- .slide: data-background-color="#e7e7e7" -->
# At-rules

![Misternie zdobiony symbol @](gifs/at.png)

notes: pierwsze użycie symbolu datuje się na rok 1536.
więcej: https://www.smithsonianmag.com/science-nature/the-accidental-history-of-the-symbol-18054936/


## O małpkach w skrócie

 * <!-- .element: class="fragment fade-in" -->
   `@import` umożliwia łatwe łączenie stylesheetów
 * <!-- .element: class="fragment fade-in" -->
   `@font` zrewolucjonizowało typografię w internecie
 * <!-- .element: class="fragment fade-in" -->
   `@media` wprowadziło responsywność na niespotykaną wcześniej skalę
 * <!-- .element: class="fragment fade-in" -->
   `@supports` cywilizuje wykrywanie przeglądarek


<!-- .slide: data-background-color="#fff" -->
## Czy będą jakieś nowe?

![Sylwetki małp coraz bardziej wyprostowanych](gifs/ape-to-human.png)


## Dygresja: `ngAfterViewInit`

 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   niektóre layouty potrzebują rezerwować miejsce na komponenty
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   komponenty potrafią być dynamiczne i ich rozmiarów nie da się przewidzieć
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   w tej sytuacji trzeba je mierzyć po zrenderowaniu
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   mniej więcej do tego przydaje się `ngAfterViewInit`


a może wcale nie trzeba `ngAfterViewInit`?


## Container queries!

 * <!-- .element: class="fragment fade-in" -->
   działają trochę tak jak _media queries_
 * <!-- .element: class="fragment fade-in" -->
   umożliwiają targetowanie konkretnych własności na jakimś kontenerze
 * <!-- .element: class="fragment fade-in" -->
   dzięki temu JS/TS może zająć się ciekawszymi zadaniami ;-)


...niestety są jeszcze na etapie propozycji :-(


...ale jak już zaczną działać, to będzie można zrobić tak:

```css
main, aside {
  container: my-layout / inline-size;
}

.media-object {
  display: grid;
  grid-template: 'img' auto 'content' auto / 100%;
}

@container my-layout (inline-size > 45em) {
  .media-object {
    grid-template: 'img content' auto / auto 1fr;
  }
}
```

[dokumentacja na MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Container_Queries)<!-- .element: class="fragment fade-in footnote" -->

notes: Dzięki container queries będzie można np. lepiej enkapsulować komponenty,
do poziomu takiego, że responsywność będzie można implementować w komponencie,
zamiast dla całego layoutu.


## Kolejna nowość: `@layer`

 * <!-- .element: class="fragment fade-in" -->
   służy do grupowania deklaracji styli i porządkowania kaskady
 * <!-- .element: class="fragment fade-in" -->
   przy pomocy tej reguły można jasno zdefiniować, które style
   są do nadpisania przez inne style
 * <!-- .element: class="fragment fade-in" -->
   przykład:
   ```css
   @layer bootstrap, base, application;

   @import url(bootstrap.css) layer(bootstrap);

   @layer base {
    body { ... }
   }
   ```

notes: Ta regułka również jest obecnie na etapie propozycji, 
ale widać wyraźnie, że w dużych projektach będzie oddawała ogromne
przysługi.