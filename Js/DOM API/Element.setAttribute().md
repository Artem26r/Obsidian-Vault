Добавляет новый атрибут или изменяет значение существующего атрибута у выбранного элемента.

Синтаксис
```
element.setAttribute(name, value);
```

-   `name` - имя атрибута (строка).
-   `value` - значение атрибута.

Пример
В следующем примере, `setAttribute()` используется, чтобы установить атрибут [`disabled`](https://developer.mozilla.org/ru/docs/Web/HTML/Global_attributes#disabled) кнопки [`<button>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/button), делая её отключённой.

```
<button>Hello World</button>
```

```
var b = document.querySelector("button");

b.setAttribute("disabled", "disabled");
```

Примечания

При вызове на элементе внутри HTML документа, setAttribute переведёт имя атрибута в нижний регистр.

Если указанный атрибут уже существует, его значение изменится на новое. Если атрибута ранее не существовало, он будет создан.

Несмотря на то, что метод [`getAttribute()`](https://developer.mozilla.org/ru/docs/Web/API/Element/getAttribute) возвращает null у удалённых атрибутов, вы должны использовать [removeAttribute() (en-US)](https://developer.mozilla.org/en-US/docs/Web/API/Element/removeAttribute "Currently only available in English (US)") вместо _elt_.setAttribute(_attr_, null), чтобы удалить атрибут. Последний заставит значение `null` быть строкой `"null"`, которая, вероятно, не то, что вы хотите.

Использование setAttribute() для изменения определённых атрибутов особенно значимо в XUL, так как работает непоследовательно, а атрибут определяет значение по умолчанию. Для того, чтобы получить или изменить текущие значения, вы должны использовать свойства. Например, elt.value вместо elt.setAttribure('value', val).

Чтобы установить атрибут, которому значение не нужно, такой как, например, атрибут `autoplay` элемента [`<audio>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/audio), используйте null или пустое значение. Например: `elt.setAttribute('autoplay', '')`

Методы DOM имеют дело с атрибутами элементов:

#dom-api #element