# Anotações de Javascript

- [Anotações de Javascript](#anotações-de-javascript)
  - [Storage APIs (4)](#storage-apis-4)
  - [Geolocation API (4)](#geolocation-api-4)
  - [API WebSocket (10)](#api-websocket-10)
  - [Lifetime das variáveis (5)](#lifetime-das-variáveis-5)
  - [Remover objetos do namespace global (5)](#remover-objetos-do-namespace-global-5)
  - ["this" para referenciar um objeto que iniciou um evento (5)](#this-para-referenciar-um-objeto-que-iniciou-um-evento-5)
  - [Herança de um objeto (6)](#herança-de-um-objeto-6)
  - [Crie funções com prototype (6)](#crie-funções-com-prototype-6)
  - [Eventos comuns do DOM onBlur, onFocus, onClick (8)](#eventos-comuns-do-dom-onblur-onfocus-onclick-8)
  - [Bubbled events (8)](#bubbled-events-8)
  - [Configure e responda códigos de erro (9)](#configure-e-responda-códigos-de-erro-9)
  - [Thrown exception (9)](#thrown-exception-9)
  - [Requisição de null checks (9)](#requisição-de-null-checks-9)
  - [Try-catch-finally (9)](#try-catch-finally-9)
  - [Conecte eventos (10)](#conecte-eventos-10)
  - [Callback com funções anônimas (10)](#callback-com-funções-anônimas-10)
  - [Ponteiro "this" (10)](#ponteiro-this-10)
  - [Inicie e pare um web worker (11)](#inicie-e-pare-um-web-worker-11)
  - [Passe dados para um web worker (11)](#passe-dados-para-um-web-worker-11)
  - [Configure intervalos e timouts para web workers (11)](#configure-intervalos-e-timouts-para-web-workers-11)
  - [Registre um event listener para um web worker (11)](#registre-um-event-listener-para-um-web-worker-11)
  - [Limitações de um web worker (11)](#limitações-de-um-web-worker-11)
  - [Regex para validar input (13)](#regex-para-validar-input-13)
  - [Validar tipo de dado correto com funções nativas (13)](#validar-tipo-de-dado-correto-com-funções-nativas-13)
  - [Previna injeção de código (13)](#previna-injeção-de-código-13)
  - [Recupere dados usando web services (14)](#recupere-dados-usando-web-services-14)
  - [Receba dados com XMLHTTPRequest (14)](#receba-dados-com-xmlhttprequest-14)
  - [Manipule dados binários (15)](#manipule-dados-binários-15)
  - [Parse data (15)](#parse-data-15)
  - [Envie dados usando XMLHTTPResquest (15)](#envie-dados-usando-xmlhttpresquest-15)
  - [Sanitize dados usando URI/form encoding (15)](#sanitize-dados-usando-uriform-encoding-15)
  - [Escopo de variáveis locais e globais (5)](#escopo-de-variáveis-locais-e-globais-5)
  - [Impemente objetos nativos (6)](#impemente-objetos-nativos-6)
  - [Implemente métodos nativos (6)](#implemente-métodos-nativos-6)
  - [Crie métodos próprios (6)](#crie-métodos-próprios-6)
  - [Itere por coleções e itens de array (7)](#itere-por-coleções-e-itens-de-array-7)
  - [Switch (7)](#switch-7)
  - [If/then (7)](#ifthen-7)
  - [Operators (7)](#operators-7)
  - [Expressões (7)](#expressões-7)
  - [Funções anônimas (8)](#funções-anônimas-8)
  - [Consumir JSON e XML (14)](#consumir-json-e-xml-14)
  - [Interagindo com a UI](#interagindo-com-a-ui)
  - [Diferença entre call(), apply() e bind()](#diferença-entre-call-apply-e-bind)
  - [Outras dicas](#outras-dicas)

## Storage APIs (4)
- Local storage: quando você fecha o browser, as informações continuam lá.
- Session storage: os dados existem enquanto durar a sessão, ou seja, vai deixar de existir depois de fechar a tab do browser.

**Local storage:**

```javascript
// Store
localStorage.setItem("lastname", "Smith");

// Retrieve
document.getElementById("result").innerHTML = localStorage.getItem("lastname");
```

**Session storage:**

```javascript
if (sessionStorage.clickcount) {
  sessionStorage.clickcount = Number(sessionStorage.clickcount) + 1;
} else {
  sessionStorage.clickcount = 1;
}
document.getElementById("result").innerHTML = "You have clicked the button " +
sessionStorage.clickcount + " time(s) in this session.";
```

## Geolocation API (4)
- `getCurrentPosition()` retorna a posição do usuário
- `watchPosition()` retorna a posição e continua acompanhando
- `clearWatch()` para o watchPosition
- `coords.accuracy` retornada do método `getCurrentPosition()`

```javascript
function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
  } else {
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude +
  "<br>Longitude: " + position.coords.longitude;
}
```

## API WebSocket (10)
- Torna possível uma comunicação entre usuário e servidor
- Bastante utilizado com o Node.js e a bliblioteca 
- Interfaces:
  - WebSocket (eventos: close, error, message, open)
  - CloseEvent
  - MessageEvent

## Lifetime das variáveis (5)
- A vida de uma variável em JS inicia quando é declarada
- Variáveis locais são deletadas quando a função é completada
- Variáveis locais são deletadas quando você fecha a janela/tab
- Se você dar um valor diretamente uma variável sem declarar ela, automaticamente ela vai se tornar global (ex: `valor = 100`)
- No modo strict variáveis não declaradas não são globais automaticamente (ex: `valor = 100` não vai ser global no modo estrito)
- No JS objetos e funções também são variáveis
- Escopo determina a acessibilidade de variáveis, objetos e funções

## Remover objetos do namespace global (5)
- Namespace provê diferente escopos para identificadores (nomes de tipos, funções, variáveis, etc) para que não haja colisão entre esses nomes
- Exemplo: você pode usar uma variável com o mesmo nome em diferentes contextos/diferentes namespaces
- Para remover objetos do namespace global você pode usar: `delete global[variable]`

## "this" para referenciar um objeto que iniciou um evento (5)

```javascript
//Here, "this" references the global namespace
this.navigator.geolocation
window.onload = function () {
  //Here, "this" references the window object
  this...
}
document.getElementById("aDiv").onclick = function() {
  //Here, "this" references the DIV element
  this…
}
```

## Herança de um objeto (6)
- Usado para extender um objeto
- Extender um objeto é o mesmo que criar um novo prototype

```javascript
var popupBook = Object.create(
  Book.protoType,
  {
    hasSound: {value: true},
    showPopUp:{ value: function showPop() {
    //do logic to show a popup
    }
  }
});
```

**Inicializando um prototype:**

```javascript
function PopUpBook() {
  Book.call(this);
}
PopUpBook.prototype = Book.prototype;
PopUpBook.prototype.hasSound = false;
PopUpBook.prototype.showPopUp = function ShowPop() { };
```

## Crie funções com prototype (6)
- Acessando cafa elemento para inicializar um objeto não é muito eficiente, por isso podemos usar prototypes para ter mais construtores em um objeto

```javascript
Book.prototype = {
  ISBN: "",
  Length: -1,
  genre: "",
  covering: "",
  author: "",
  currentPage: 0,
  title: "",
  flipTo: function FlipToAPage(pNum) {
    this.currentPage = pNum;
  },
  turnPageForward: function turnForward() {
    this.flipTo(this.currentPage++);
  },
  turnPageBackward: function turnBackward() {
    this.flipTo(this.currentPage--);
  }
};
```

## Eventos comuns do DOM onBlur, onFocus, onClick (8)
- `blur` quando um evento perde o foco
- `focus`
- `click`
- `change` quando um input muda o estado
- `copy`
- `contextmenu`
- `dblclick`
- `drag` quando um elemento está sendo arrastado
- `dragend` quando finaliza de arrastar o elemento
- `dragover` quando o elemento arrastado está em cima do drop target
- `drop`
- `focusin` e `focusout`
- `fullscreenchange`
- `invalid`
- `keydown`, `keypress`, `keyup`
- `load`
- `mouseout`
- `resize`
- `scroll`
- `submit`
- `toggle`

## Bubbled events (8)
- Eventos bubbled é uma forma de propagação do eventos dentro do DOM
- No bubbled o primeiro evento capturado é aquele do elemento interior e então propagado para os eventos dos elementos externos a ele
- No capturing eventos, o primeiro evento capturado é aquele do elemento DOM mais externo e então propagado para os eventos dos elementos do DOM internos

## Configure e responda códigos de erro (9)
- Propriedades disponíveis no objeto exception:
  - message
  - number (erro de código numérico)
  - name

## Thrown exception (9)
- O statement `throw` permite gerar erros customizados
- Os erros customizados são aqueles além dos erros que o JS já reconhece
- Uma exception pode ser uma: String, Number, Boolean ou Objeto
- Se você usar `throw` com try e catch, você pode controlar o fluxo de mensagens
- Propriedades do objeto error: `name`, `message`
- Valores que podem ser retornados na propriedade `name`:
  - EvalError: erro na função `eval()`
  - RangeError: fora de alcance
  - ReferenceError
  - SyntaxError
  - TypeError
  - URIError: erro no `encodeURI()`

**Exemplo:**

```javascript
function myFunction() {
  var message, x;
  message = document.getElementById("message");
  message.innerHTML = "";
  x = document.getElementById("demo").value;
  try {
    if(x == "") throw "is Empty";
    if(isNaN(x)) throw "not a number";
    if(x > 10) throw "too high";
    if(x < 5) throw "too low";
  }
  catch(err) {
    message.innerHTML = "Input " + err;
  }
}
```

## Requisição de null checks (9)
- Checar valores nulos em javascript
- Você pode avaliar se especificamente é null, undefined, false, string vazia (`""`)
- Você usar também `Boolean(valor)`, se for um null check vai retornar false

## Try-catch-finally (9)
- O statement `try` permite testar se tem erros num bloco de código
- `catch` vai deixar você manipular o erro
- `trow` é para criar erros customizados
- `finally` permite executar código depois do `try...catch` indepenente se tiver dado erro ou não
- Quando ocorre um erro durante a execução de um script, o JS vai parar e gerar uma mensagem
- O termo técnico para isso é: "**throw an exception/error**"

```html
<p id="demo"></p>

<script>
try {
  adddlert("Welcome guest!"); // adddlert vai dar erro
}
catch(err) {
  document.getElementById("demo").innerHTML = err.message;
}
</script>
```

## Conecte eventos (10)
- Anotações

## Callback com funções anônimas (10)
- Anotações

## Ponteiro "this" (10)
- Anotações

## Inicie e pare um web worker (11)
- Web Workers roda no fundo e não interrompe o funcionamento da página
- Geralmente os web workers são usados para scripts que consomem muita CPU
- `postMessage()` posta a mensagem de volta para a página HTML (e você também pode usar para enviar mensagem para o Web Worker)

**Iniciando um web worker:**

```javascript
function startWorker() {
  if(typeof(Worker) !== "undefined") {
    if(typeof(w) == "undefined") {
      w = new Worker("demo_workers.js");
    }
    w.onmessage = function(event) {
      document.getElementById("result").innerHTML = event.data;
    };
  } else {
    document.getElementById("result").innerHTML = "Sorry, your browser does not support Web Workers...";
  }
}

function stopWorker() { 
  w.terminate();
  w = undefined;
}
```

**demo_workers.js:**

```javascript
var i = 0;

function timedCount() {
  i = i + 1;
  postMessage(i);
  setTimeout("timedCount()",500);
}

timedCount();
```

## Passe dados para um web worker (11)
- `postMessage()` para enviar mensagens
- `onmessage` para definir o handler que recebe as mensagens

No arquivo principal:
```javascript
worker.postMessage(data);
```

No web worker:
```javascript
self.addEventListener("message", function(e) {
    // the passed-in data is available via e.data
}, false);

// OU

onmessage = function(e) {
    // the passed-in data is available via e.data
};
```

## Configure intervalos e timouts para web workers (11)
```javascript
function timedCount() {
  i = i + 1;
  postMessage(i);
  setTimeout("timedCount()",500);
}
```

## Registre um event listener para um web worker (11)

```javascript
w.onmessage = function(event){
  document.getElementById("result").innerHTML = event.data;
};
```

## Limitações de um web worker (11)
- Como o web workers são arquivos externos, eles não tem acesso aos seguintes objetos Javascript:
  - Window object
  - Document object
  - Parant object
- Você não pode acessar o DOM, não pode carregar imagens e também não pode desenhar no canvas

## Regex para validar input (13)
- Você pode usar `pattern` no input a ser validado

```html
<input type="text" id="country_code" name="country_code"
  pattern="[A-Za-z]{3}" title="Three letter country code">
  <!-- apenas 3 letras (sem número, sem caracteres especiais) -->

<input type="password" id="pwd" name="pwd"
  pattern=".{8,}" title="Eight or more characters">
  <!-- precisa conter 8 ou mais caracteres -->

<input type="password" id="pwd" name="pwd"
  pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}"
  title="Must contain at least one  number and one uppercase and lowercase letter, and at least 8 or more characters">
```

## Validar tipo de dado correto com funções nativas (13)

```javascript
typeof 37 === 'number';
typeof "bla" === 'string';
typeof undefined === 'undefined';
typeof true === 'boolean';
typeof {a:1} === 'object';
typeof function(){} === 'function';
typeof Math.sin === 'function';
```

## Previna injeção de código (13)
- Previnir injeção de código é previnir que pessoas injetem código malicioso numa página para executar scripts
- Hackers podem usar o `eval()` para inserir códigos maliciosos
- Fazer validações no lado do cliente podem abrir brechas para injeção de código, validações devem ser feitas no server side
- Não usar `innerHTML` para inserir algo na tela, porque permite inserir código malicioso
- Você pode tratar código malicioso inserido pelo usuário por meio de inputs fazendo o encoding para o código ser lido como string e não como código JS/HTML
- Exemplo: salvar tags HTML como string (texto) e não como código HTML: `html = html.replace(/</g, "&lt;").replace(/>/g, "&gt;");`

## Recupere dados usando web services (14)
- Anotações

## Receba dados com XMLHTTPRequest (14)

```javascript
var xReq = new XMLHttpRequest();
xReq.open("GET", "myXMLData.xml", false);
xReq.timeout = 2000;
xReq.ontimeout = function () {
  $("#results").text("Request Timed out");
}
xReq.send(null);
$("#results").text(xReq.response);
```

## Manipule dados binários (15)
- Anotações

## Parse data (15)
- Anotações

## Envie dados usando XMLHTTPResquest (15)

- O JS pode receber dados em HTML com o XMLHTTPResquest que recebe dados de um web service, REST API ou outros provedores
- Propriedades: readyState, Response, responseBody, Status, etc
- Métodos: Abort, getResonseHeader, Send, setRequestHeader, etc

```javascript
$("document").ready(function () {
  $("#btnGetXMLData").click(function () {
    var xReq = new XMLHttpRequest();
    xReq.open("GET", "myXMLData.xml", false);
    xReq.send(null);
    $("#results").text(xReq.response);
  });
});
```

##  Escopo de variáveis locais e globais (5)
- Variáveis locais só existem dentro de blocos (funções) e globais podem ser usadas no namespace global do javascript, ou seja, em qualquer lugar do código

##  Impemente objetos nativos (6)

- Tudo no JS são objetos. Todos os objetos são baseados em um prototype. Quando você cria uma nova instância de um objeto, essa instância é baseada um prototype de um objeto

```javascript
var squareValue = Math.sqrt(144);
var listofPrimeNumbers = new Array(1, 2, 3, 5, 7, 11, 13, 17, 19, 23);
```

##  Implemente métodos nativos (6)

- Exemplos de métodos nativos para trabalhar com o DOM

```javascript
valor.getElementById("myId");
valor.getElementsByTagName("p");
```

##  Crie métodos próprios (6)

```javascript
var book = {
  ISBN: "55555555",
  Length: 560,
  genre: "programming",
  covering: "soft",
  author: "John Doe",
  currentPage: 5,
  title: "My Big Book of Wonderful Things",
  flipTo: function flipToAPage(pNum) {
    this.currentPage = pNum;
  },
  turnPageForward: function turnForward() {
    this.flipTo(this.currentPage++);
  },
  turnPageBackward: function turnBackward() {
    this.flipTo(this.currentPage--);
  }
}
```

## Interagindo com a UI

```javascript
getElementById
getElementByClassName
getEelementsByTagName
querySelector
querySelectorAll // queryAll não tem mais
```

## Diferença entre call(), apply() e bind()

- Os 3 são usados para alterar o valor de this
- `call()` útil para reutilização de código

```javascript
let personRenata = {
  name: 'Renata',
  age: 23
}

function hello() {
  return `Hello, my name is ${this.name} and I have ${this.age} years old.`
}

hello.call(personRenata) // personRenata é o this, retorna: Hello, my name is Renata and I have 23 years old.
```

- `aplly()` parecido com o call, porém utiliza como parâmetro array

```javascript
function addsNumbers(n1, n2, n3) {
  return this * n1 * n2 * n3
}

arr123 = [1, 2, 3]

addsNumbers.apply(1, arr123) // o 1 é o this e retorna 6
```

- o `bind()` é o mais diferente, pois além de alterar o valor de this, também consegue aumentar o número de parâmetros de uma função
- É útil quando queremos manipular valores dentro de callbacks

```javascript
function multiplyThis(n1, n2) {
  return this * n1 * n2
}

let thisIs2 = multiplyThis.bind(2) // cria uma nova função que o valor de this é 2
let thisIs2N1Is3 = multiplyThis.bind(2, 3) // cria uma nova função que o this é 2 e o n1 é 3
let thisIs2N1Is3N2Is3 = multiplyThis.bind(2, 3, 3) // cria uma nova função em que this é 2, n1 é 3 e n2 é 3

thisIs2(3, 3) // somente altera o this, retorna 18
thisIs2N1Is3(3) // altera o this e n1, retorna 18
thisIs2N1Is3N2Is3() // altera o this e todos os parâmetros, retorna 18
```

## Outras dicas
- Objetos estáticos do JS: você não precisa instânciar para ser utilizados. Ex: `Math.sqrt()`
- `map()` possibilita mudar o valor do array
- `splice()` muda o array, o `slice()` cria um novo array
- `statements` no JS: block (`{}`), break, continue, Empty, if...else, switch, throw, try...catch

- `eval()` recebe uma string e avalia expressões e declarações

```javascript
var expression = new String("2 + 2");
eval(expression.toString()); // retorna 4
```
