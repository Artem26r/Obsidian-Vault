Описание
Свойство **`classList`** возвращает псевдомассив [`DOMTokenList`](https://developer.mozilla.org/ru/docs/Web/API/DOMTokenList), содержащий все классы элемента.

Синтаксис
```
var elementClasses = elem.classList;
```

-   Результат - псевдомассив [`DOMTokenList`](https://developer.mozilla.org/ru/docs/Web/API/DOMTokenList), содержащий все классы узла **elem**

Методы

**ClassList** является геттером. Возвращаемый им объект имеет несколько методов:

add( String [,String] )

Добавляет элементу указанные классы

remove( String [,String] )

**Удаляет у элемента указанные классы **item** ( Number ) Результат аналогичен вызову **`сlassList[Number]`** **toggle** ( String [, Boolean]) Если класс у элемента отсутствует - добавляет, иначе - убирает. Когда вторым параметром передано false - удаляет указанный класс, а если true - добавляет. Если вторым параметром передан undefined или переменная с typeof == 'undefined', поведение будет аналогичным передаче только первого параметра при вызове toggle. **contains** ( String ) Проверяет, есть ли данный класс у элемента (вернёт true или false)

**Примечание:** И, конечно же, у **ClassList** есть заветное свойство **length**, которое возвращает количество классов у элемента.

#dom-api #element