Возвращает ссылку на элемент по его идентификатору ([ID (en-US)](https://developer.mozilla.org/en-US/docs/Web/API/Element/id "Currently only available in English (US)")); идентификатор является строкой, которая может быть использована для идентификации элемента; она может быть определена при помощи атрибута `id` в HTML или из скрипта.

Синтаксис
```
element = document.getElementById(id);
```

Возвращаемое значение
ссылка на объект типа Element соответствующий указанному ID или null, если элемент с указанным ID не найден в документе.

**Элементы вне документа** не ищутся `getElementById()`. При создании элемента и назначении ему ID, вам следует вставить элемент в дерево документа с помощью [`Node.insertBefore()`](https://developer.mozilla.org/ru/docs/Web/API/Node/insertBefore) или подобным методом, до того как вы сможете получить к нему доступ при помощи `getElementById()`:

```
var element = document.createElement("div");
element.id = 'testqq';
var el = document.getElementById('testqq'); // el will be null!
```

#dom-api #document #js