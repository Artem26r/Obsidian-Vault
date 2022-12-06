Метод **`find()`** возвращает **значение** первого найденного в массиве элемента, которое удовлетворяет условию переданному в callback функции. В противном случае возвращается [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Также смотрите метод [`findIndex()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex), который возвращает **индекс** найденного в массиве элемента вместо его значения.

Если вам нужно найти позицию элемента или наличие элемента в массиве, используйте [`Array.prototype.indexOf()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) или [`Array.prototype.includes()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) соответственно.

Синтаксис
```
arr.find(callback[, thisArg])
```

Параметры

```
callback
Функция, вызывающаяся для каждого значения в массиве
```

принимает три аргумента:
```
element
Текущий обрабатываемый элемент в массиве.
```

```
index
Индекс текущего обрабатываемого элемента в массиве.
```

```
array
Массив, по которому осуществляется проход.
```

```
thisArg //Необязательный параметр. 
Значение, используемое в качестве this при выполнении функции callback.
```

Возвращаемое значение
Значение элемента из массива, если элемент прошёл проверку, иначе undefined.

Описание
Метод `find` вызывает переданную функцию `callback` один раз для каждого элемента, присутствующего в массиве, до тех пор, пока она не вернёт `true`. Если такой элемент найден, метод `find` немедленно вернёт значение этого элемента. В противном случае, метод `find` вернёт [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined). До Firefox 34 функция `callback` не вызывалась для «дырок» в массивах ([bug 1058394](https://bugzilla.mozilla.org/show_bug.cgi?id=1058394)).

Функция `callback` вызывается с тремя аргументами: значением элемента, индексом элемента и массивом, по которому осуществляется проход.

Если в метод `find` был передан параметр `thisArg`, при вызове `callback` он будет использоваться в качестве значения `this`. В противном случае в качестве значения `this` будет использоваться значение [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Метод `find` не изменяет массив, для которого он был вызван.

Диапазон элементов, обрабатываемых методом `find`, устанавливается до первого вызова функции `callback`. Элементы, добавленные в массив после начала выполнения метода `find`, не будут посещены функцией `callback`. Если существующие, непосещение элементы массива изменяются функцией `callback`, их значения, переданные в функцию, будут значениями на тот момент времени когда метод `find` посетит их; удалённые элементы все ещё будут посещены.

Примеры

Пример: поиск простого числа в массиве
Следующий пример находит в массиве положительных чисел элемент, являющийся простым числом (либо возвращает undefined, если в массиве нет простых чисел).

```
function isPrime(element, index, array) {
  var start = 2;
  while (start <= Math.sqrt(element)) {
    if (element % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}

console.log([4, 6, 8, 12].find(isPrime)); // undefined, не найдено
console.log([4, 5, 8, 12].find(isPrime)); // 5
```

#Arrayprototype