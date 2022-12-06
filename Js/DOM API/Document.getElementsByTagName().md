Возвращает [`HTMLCollection`](https://developer.mozilla.org/ru/docs/Web/API/HTMLCollection) элементов с указанным именем тега. Поиск осуществляется по всему документу, включая корневой узел. Возвращаемая HTMLCollection живая, это значит что она автоматически обновляет сама себя чтобы оставаться синхронизированной с DOM деревом без необходимости вызова document.getElementByTagName() снова.

Синтаксис
```
var elements = document.getElementsByTagName(name);
```
-   `elements` это живая [`HTMLCollection`](https://developer.mozilla.org/ru/docs/Web/API/HTMLCollection) (с учётом примечания внизу) найденных документов в таком порядке в каком они появляются в дереве.
-   `name` строка представляющая собой имя элемента. Специальная строка "*" позволяет получить все элементы.

#dom-api  #document