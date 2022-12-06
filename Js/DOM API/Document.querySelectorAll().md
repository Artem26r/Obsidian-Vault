Метод **`querySelectorAll()`** [`Document`](https://developer.mozilla.org/ru/docs/Web/API/Document) возвращает статический (не динамический) [`NodeList`](https://developer.mozilla.org/ru/docs/Web/API/NodeList), содержащий все найденные элементы документа, которые соответствуют указанному селектору.

Синтаксис
```
elementList = document.querySelectorAll(selectors);
```

Параметры
```
selectors
```
Строка [`DOMString`](https://developer.mozilla.org/ru/docs/conflicting/Web/JavaScript/Reference/Global_Objects/String_6fa58bba0570d663099f0ae7ae8883ab), содержащая один или более [CSS селектор (en-US)](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors "Currently only available in English (US)"). Эта строка должна быть валидным [CSS селектором](https://developer.mozilla.org/ru/docs/Web/CSS/CSS_Selectors). Если это не так, то генерируется `SyntaxError`. Смотрите [Поиск элементов DOM с использованием селекторов](https://developer.mozilla.org/ru/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors) для получения информации о том, распознавать элементы. Несколько селекторов нужно разделить запятыми.

Возвращаемое значение
Статический (non-live) [`NodeList`](https://developer.mozilla.org/ru/docs/Web/API/NodeList), содержащий все элементы в пределах документа, которые соответствуют как минимум одному из указанных селекторов, или пустой [`NodeList`](https://developer.mozilla.org/ru/docs/Web/API/NodeList) в случае отсутствия совпадений.

**Примечание:** Если в строке `selectors` содержатся [CSS псевдоэлементы](https://developer.mozilla.org/ru/docs/Web/CSS/Pseudo-elements), то возвращаемый список будет всегда пуст.

Примеры
Получение списка совпадений
Чтобы получить NodeList всех элементов `<p>` в документе:
```
var matches = document.querySelectorAll("p");
```

В этом примере возвращается список всех элементов [`<div>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/div) в документе, которые имеют класс `note` или `alert`:
```
var matches = document.querySelectorAll("div.note, div.alert");
```

Здесь мы получаем список элементов `<p>`, чьим непосредственным родительским элементом является [`<div>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/div) с классом `highlighted`, который расположен внутри контейнера с идентификатором `test`.
```
var container = document.querySelector("#test");
var matches = container.querySelectorAll("div.highlighted > p");
```

В этом примере используются [селекторы атрибутов](https://developer.mozilla.org/ru/docs/Web/CSS/Attribute_selectors), чтобы вернуть список элементов [`<iframe>` (en-US)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe "Currently only available in English (US)"), которые содержат атрибут `data-src`:
```
var matches = document.querySelectorAll("iframe[data-src]");
```

Здесь селектор атрибута используется для возврата элементов списка, содержащихся в списке с идентификатором `"userlist"`, который имеет атрибут `"data-active"` со значением `"1"`
```
var container = document.querySelector("#userlist");
var matches = container.querySelectorAll("li[data-active='1']");
```

Доступ к совпадениям
Вернув [`NodeList`](https://developer.mozilla.org/ru/docs/Web/API/NodeList) совпадений один раз, вы можете использовать его как простой массив. Если массив пустой (т. е. свойство `length` равно 0), то совпадений не было найдено.

В другом случае, вы можете использовать стандартную запись массива для доступа к содержимому. Вы можете использовать любой оператор зацикливания, например:

```
var highlightedItems = userList.querySelectorAll(".highlighted");

highlightedItems.forEach(function(userItem) {
  deleteUser(userItem);
});
```

#dom-api
#document