<!-- .slide: data-background-image="gifs/float.jpg" data-background-opacity="0.6" -->
## Float


<!-- .slide: data-background-color="#fff" -->
Pierwotnym przeznaczeniem mechanizmu floatowania było pozycjonowanie obrazków w tekście:

![Obrazki oblane tekstem](gifs/floating-images.png)


<!-- .slide: data-background-color="#fff" -->
...później ktoś wpadł na pomysł, że można tym ustawiać bloki obok siebie

![Layout dwukolumnowy przy użyciu floatów](gifs/website-layout-using-float.jpg)


<!-- .slide: data-background-color="#fff" -->
...ale szybko okazało się, że zdarzają się takie kwiatki:

![Layout dwukolumnowy przy użyciu floatów](gifs/overfloat.png)


ktoś wymyślił więc `clearfix`a

```html
<div class="float-parent">
  <div style="float: left">
    coś, co jest duże i potencjalnie może wystawać
  </div>
</div>
<div class="clearfix"></div>
```

```css
.clearfix::before {
    display: block;
    clear: both;
    content: '';
}
```


Dopiero jakoś około roku 2017 pojawiło się systemowe rozwiązanie tego problemu:

```html
<div class="float-parent">
  <div style="float: left">
    coś, co jest duże i potencjalnie może wystawać
  </div>
</div>
```

```css
.float-parent { display: flow-root; }
```

notes: ta własność tak naprawdę ustawia tylko block formatting context (BFC).
Jest to coś, co można zrobić na kilka innych sposobów, np. position:absolute
również ustanawia nowy BFC -- ale dawanie position:absolute tylko po to, żeby
floaty nie wystawały, jest jednak overkillem


...ale wtedy mieliśmy już flexboxa!
