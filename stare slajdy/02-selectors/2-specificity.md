# `!important` problem

notes: zdarza się, że musimy nadpisać jakieś regułki. Pierwszą metodą,
która przychodzi nam do głowy, jest użycie !important. A może da się inaczej?


W CSS istnieje algorytm obliczający, która regułka jest ważniejsza.
Reguła jest najważniejsza, jeśli jej selektor ma najwyższą
**specyficzność**<!-- .element: style="color:red"-->.
Algorytm dla każdego selektora oblicza jego wagę w postaci wartości
złożonej z trzech części, gdzie każda odpowiada innej kategorii wagi.


### Kategorie

 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   ID: na tę wagę wpływają wyłącznie selektory identyfikatorów.
   Dla każdego selektora `#` dodawana jest wartość `1-0-0` do wagi.

 * <!-- .element: class="fragment fade-in-then-semi-out" -->
   CLASS: w tej kategorii brane pod uwagę są klasy, ale też selektory
   atrybutów i pseudoklasy. Dla każdego takiego selektora w całym wyrażeniu
   dodawane jest `0-1-0`<!-- .element: style="white-space:nowrap" --> do wagi całości.

 * <!-- .element: class="fragment fade-in" -->
   TYPE: wszystkie selektory elementów i pseudoelementów. Dla każdego takiego
   selektora do wagi całości dodawana jest wartość `0-0-1`.


### Przykład

```css [1|2|3|1-5]
[type="password"],
input:focus,
:root #myApp input:required {
  color: blue;
}
```

pierwszy selektor: specyficzność `0-1-0`
<!-- .element: class="fragment fade-in-then-semi-out" -->

drugi selektor: specyficzność `0-1-1`
<!-- .element: class="fragment fade-in-then-semi-out" -->

trzeci selektor: specyficzność `1-2-1`
<!-- .element: class="fragment fade-in" -->


### Ćwiczenia!

 * <!-- .element: class="fragment fade-in" -->
   napisz selektor o specyficzności `1-0-0`
 * <!-- .element: class="fragment fade-in" -->
   napisz selektor o specyficzności `0-1-0`
 * <!-- .element: class="fragment fade-in" -->
   napisz selektor o specyficzności `0-0-1`
 * <!-- .element: class="fragment fade-in" -->
   oblicz specyficzność selektora:
  ```css
  #main div.login form[name] input:focus {
    outline: none;
  }
  ```


### Odpowiedzi ;)

```css
#cokolwiek {}
```
<!-- .element: class="fragment fade-in" -->

```css
.cokolwiek {}
:hover {}
[type="checkbox"] {}
```
<!-- .element: class="fragment fade-in" -->

```css
h1 {}
::after {}
```
<!-- .element: class="fragment fade-in" -->

```text
1-3-3
```
<!-- .element: class="fragment fade-in" -->
