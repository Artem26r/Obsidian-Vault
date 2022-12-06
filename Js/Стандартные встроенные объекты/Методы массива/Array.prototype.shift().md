Метод **`shift()`** удаляет **первый** элемент из массива и возвращает его значение. Этот метод изменяет длину массива.
**Мутирует**

```
arr.shift()
```

Метод `shift` удаляет элемент по нулевому индексу, сдвигает значения по последовательным индексам вниз, а затем возвращает удалённое значение. Если свойство [`length`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/length) массива равно 0, вернётся значение [`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Метод `shift` не является привязанным к типу; этот метод может быть [вызван](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/call) или [применён](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) к объектам, напоминающим массив. Объекты, не содержащие свойство `length`, отражающее последний элемент в серии последовательных числовых, начинающихся с нуля, свойств, могут повести себя неправильным образом.

Пример: удаление элемента из массива
Следующий код показывает массив `myFish` до и после удаления его первого элемента. Также он показывает удалённый элемент:

```
var myFish = ['ангел', 'клоун', 'мандарин', 'хирург'];

console.log('myFish до: ' + myFish);
//myFish до: ангел,клоун,мандарин,хирург

var shifted = myFish.shift();

console.log('myFish после: ' + myFish);
//myFish после: клоун,мандарин,хирург

console.log('Удалён этот элемент: ' + shifted);
//Удалён этот элемент: ангел
```

Вывод этого примера будет следующим:

```
myFish до: ангел,клоун,мандарин,хирург
myFish после: клоун,мандарин,хирург
Удалён этот элемент: ангел
```

#Arrayprototype