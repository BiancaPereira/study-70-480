# Certificação Microsoft 70-480: Estudos

## Índice
- [Certificação Microsoft 70-480: Estudos](#certificação-microsoft-70-480-estudos)
  - [Índice](#índice)
  - [Materiais usados](#materiais-usados)
  - [Minhas anotações](#minhas-anotações)
  - [Habilidades medidas](#habilidades-medidas)
    - [1. Implementar e manipular estruturas de documentos e objetos (20-25%)](#1-implementar-e-manipular-estruturas-de-documentos-e-objetos-20-25)
    - [2. Implementar fluxo de programa (25-30%)](#2-implementar-fluxo-de-programa-25-30)
    - [3. Acessar e proteger dados (25-30%)](#3-acessar-e-proteger-dados-25-30)
    - [4. Usar CSS3 em aplicativos (25-30%)](#4-usar-css3-em-aplicativos-25-30)

## Materiais usados
- [Página do exame no site da Microsoft](https://docs.microsoft.com/pt-br/learn/certifications/exams/70-480)
- [Gist do rgharris](https://gist.github.com/rgharris/a97a38ffd94a6fa6f975)
- [Artigo da Rita no iMasters](https://imasters.com.br/carreira-dev/guia-de-estudos-certificacao-microsoft-70-480)
- [Aplicativo com perguntas para treinar](https://tinyurl.com/yy586x3p)
- [Playlist no Youtube do Ray Carneiro](https://ysoutu.be/vmJ896cWXCQ) e seu [repositório](https://github.com/rcarneironet/exam70480)
- [Tutoriais no MDN](https://developer.mozilla.org/pt-BR/) e exemplos no [W3Schools](https://www.w3schools.com/)

## Minhas anotações

> :pencil: **[Lista de tarefas detalhada](todo-detailed-topics.md)**
> 
> **Importante:** Nas minhas anotações tem bastante conteúdo, mas não é tudo que cai na prova e nem está bem explicado. Escrevi como material de referência pessoal.

1. [HTML](study-notes/html-notes.md)
2. [CSS](study-notes/css-notes.md)
3. [Javascript](study-notes/javascript-notes.md)
4. [jQuery](study-notes/jquery-notes.md)

## Habilidades medidas

### 1. Implementar e manipular estruturas de documentos e objetos (20-25%)

- (1) Criar estrutura de documentos usando HTML **(OK)**
  - Usar markup semântico (incluindo markup para mecanismos de busca e leitores de tela, como Section, Article, Nav, Header, Footer e Aside)
  - Criar um layout container em HTML

- (2) Escreva códigos que interagem com UI controls **(OK)**
  - Adicione e modifique elementos HTML através de código
  - Implemente media controls
  - Implemente HTML5 canvas e gráficos SVG

- (3) Aplique estilo em elementos HTML **(OK)**
  - Mude a localização de um elemento
  - Aplique um transform
  - Show/hide de elementos

- (4) Implemente APIs de HTML5 **(OK)**
  - Storage APIs
  - Geolocation API

- (5) Estabeleça o escopo de objetos e variáveis **(OK)**
  - Defina o lifetime das variáveis
  - Remova objetos fora do namespace global
  - Use this para referenciar um objeto que iniciou um evento
  - Escopo de variáveis locais e globais

- (6) Crie e implemente objetos e métodos **(OK)**
  - Implemente objetos nativos
  - Crie objetos e propriedades costumizadas para objetos nativos usando prototypes e funções
  - Herança de um objeto
  - Implemente métodos nativos e crie métodos próprios

### 2. Implementar fluxo de programa (25-30%)

- (7) Implemente fluxos de programa **(OK)**
  - Itere por coleções e itens de array
  - Decisões através de switch
  - If/then
  - Operators
  - Avalie expressões

- (8) Manipule um evento **(OK)**
  - Manipule eventos comuns expostos pelo DOM (onBlur, onFocus, onClick)
  - Declare e manipule bubbled events
  - Manipular um evento usando uma função anônima

- (9) Implemente manipulação de exceptions **(OK)**
  - Configure e responda a códigos de erro
  - Lance uma exception
  - Requisição para null checks
  - Implemente blocos de try-catch-finally

- (10) Implemente programação assíncrona **(OK)**
  - Receba mensagens da API WebSocket do HTML5
  - Use jQuery para fazer uma chamada ajax
  - Conecte um evento
  - Implemente um callback usando funções anônimas
  - Manipule o ponteiro "this"

- (11) Crie um processo de web worker **(OK)**
  - Inicie e pare um web worker
  - Passe dados para um web worker
  - Configure intervalos e timeouts no web worker
  - Registre um event listener para o web worker
  - Limitações de um web worker

### 3. Acessar e proteger dados (25-30%)

- (12) Valide inputs usando HTML5 **(OK)**
  - Escolha controles apropriados baseado nos requerimentos
  - Implemente tipos de input HTML5 e atributos para coletar entradas de usuários

- (13) Valide inputs usando Javascript **(OK)**
  - Use regex para validar um input
  - Valide que você está recebendo o tipo certo de dados usando funções nativas
  - Previna injeção de código

- (14) Consuma dados **(OK)**
  - Consuma dados em JSON e XML
  - Recupere dados usando web services
  - Receba dados usando XMLHTTPRequest

- (15) Serialize, deserialize e transmita dados **(OK)**
  - Manipule dados binários
  - Manipule dados em texto como JSON e XML
  - Implemente o método serialize do jQuery
  - Manipule formulários web usando Form.Submit
  - Parse data
  - Envie dados usando XMLHTTPRequest
  - Sanitize dados usando URI/form encoding

### 4. Usar CSS3 em aplicativos (25-30%)

- (16) Estilize propriedades de texto HTML **(OK)**
  - Aplique estilos para mudar a aparência de textos
  - Aplique estilos para formatar fontes incluindo WOOF, @font-face, tamanho e understudy fonts
  - Aplique estilos para alinhamento de textos
  - Espaçamento e identação
  - Aplique estilos para hifenização de texto
  - Aplique estilos para drop shadow

- (17) Estilize propriedades HTML de box **(OK)**
  - Aplique estilos para alterar aparência de atributos, incluindo tamanho, bordas arredondadas, outline, preenchimento e margem
  - Aplique estilos para alterar efeitos gráficos, incluindo transparecência, opacidade, imagem de background, gradientes, sombras e cortes (clipping)
  - Aplique estilos para estabelecer e mudar a posição de um elemento

- (18) Crie um layout flexível **(OK)**
  - Implemente um layout usando flexbox
  - Implemente um layout multicoluna
  - Implemente um layout usando floating e exclusões
  - Implemente um layout usando grid, regiões, agrupamento e nesting

- (19) Crie uma interface animada e adaptada **(OK)**
  - Anime objetos usando transiões CSS
  - Aplique transformaçoes 3D e 2D
  - Use media queries, incluindo adaptações para output formats, diplays e representações
  - Hide/display controls

- (20) Localize elementos usando seletores CSS e jQuery **(OK)**
  - Escolha o seletor correto para referenciar um elemento
  - Defina um elemento, estilo e seletores de atributos
  - Localize elementos udando pseudo-elementos e pseudo-classes

- (21) Estruture um arquivo CSS usando seletores CSS **(OK)**
  - Referencie elementos corretamente
  - Implemente herança
  - Sobreescreva heranças usando !important
  - Estilize um elemento baseado em pseudo-elementos e pseudo-classes
