Свойство **`Node.parentElement`** только для чтения, возвращает родителя узла DOM [`Element`](https://developer.mozilla.org/ru/docs/Web/API/Element), или `null` если узел не имеет родителя, или его родитель не DOM [`Element`](https://developer.mozilla.org/ru/docs/Web/API/Element).

Синтаксис
```
parentElement = node.parentElement
```

`parentElement` это родительский элемент текущего узла. Это всегда объект DOM [`Element`](https://developer.mozilla.org/ru/docs/Web/API/Element), или `null`.

Пример
```
if (node.parentElement) {
    node.parentElement.style.color = "red";
}
```

#dom-api #node #js