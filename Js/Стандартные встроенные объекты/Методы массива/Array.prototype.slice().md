https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/slice#
Метод **`slice()`** возвращает новый массив, содержащий копию части исходного массива.

```
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

console.log(animals.slice());
// expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
```

Синтаксис
```
arr.slice([begin[, end]])
```

Параметры
```
begin //Необязательный
Индекс (счёт начинается с нуля), по которому начинать извлечение.

Если индекс отрицательный, begin указывает смещение от конца последовательности. Вызов slice(-2) извлечёт два последних элемента последовательности.

Если begin не определён, slice() начинает работать с индекса 0.

Если begin больше длины последовательности вернётся пустой массив.
```

```
end //Необязательный
Индекс (счёт начинается с нуля), по которому заканчивать извлечение. Метод slice() извлекает элементы с индексом меньше end.

Вызов slice(1, 4) извлечёт элементы со второго по четвёртый (элементы по индексам 1, 2 и 3).

Если индекс отрицательный, end указывает смещение от конца последовательности. Вызов slice(2, -1) извлечёт из последовательности элементы начиная с третьего элемента с начала и заканчивая вторым с конца.

Если end опущен, slice() извлекает все элементы до конца последовательности (arr.length).
```

Возвращаемое значение
Новый массив, содержащий извлечённые элементы.

Описание

Метод `slice()` не изменяет исходный массив, а возвращает новую «одноуровневую» копию, содержащую копии элементов, вырезанных из исходного массива. Элементы исходного массива копируются в новый массив по следующим правилам:

-   Ссылки на объекты (но не фактические объекты): метод `slice()` копирует ссылки на объекты в новый массив. И оригинал, и новый массив ссылаются на один и тот же объект. То есть, если объект по ссылке будет изменён, изменения будут видны и в новом, и в исходном массивах.
-   Строки и числа (но не объекты [`String`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String) и [`Number`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Number)): метод `slice()` копирует значения строк и чисел в новый массив. Изменения строки или числа в одном массиве никак не затрагивает другой.

Если к любому массиву будет добавлен новый элемент, это никак не повлияет на другой массив.

Примеры

Пример: возврат части существующего массива

```
// Пример: наши хорошие друзья цитрусовые среди фруктов
var fruits = ['Банан', 'Апельсин', 'Лимон', 'Яблоко', 'Манго'];
var citrus = fruits.slice(1, 3);

// citrus содержит ['Апельсин', 'Лимон']
```

Пример: использование метода slice()

В следующем примере метод `slice()` создаёт новый массив, `newCar`, из массива `myCar`. Оба содержат ссылку на объект `myHonda`. Когда цвет в объекте `myHonda` изменяется на багровый, оба массива замечают это изменение.
```
// Используя slice, создаём newCar из myCar.
var myHonda = { color: 'красный', wheels: 4, engine: { cylinders: 4, size: 2.2 } };
var myCar = [myHonda, 2, 'в хорошем состоянии', 'приобретена в 1997'];
var newCar = myCar.slice(0, 2);

// Отображаем значения myCar, newCar и цвет myHonda
//  по ссылкам из обоих массивов.
console.log('myCar = ' + myCar.toSource());
console.log('newCar = ' + newCar.toSource());
console.log('myCar[0].color = ' + myCar[0].color);
console.log('newCar[0].color = ' + newCar[0].color);

// Изменяем цвет myHonda.
myHonda.color = 'багровый';
console.log('Новый цвет моей Honda - ' + myHonda.color);

// Отображаем цвет myHonda по ссылкам из обоих массивов.
console.log('myCar[0].color = ' + myCar[0].color);
console.log('newCar[0].color = ' + newCar[0].color);
```

Этот скрипт выведет:
```
myCar = [{color:'красный', wheels:4, engine:{cylinders:4, size:2.2}}, 2,
         'в хорошем состоянии', 'приобретена в 1997']
newCar = [{color:'красный', wheels:4, engine:{cylinders:4, size:2.2}}, 2]
myCar[0].color = красный
newCar[0].color = красный
Новый цвет моей Honda - багровый
myCar[0].color = багровый
newCar[0].color = багровый
```

Массивоподобные объекты

Метод `slice()` также может использоваться для преобразования массивоподобных объектов / коллекций в новый массив `Array`. Вам просто нужно привязать метод к объекту. Псевдомассив [`arguments` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments "Currently only available in English (US)") внутри функции как раз является примером «массивоподобного объекта».
```
function list() {
  return Array.prototype.slice.call(arguments, 0);
}

var list1 = list(1, 2, 3); // [1, 2, 3]
```

Привязка может быть осуществлена посредством функции `call()` из прототипа функции [`Function.prototype` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/prototype "Currently only available in English (US)"), также запись может быть сокращена до `[].slice.call(arguments)` вместо использования `Array.prototype.slice.call()`. В любом случае, она может быть упрощена посредством использования функции [`bind()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/bind).

```
var unboundSlice = Array.prototype.slice;
var slice = Function.prototype.call.bind(unboundSlice);

function list() {
  return slice(arguments, 0);
}

var list1 = list(1, 2, 3); // [1, 2, 3]
```

#Arrayprototype