# Anotações HTML5

- [Anotações HTML5](#anotações-html5)
  - [Section, Article, Nav, Header, Footer e Aside (1)](#section-article-nav-header-footer-e-aside-1)
  - [Markup mecanismo de busca (1)](#markup-mecanismo-de-busca-1)
  - [Markup leitores de tela (1)](#markup-leitores-de-tela-1)
  - [Markup de media (vídeo, áudio, etc) (2)](#markup-de-media-vídeo-áudio-etc-2)
  - [HTML Canvas (2)](#html-canvas-2)
  - [Gráficos SVG (2)](#gráficos-svg-2)
  - [Validar inputs (required, minLength, etc) (12)](#validar-inputs-required-minlength-etc-12)

## Section, Article, Nav, Header, Footer e Aside (1)

- `<article>`: define áreas na página
- `<section>`: conteúdo distinto de um documento ou área
- `<nav>`: define conjunto de links de navegação
- `<aside>`: áreas de fluxo menores fora do fluxo da página
- `<mark>`: define que um texto precisa ser marcado
- `<progress>`: progresso de uma tarefa
- `<details>`: detalhes
- `<summary>`: cabeçalho para a tag details
- `<dialog>`: caixa de diálogo
- `<meter>`: medida escalar
- `<time>`: define data/tempo

## Markup mecanismo de busca (1)

```html
<head>
  <meta charset="UTF-8">
  <meta name="description" content="Free Web tutorials">
  <meta name="keywords" content="HTML, CSS, JavaScript">
  <meta name="author" content="John Doe">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

## Markup leitores de tela (1)

- HTML semântico é usado por leitores de tela
- Sempre adicionar o atributo `lang` dentro de `<html>`
- Adicionar texto alternativo `alt` nas imagens
- Usar linguagem clara, sem abreviações ou gírias
- Crie bons textos para links
- O atributo `aria-label` é usado quando a tag do texto não seja visível na tela e pode ser usado em qualquer elemento HTML

## Markup de media (vídeo, áudio, etc) (2)

- Audio
- Embed
- Source: define múltiplos recursos de mídia como vídeo e áudio
- Track: define faixas para elementos de mídia como vídeo e áudio
- Video: define um vídeo ou filme
  - O atributo `controls` adiciona controles como play, pause e volume

```html
<video width="320" height="240" autoplay controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  Your browser does not support the video tag.
</video>
```

## HTML Canvas (2)

- É um container usado para desenhar gráficos com Javascript

```html
<canvas id="myCanvas"></canvas>

<script>
var canvas = document.getElementById("myCanvas");
var ctx = canvas.getContext("2d");
ctx.fillStyle = "#FF0000";
// 0 e 0 é onde inicia o quadrado
// depois vem 80 unidades de largura e então 80 de altura
ctx.fillRect(0, 0, 80, 80);
</script>
```

- OBS: Canvas com Javascript é mais performático que o SVG para renderizar gráficos.

## Gráficos SVG (2)

- A tag `<svg>` define um container para gráficos SVG
- Existem vários métodos para desenhar caminhos, caixas, círculos, texto e imagens gráficas
- Desenhando um círculo:

```html
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow">
</svg>
```

## Validar inputs (required, minLength, etc) (12)

- Tipos de input diferentes: color, date, datetime-local, file, hidden, month, image, range, search, reset, time, week
- Atributos de validação:
  - `accept` que tipo de formato de mídia aceita
  - `autofocus`
  - `dirname` local onde o texto será submetido
  - `max` e `min` para valores
  - `maxlength` e `minlenght` para o número máximo de caracteres
  - `size` tamanho do input em quantidade de caracteres
  - `step` de acordo com o código abaixo os valores podem ser: -3, 0, 3, 6, etc

```html
<input type="number" id="points" name="points" step="3">
```
