Метод **`forEach()`** выполняет указанную функцию один раз для каждого элемента в массиве.

```
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"
```

Синтаксис
```
arr.forEach(function callback(currentValue, index, array) {
    //your iterator
}[, thisArg]);
```

Параметры

```
callback
Функция, которая будет вызвана для каждого элемента массива. Она принимает от одного до трёх аргументов:
```

```
currentValue
Текущий обрабатываемый элемент в массиве.
```

```
index //еобязательный
Индекс текущего обрабатываемого элемента в массиве.
```

```
array //Необязательный
Массив, по которому осуществляется проход.
```

```
thisArg
Необязательный параметр. Значение, используемое в качестве this при вызове функции callback.
```

Возвращаемое значение
`undefined`.

Описание

Метод `forEach()` выполняет функцию `callback` один раз для каждого элемента, находящегося в массиве в порядке возрастания. Она не будет вызвана для удалённых или пропущенных элементов массива. Однако, она будет вызвана для элементов, которые присутствуют в массиве и имеют значение [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Функция `callback` будет вызвана с **тремя аргументами**:

-   значение элемента (**value**)
-   индекс элемента (**index**)
-   массив, по которому осуществляется проход (**array**)

Если в метод `forEach()` был передан параметр `thisArg`, при вызове `callback` он будет использоваться в качестве значения `this`. В противном случае, в качестве значения `this` будет использоваться значение [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined). В конечном итоге, значение `this`, наблюдаемое из функции `callback`, определяется согласно [``обычным правилам определения `this`, видимого из функции``](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/this).

Диапазон элементов, обрабатываемых методом `forEach()`, устанавливается до первого вызова функции `callback`. Элементы, добавленные в массив после начала выполнения метода `forEach()`, не будут посещены функцией `callback`. Если существующие элементы массива изменятся, значения, переданные в функцию `callback`, будут значениями на тот момент времени, когда метод `forEach()` посетит их; удалённые элементы посещены не будут. Если уже посещённые элементы удаляются во время итерации (например, с помощью [`shift()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)), последующие элементы будут пропущены. ([`Смотри пример ниже`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach#%D0%9C%D0%BE%D0%B4%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F_%D0%BC%D0%B0%D1%81%D1%81%D0%B8%D0%B2%D0%B0_%D0%B2%D0%BE_%D0%B2%D1%80%D0%B5%D0%BC%D1%8F_%D0%B8%D1%82%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8))


**Примечание:** Не существует способа остановить или прервать цикл `forEach()` кроме как выбрасыванием исключения. Если вам необходимо такое поведение, метод `forEach()` неправильный выбор.

Досрочное прекращение может быть достигнуто с:

-   Простой цикл [`for`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/for)
-   Циклы [`for...of`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/for...of) / [`for...in`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/for...in)
-   [`Array.prototype.every()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
-   [`Array.prototype.some()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
-   [`Array.prototype.find()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
-   [`Array.prototype.findIndex()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

Если нужно протестировать элементы массива на условие и нужно вернуть булево значение, вы можете воспользоваться методами [`every()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/every), [`some()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/some), [`find()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/find) или [`findIndex()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex).

Метод `forEach()` выполняет функцию `callback` один раз для каждого элемента массива; в отличие от методов [`every()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/every) и [`some()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/some), он всегда возвращает значение [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Примеры

Нет операции для неинициализированных значений (разреженные массивы)
```
const arraySparse = [1,3,,7]
let numCallbackRuns = 0

arraySparse.forEach((element) => {
  console.log(element)
  numCallbackRuns++
})

console.log("numCallbackRuns: ", numCallbackRuns)

// 1
// 3
// 7
// numCallbackRuns: 3
// комментарий: как вы видите пропущенное значение между 3 и 7 не вызывало функцию callback.
```

Конвертируем цикл for в forEach
```
const items = ['item1', 'item2', 'item3']
const copy = []

// до
for (let i = 0; i < items.length; i++) {
  copy.push(items[i])
}

// после
items.forEach(function(item){
  copy.push(item)
})
```

Печать содержимого массива
**Примечание:** Для отображения содержимого массива в консоли вы можете использовать [`console.table()`](https://developer.mozilla.org/ru/docs/Web/API/Console/table), который выводит отформатированную версию массива.

Следующий пример иллюстрирует альтернативный подход, использующий `forEach()`.

Следующий код выводит каждый элемент массива на новой строке журнала:
```
function logArrayElements(element, index, array) {
  console.log('a[' + index + '] = ' + element);
}

// Обратите внимание на пропуск по индексу 2, там нет элемента, поэтому он не посещается
[2, 5, , 9].forEach(logArrayElements);
// логи:
// a[0] = 2
// a[1] = 5
// a[3] = 9
```

Использование thisArg
Следующий (надуманный) пример обновляет свойства объекта, когда перебирает записи массива:
```
function Counter() {
  this.sum = 0
  this.count = 0
}
Counter.prototype.add = function(array) {
  array.forEach((entry) => {
    this.sum += entry
    ++this.count
  }, this)
  // ^---- Note
}

const obj = new Counter()
obj.add([2, 5, 9])
obj.count
// 3
obj.sum
// 16
```

Поскольку в `forEach()` передан параметр `thisArg` (`this`), он затем передаётся в `callback` при каждом вызове. И callback использует его в качестве собственного значения `this`.
**Примечание:** Если при передаче callback функции используется [`выражение стрелочной функции`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Arrow_functions), параметр `thisArg` может быть опущен, так как все стрелочные функции лексически привязываются к значению[`this`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/this).


Прерывание цикла
Следующий код использует [`Array.prototype.every()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/every) для логирования содержимого массива и останавливается при превышении значением заданного порогового значения `THRESHOLD`.
```
var THRESHOLD = 12;
var v = [5, 2, 16, 4, 3, 18, 20];
var res;

res = v.every(function(element, index, array) {
  console.log('element:', element);
  if (element >= THRESHOLD) {
    return false;
  }

  return true;
});
console.log('res:', res);
// логи:
// element: 5
// element: 2
// element: 16
// res: false

res = v.some(function(element, index, array) {
  console.log('element:', element);
  if (element >= THRESHOLD) {
    return true;
  }

  return false;
});
console.log('res:', res);
// логи:
// element: 5
// element: 2
// element: 16
// res: true
```

Функция копирования объекта
Следующий код создаёт копию переданного объекта. Существует несколько способов создания копии объекта, и это один из них. Он позволяет понять, каким образом работает `Array.prototype.forEach()`, используя функции мета-свойств `Object.*` из ECMAScript 5.
```
function copy(o) {
  var copy = Object.create(Object.getPrototypeOf(o));
  var propNames = Object.getOwnPropertyNames(o);

  propNames.forEach(function(name) {
    var desc = Object.getOwnPropertyDescriptor(o, name);
    Object.defineProperty(copy, name, desc);
  });

  return copy;
}

var o1 = { a: 1, b: 2 };
var o2 = copy(o1); // теперь o2 выглядит также, как и o1
```

Модификация массива во время итерации
В следующем примере в лог выводится `"one"`, `"two"`, `"four"`.
При достижении записи, содержащей значение `'two'`, первая запись всего массива удаляется, в результате чего все оставшиеся записи перемещаются на одну позицию вверх. Поскольку элемент `'four'` теперь находится на более ранней позиции в массиве, `'three'` будет пропущен.

`forEach()` не делает копию массива перед итерацией.
```
let words = ['one', 'two', 'three', 'four']
words.forEach((word) => {
  console.log(word)
  if (word === 'two') {
    words.shift()
  }
})
// one
// two
// four
```

Выравнивание (уплощение) массива
Следующий пример приведён только для целей обучения. Если вы хотите выравнять массив с помощью встроенных методов, вы можете использовать [`Array.prototype.flat()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)
```
function flatten(arr) {
  const result = []

  arr.forEach((i) => {
    if (Array.isArray(i)) {
      result.push(...flatten(i))
    } else {
      result.push(i)
    }
  })

  return result
}

// Usage
const nested = [1, 2, 3, [4, 5, [6, 7], 8, 9]]

flatten(nested) // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#Arrayprototype
#immutable