Метод **`push()`** добавляет один или более элементов в конец массива и возвращает новую длину массива.
**Мутирует**

```
arr.push(element1, ..., elementN)
```

```
var sports = ['футбол', 'бейсбол'];
var total = sports.push('американский футбол', 'плавание');

console.log(sports); // ['футбол', 'бейсбол', 'американский футбол', 'плавание']
console.log(total);  // 4
```

#Arrayprototype
#js