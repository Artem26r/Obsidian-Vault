Возвращает массивоподобный (итерируемый) объект всех дочерних элементов, соответствующих всем из указанных имён классов. В случае вызова по отношению к объекту 'document', поиск происходит по всему документу, включая корневой элемент. Вызывать [`getElementsByClassName()`](https://developer.mozilla.org/ru/docs/Web/API/Element/getElementsByClassName "getElementsByClassName()") можно также применительно к любому элементу: возвращены будут лишь те элементы, которые являются потомками указанного корневого элемента и имеют при этом указанные классы.

Синтаксис
```
var elements = document.getElementsByClassName(names); // или:
var elements = rootElement.getElementsByClassName(names);
```

-   _В "elements"_ будет текущая [`HTMLCollection`](https://developer.mozilla.org/ru/docs/Web/API/HTMLCollection) найденных элементов.
-   _"names"_ - строка, состоящая из списка имён искомых классов; имена классов разделяют пробелами.
-   getElementsByClassName может быть вызвана по отношению к любому элементу, не только для документа целиком. ("document"). Элемент, по отношению к которому осуществляется вызов, используется для целей поиска в качестве корневого элемента.

Мы также можем использовать методы из Array.prototype по отношению к любой [`HTMLCollection`](https://developer.mozilla.org/ru/docs/Web/API/HTMLCollection), передавая коллекцию в качестве значения _this_ метода. Код в примере найдёт все элементы 'div' с классом 'test':
```
var testElements = document.getElementsByClassName('test');
var testDivs = Array.prototype.filter.call(testElements, function(testElement){
    return testElement.nodeName === 'DIV';
});
```

#dom-api #document #js