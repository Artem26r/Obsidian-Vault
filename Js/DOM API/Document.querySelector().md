[`Document`](https://developer.mozilla.org/ru/docs/Web/API/Document) метод **`querySelector()`** возвращает первый элемент ([`Element`](https://developer.mozilla.org/ru/docs/Web/API/Element)) документа, который соответствует указанному селектору или группе селекторов. Если совпадений не найдено, возвращает значение `null`.

Синтаксис
```
element = document.querySelector(selectors);
```

Параметры
селекторы
[`DOMString`](https://developer.mozilla.org/ru/docs/conflicting/Web/JavaScript/Reference/Global_Objects/String_6fa58bba0570d663099f0ae7ae8883ab), содержащий один или более селекторов для сопоставления. Эта строка должна быть допустимой строкой селектора CSS; если же нет, генерируется исключение `SYNTAX_ERR`. Смотрите [Расположение элементов DOM с использованием селекторов](https://developer.mozilla.org/ru/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors) для того, чтобы узнать больше о селекторах и о том, как ими управлять.

**Примечание:** Символы, которые не являются частью стандартного синтаксиса CSS должны быть экранированы символом обратной косой черты. Поскольку JavaScript также использует экранирование символом обратной косой черты, будьте особенно внимательны при написании строковых литералов с использованием этих символов. См. [Escaping special characters](https://developer.mozilla.org/ru/docs/Web/API/Document/querySelector#escaping_special_characters) для получения дополнительной информации.

Возвращаемое значение
Ссылка на объект типа [`Element`](https://developer.mozilla.org/ru/docs/Web/API/Element), являющийся первым элементов в документе, который соответствует указанному набору [CSS селекторов](https://developer.mozilla.org/ru/docs/Web/CSS/CSS_Selectors), либо `null`, если совпадений нет.

Если вам нужен список всех элементов, соответствующих указанным селекторам, используйте функцию [`querySelectorAll()`](https://developer.mozilla.org/ru/docs/Web/API/Document/querySelectorAll "querySelectorAll()").

Более сложный селектор
Селекторы, передаваемые в querySelector, могут быть использованы и для точного поиска, как показано в примере ниже. В данном примере возвращается элемент ```

```
<input name="login"/>, находящийся в <div class="user-panel main">:
```

```
var el = document.querySelector("div.user-panel.main input[name=login]");
```

#dom-api #document #js