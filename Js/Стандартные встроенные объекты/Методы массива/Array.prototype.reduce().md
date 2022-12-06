Метод **`reduce()`** применяет функцию **`reducer`** к каждому элементу массива (слева-направо), возвращая одно результирующее значение.

```
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10
```

```
array.reduce(callback[, initialValue])
```

Параметры

```
callback
//Функция, выполняющаяся для каждого элемента массива, принимает четыре аргумента:
```

```
accumulator
Аккумулятор, аккумулирующий значение, которое возвращает функция callback после посещения очередного элемента, либо значение initialValue, если оно предоставлено (смотрите пояснения ниже).
```

```
currentValue
Текущий обрабатываемый элемент массива.
```

```
index //Необязательный
Индекс текущего обрабатываемого элемента массива.
```

```
array //Необязательный
Массив, для которого была вызвана функция reduce.
```

```
initialValue //Необязательный
Необязательный параметр. Объект, используемый в качестве первого аргумента при первом вызове функции callback.
```

Описание
Метод `reduce()` выполняет функцию `callback` один раз для каждого элемента, присутствующего в массиве, за исключением пустот, принимая четыре аргумента: начальное значение (или значение от предыдущего вызова `callback`), значение текущего элемента, текущий индекс и массив, по которому происходит итерация.

При первом вызове функции, параметры `accumulator` и `currentValue `могут принимать одно из двух значений. Если при вызове `reduce()` передан аргумент `initialValue`, то значение accumulator будет равным значению` initialValue`, а значение ``currentValue`` будет равным первому значению в массиве. Если аргумент `initialValue` не задан, то значение accumulator будет равным первому значению в массиве, а значение `currentValue` будет равным второму значению в массиве.

Если массив пустой и аргумент` initialValue` не указан, будет брошено исключение `TypeError`. Если массив состоит только из одного элемента (независимо от его положения в массиве) и аргумент `initialValue` не указан, или если аргумент `initialValue` указан, но массив пустой, то будет возвращено одно это значение, без вызова функции `callback`.

Предположим, что` reduce()` используется следующим образом:

```
[0, 1, 2, 3, 4].reduce(function(previousValue, currentValue, index, array) {
  return previousValue + currentValue;
});
```

Колбэк-функция будет вызвана четыре раза, аргументы и возвращаемое значение при каждом вызове будут следующими:

![[Pasted image 20221130055656.png]]

Значение, возвращённое методом `reduce()` будет равным последнему результату выполнения колбэк-функции — `10`.

Если же вы зададите начальное значение `initialValue`, результат будет выглядеть так:

```
[0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, index, array) {
  return accumulator + currentValue;
}, 10);
```

![[Pasted image 20221130055747.png]]

Значение, возвращённое методом `reduce()` на этот раз, конечно же, будет равным `20`.

Примеры
Суммирование всех значений в массиве
```
var total = [0, 1, 2, 3].reduce(function(a, b) {
  return a + b;
});
// total == 6
```

Суммирование значений в массиве объектов
Чтобы суммировать значения, содержащиеся в массиве объектов, вы должны указать initialValue, чтобы каждый элемент смог пройти через callback.
```
var initialValue = 0;
var sum = [{x: 1}, {x:2}, {x:3}].reduce(function (accumulator, currentValue) {
    return accumulator + currentValue.x;
}, initialValue)
// sum == 6
```

Тоже самое, но со стрелочной функцией:
```
var initialValue = 0;
var sum = [{x: 1}, {x:2}, {x:3}].reduce(
    (accumulator, currentValue) => accumulator + currentValue.x,
    initialValue
);
// sum == 6
```

Разворачивание массива массивов
```
var flattened = [[0, 1], [2, 3], [4, 5]].reduce(function(a, b) {
  return a.concat(b);
});
// flattened равен [0, 1, 2, 3, 4, 5]
```

Пример: склеивание массивов, содержащихся в объектах массива, с использованием оператора расширения и initialValue
```
// friends - список из объектов(друзей)
// где поле "books" - список любимых книг друга
var friends = [
{ name: "Anna", books: ["Bible", "Harry Potter"], age: 21 },
{ name: "Bob", books: ["War and peace", "Romeo and Juliet"], age: 26 },
{ name: "Alice", books: ["The Lord of the Rings", "The Shining"], age: 18 }
]

// allbooks - список, который будет содержать все книги друзей +
// дополнительный список указанный в initialValue
var allbooks = friends.reduce(function(prev, curr) {
  return [...prev, ...curr.books];
}, ["Alphabet"]);

// allbooks = ["Alphabet", "Bible", "Harry Potter", "War and peace",
// "Romeo and Juliet", "The Lord of the Rings", "The Shining"]
```

#Arrayprototype