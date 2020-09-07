# Anotações de CSS

##  Transform (3)

- Permite transformações em elementos 2D e 3D

```css
.transform {
  transform: rotate(90deg);
  transform: translate(50px, 0); /* 50px eixo x e 0px eixo y */
  transform: skewY(20deg); /* entorta em trapézio no eixo Y */
  transform: scaleY(1.5); /* cresce 1.5 vezes no eixo Y */
  transform: rotateZ(-20deg); /* o eixo Z é usado em objetos 3D */
}
```

##  Posicionamento (3)
- Static: renderiza em ordem
- Absolute: relativo ao primeiro elemento ancestral (pai) posicionado e não estático
- Fixed: relativo a janela do navegador
- Relativo: relativo a sua posição normal
- Sticky: posicionado de acordo com o scroll da tela

##  Mostrar/esconder elementos (3)
- `display: none`: esconde o elemento sem deletar e recriar o elemento no DOM
- `visibility: hidden`: esconde o elemento sem remover o espaço do elemento da tela

##  Fontes incluindo WOOF, @font-face, understudy fonts (16)
- WOOF é um formato que funciona na maioria dos navegadores, TTF/OFT (true type) também, mas você pode confiar só na WOOF mesmo
- EOT só funciona no IE6
- WOOF2 é uma fonte que funciona em navegadores mais novos
- `font-stretch: normal | condensed | ultra-condensed | extra-condensed | semi-condensed | expanded | semi-expanded | extra-expanded | ultra-expanded`
- `font-style: normal | italic | oblique`
- `font-weight normal | bold | 100...900`
- `unicode-range`: range de caracteres unicode suportados

```css
@font-face {
  font-family: myFirstFont;
  src: url(sansation_light.woff);
}
```

##  Identação (16)
- Identa a primeira linha de um texto

```css
div.a {
  text-indent: 50px;
}
```

##  Hifenização de texto (16)
- `hyphens: none | manual (default) | auto | initial | inherit`

##  Background (17)
- `background-color`
- `background-image`
- `background-repeat: no-repeat | repeat-x | repeat-y`
- `background-attachment: fixed | scroll`
- `background-position: right top`
- `background-size`
- `background-clip: padding-box | border-box (default) | content-box`: define como o background vai extender dentro de um elemento

##  Cortes (clipping) (17)
- `clip: auto | shape`
- Não funciona se `overflow: visible`

```css
img {
  position: absolute;
  clip: rect(0px,60px,200px,0px);
}
```

- `object-fit: fill (default) | contain (não é clipped) | cover (clipped)`: corta imagens de acordo com a preferência, elas podem ser esticadas, escaladas, etc

```css
img.a {
  width: 200px;
  height: 400px;
  object-fit: cover;
}
```

##  Layout com flexbox (18)

- Layout de linhas

##  Layout com grid, incluindo regiões, agrupamento e nesting (18)

- Layout de colunas e linhas

```css
.grid-container {
  display: grid;
  grid-column-gap: 50px;
}

.item1 {
  grid-column-start: 1;
  grid-column-end: 3;
}

/* regions */
.item1 {
  grid-area: 2 / 1 / span 2 / span 3; /* item 1 inicia na row 2, col 1, span 2 row e 3 col */
}


```

##  Transições (19)

```css
.classToAnimate {
  /* <name> <duration> <delay> <# of times> <fill mode> */
  animation: Your-Animation 5s 1s infinite backwards;
}
@keyframes Your-Animation {
  0% { opacity: 0.1; } /* can use 'from' instead of '0%' */
  50% { opacity: 0.2; }
  100% { opacity: 0.8; } /* can use 'to' instead of '100%' */
}
```

##  Seletores (20)

```
button //element
#someId
.someClass
* //universal selector, avoid
table td //descendent
div > p //child
div + h1 //subsequent adjacent sibling
div ~ h1 //subsequent sibling
a[href] //attribute
a[href='http://localhost'] //equals
a[href*='localhost'] //contains
a[href^='https'] //starts with
a[href$='.png'] //ends with
a[data-bind~='css'] //contains - space separated
```

##  Pseudo-elementos e pseudo-classes (20)

**Pseudo-classes:**

```
:link
:visited
:active
:hover
:focus
:checked
:lang(language) 
:not(selector)
:first-child
:last-child
:nth-child(an+b) 
:nth-last-child(an+b) // começa pelo a e vai adicionado de b em b (n é a iteração do elemento)
:only-child
:only-of-type
:first-of-type
:last-of-type
:target //ID at end of URL - e.g. 'http://a.com/index.html#test'

//examples
p:lang(en) {}
div p:nth-child(3n+2) {}
```

**Pseudo-elementos:**

```
::first-line
::first-letter
::before //can set content
::after //can set content

//examples
#myParagraph::after {
	color: #FFF;
	content: 'test content';
}
#myParagraph::first-letter {
	font-weight: bold;
}
```

##  Herança (21)

**Precedência:**

1. browser - lowest precedence
2. user
3. author
4. author !important
5. user !important - highest precedence

**Especificidade:**

A é o mais significante, procedido pelo b e depois c
- a = id
- b = class, attribute, and pseudo class
- c = element

##  Box shadow (16)

```css
.box {
  box-shadow: 5px 10px #888888 /* 5px é horizontal e 10px é vertical */
}
```
