`getAttribute()` возвращает значение указанного атрибута элемента. Если элемент не содержит данный атрибут, могут быть возвращены `null` или `""` (пустая строка); подробнее [Notes](https://developer.mozilla.org/ru/docs/Web/API/Element/getAttribute#notes).

Синтаксис
```
var attribute = element.getAttribute(attributeName);
```

где

-   `attribute` - переменная, которой будет присвоено значение `attributeName`.
-   `attributeName` - имя атрибута, значение которого необходимо получить.

Пример
```
var div1 = document.getElementById("div1");
var align = div1.getAttribute("align");
alert(align); // отобразит значение атрибута align элемента с id="div1"
```

Примечания
Когда метод getAttribute вызывается применительно к HTML-элементу, в DOM HTML-документа, значение аргумента приводится к нижнему регистру.

В действительности все браузеры (Firefox, Internet Explorer, последние версии Opera, Safari, Konqueror, iCab и т.д.) возвращают null, когда выбранный элемент не содержит атрибута с переданным именем. Спецификация DOM определяет, что корректное возвращаемое значение в данном случае - пустая строка и некоторые реализации DOM придерживаются такого поведения. Реализация getAttribute в XUL (Gecko) в настоящее время следует спецификации и возвращает пустую строку. Следовательно, имеет смысл использовать hasAttribute, чтобы проверять наличие атрибутов перед вызовом getAttribute(), если может быть такое, что выбранный элемент не будет содержать искомого атрибута.

#dom-api #element #js