**`NonDocumentTypeChildNode.nextElementSibling`** свойство только для чтения, возвращающее последующий элемент перед текущим, или `null`, если элемент является последним в своём родительском узле.

Синтаксис
```
var nextNode = elementNodeReference.nextElementSibling;
```

Пример
```
<div id="div-01">Это div-01</div>
<div id="div-02">Это div-02</div>

<script type="text/javascript">
  var el = document.getElementById('div-01').nextElementSibling;
  console.log('Сосед div-01:');
  while (el) {
    console.log(el.nodeName);
    el = el.nextElementSibling;
  }
</script>
```

Этот пример выведет в консоль следующее:

```
Сосед div-01:
DIV
SCRIPT
```

#dom-api #node #js