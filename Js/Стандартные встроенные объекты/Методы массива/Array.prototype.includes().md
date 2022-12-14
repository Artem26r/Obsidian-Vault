Метод **`includes()`** определяет, содержит ли массив определённый элемент, возвращая в зависимости от этого `true` или `false`.

```
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false
```

```
arr.includes(searchElement[fromIndex = 0])
```

Параметры

```
searchElement
// Искомый элемент.
```

```
fromIndex 
// Необязательный
```
Позиция в массиве, с которой начинать поиск элемента searchElement. При отрицательных значениях поиск производится начиная с индекса array.length + fromIndex по возрастанию. Значение по умолчанию равно 0.

Возвращаемое значение
Boolean.

```
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

fromIndex больше или равен длине массива
Если fromIndex больше или равен длине массива, то возвращается false. При этом поиск не производится.
```
var arr = ['a', 'b', 'c'];

arr.includes('c', 3);   // false
arr.includes('c', 100); // false
```

Вычисленный индекс меньше нуля 0
Если fromIndex отрицательный, то вычисляется индекс, начиная с которого будет производиться поиск элемента searchElement. Если вычисленный индекс меньше нуля, то поиск будет производиться во всём массиве.
```
// длина массива равна 3
// fromIndex равен -100
// вычисленный индекс равен 3 + (-100) = -97

var arr = ['a', 'b', 'c'];

arr.includes('a', -100); // true
arr.includes('b', -100); // true
arr.includes('c', -100); // true
```

Использование includes() в качестве общих метода
includes() специально сделан общим. Он не требует, чтобы this являлся массивом, так что он может быть применён к другим типам объектов (например, к массивоподобным объектам). Пример ниже показывает использование метода includes() на объекте arguments.
```
(function() {
  console.log([].includes.call(arguments, 'a')); // true
  console.log([].includes.call(arguments, 'd')); // false
})('a','b','c');
```

#Arrayprototype
#js