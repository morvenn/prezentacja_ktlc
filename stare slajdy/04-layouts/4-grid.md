<!-- .slide: data-background-image="gifs/the-grid.jpg" data-background-opacity="0.4" -->
## Grid

notes: ten obrazek pochodzi z filmu "Tron" z 1984 roku ;)


### Podstawowe pojęcia

 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   DWUWYMIAROWY model layoutu
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   automatyczne rozmieszczanie elementów
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   automatyczne _resajzowanie_ i _repozycjonowanie_ elementów przy zmianie rozmiaru grida
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   możliwość łatwego manipulowania elementami grida


### Koncepcje

 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   Wizualne planowanie layoutu przekłada się niemal bezpośrednio na CSS
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   Grid można zdefiniować wprost lub można częściowo pozostawić do zrobienia przeglądarce („explicit” vs. „implicit”)
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   Elementy grida można układać w dowolny sposób w siatce
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   Można podzielić stronę w logiczny sposób na sekcje (nagłówek, menu, treść, stopka)
 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   Sekcje można umieszczać w innych miejscach w siatce w zależności od np. szerokości ekranu


<div style="display:flex;flex-flow:row nowrap">

```css
.header { grid-area: head; }
.footer { grid-area: foot; }
.content { grid-area: main; }
.sidebar { grid-area: side; }
.wrapper {
  display: grid;
  grid-template-columns: repeat(9, 1fr);
  grid-auto-rows: minmax(100px, auto);
  grid-template-areas: 
    "head head head head head head head head head"
    "side side side main main main main main main"
    "side side side foot foot foot foot foot foot";
}
```

![Przykładowy layout zrealizowany przy pomocy grida](gifs/example-grid.png)
<!-- .element: style="margin:0;flex: 0 0 300px" -->

</div>


Dobra praktyka: „Mobile first”: najpierw planujemy layout dla najwęższych ekranów.
Zwykle taki layout nadaje się też dla przeglądarek nie obsługujących grida.


![Trzy różne layouty w zależności od szerokości ekranu](gifs/responsive-layouts.png)


### Zadanie!

 * zrealizuj responsywny layout według wytycznych z obrazka z poprzedniego slajdu
 * dla uproszczenia pobierz sobie wstępnie przygotowane pliki stąd:

**[git.io/vhUbG](https://git.io/vhUbG)**
