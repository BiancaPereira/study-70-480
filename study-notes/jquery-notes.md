# Anotações de jQuery

- [Anotações de jQuery](#anotações-de-jquery)
  - [Chamada ajax (10)](#chamada-ajax-10)
  - [Serialize (15)](#serialize-15)
  - [Form.Submit (15)](#formsubmit-15)
  - [Localize elementos por seletores (20)](#localize-elementos-por-seletores-20)
  - [Async with jQuery](#async-with-jquery)
  - [Show/hide com jQuery](#showhide-com-jquery)

## Chamada ajax (10)

```javascript
$.ajax({
    url: 'action.php', // caminho da requisição
    type: 'POST',
    data: formData,
    async: true, // default é true
    cache: true, // default é true
    complete: someFunc, // chamado após sucesso ou erro
}).done(function(data) {...}).fail(func).always(func);
```

- Também dá para usar o `.post()` para fazer a requisição acima

```javascript
$.post("ajax/test.html", function(data) {
  $(".result").html(data);
});
```

## Serialize (15)

- Usado para encodar dados de formulários em strings para enviar na submissão do form (ex: `?rua=Rua%20Piriquito&numero=32`)

```javascript
$("form").serialize();
$("form").serializeArray(); // mesma coisa, mas transforma em array
$.parseXML("string"); // string em XML que é transformada em objeto XML
JSON.parse(str);
JSON.stringify(obj);
$.parseJSON(str);
encodeURI(str); // enconde URL para usar como URI
encodeURIComponent(str); // encode string para usar como parte de URL
```

## Form.Submit (15)

```javascript
$("#other").click(function() {
  $("#target").submit();
});
```

## Localize elementos por seletores (20)

```javascript
$("#myId");
$(".myClass");
$("input[name='first_name']"); // por atributo
$("#contents ul.people li"); // elementos css compostos
$("div.myClass, ul.people"); // separando por listas com vírgula
$("a.external:first"); // pseudo elementos
```

## Async with jQuery

- Promises criadas por um objeto $.Deferred()
- Métodos deferidos (concedidos):
  - resolve
  - resolveWith
  - notify
  - notifyWith
  - reject
  - rejectWith
  - promise
- Métodos de promise:
  - always
  - done
  - fail
  - pipe
  - progress
  - state
  - then

## Show/hide com jQuery

```javascript
// sintaxe: $(selector).hide(speed,callback);

$("button").click(function(){
  $("p").hide(1000);
});

// outro exemplo
$("#hide").click(function(){
  $("p").hide();
});

$("#show").click(function(){
  $("p").show();
});
```
