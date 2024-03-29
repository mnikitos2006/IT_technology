 https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String
# Массивы

Для хранения упорядоченных коллекций существует особая структура данных, которая называется массив, Array

Существует два варианта синтаксиса для создания пустого массива:

```js
let arr = new Array();
let arr = [];
```

Элементы массива нумеруются, начиная с нуля.

Мы можем получить элемент, указав его номер в квадратных скобках:

```js
let fruits = ["Яблоко", "Апельсин", "Слива"];

alert(fruits[0]); // Яблоко
alert(fruits[1]); // Апельсин
alert(fruits[2]); // Слива

```

Замена элемента

```js
let fruits = ["Яблоко", "Апельсин", "Слива"];

fruits[2] = 'Груша'; // теперь ["Яблоко", "Апельсин", "Груша"]
```

Добавление элементы:

```js
let fruits = ["Яблоко", "Апельсин", "Слива"];

fruits[3] = 'Лимон'; // теперь ["Яблоко", "Апельсин", "Груша", "Лимон"]
```

Общее число элементов массива содержится в его свойстве length:

```js
let fruits = ["Яблоко", "Апельсин", "Слива"];

alert(fruits.length); // 3
```

В массиве могут храниться элементы любого типа.

```js
// разные типы значений
let arr = ['Яблоко', {name: 'Джон'}, true, function () {
    alert('привет');
}];

// получить элемент с индексом 1 (объект) и затем показать его свойство
alert(arr[1].name); // Джон

// получить элемент с индексом 3 (функция) и выполнить её
arr[3](); // привет

```

Получение последних элементов при помощи «at»

```js
let fruits = ["Apple", "Orange", "Plum"];
alert(fruits[fruits.length - 1]); // Plum

let fruits = ["Apple", "Orange", "Plum"];
// то же самое, что и fruits[fruits.length-1]
alert(fruits.at(-1)); // Plum
```

## Методы pop/push, shift/unshift

Очередь – один из самых распространённых вариантов применения массива. В области компьютерных наук так называется
упорядоченная коллекция элементов, поддерживающая два вида операций:

- `push` добавляет элемент в конец.
- `shift` удаляет элемент в начале, сдвигая очередь, так что второй элемент становится первым.
  Массивы поддерживают обе операции.

На практике необходимость в этом возникает очень часто. Например, очередь сообщений, которые надо показать на экране.

Существует и другой вариант применения для массивов – структура данных, называемая стек.

Она поддерживает два вида операций:

- `push` добавляет элемент в конец.
- `pop` удаляет последний элемент.
  Таким образом, новые элементы всегда добавляются или удаляются из «конца».

Примером стека обычно служит колода карт: новые карты кладутся наверх и берутся тоже сверху:

Массивы в JavaScript могут работать и как очередь, и как стек. Мы можем добавлять/удалять элементы как в начало, так и в
конец массива.

В компьютерных науках структура данных, делающая это возможным, называется двусторонняя очередь.

Методы, работающие с концом массива:

- `pop`

Удаляет последний элемент из массива и возвращает его:

```js
let fruits = ["Яблоко", "Апельсин", "Груша"];

alert(fruits.pop()); // удаляем "Груша" и выводим его

alert(fruits); // Яблоко, Апельсин
```

И fruits.pop() и fruits.at(-1) возвращают последний элемент массива, но fruits.pop() также изменяет массив, удаляя его.

- `push`
  Добавляет элемент в конец массива:

```js
let fruits = ["Яблоко", "Апельсин"];

fruits.push("Груша");

alert(fruits); // Яблоко, Апельсин, Груша
```

Вызов fruits.push(...) равнозначен fruits[fruits.length] = ....

Методы, работающие с началом массива:

- `shift`
  Удаляет из массива первый элемент и возвращает его:

```js
let fruits = ["Яблоко", "Апельсин", "Груша"];

alert(fruits.shift()); // удаляем Яблоко и выводим его

alert(fruits); // Апельсин, Груша
```

Методы push и unshift могут добавлять сразу несколько элементов:

```js
let fruits = ["Яблоко"];

fruits.push("Апельсин", "Груша");
fruits.unshift("Ананас", "Лимон");

// ["Ананас", "Лимон", "Яблоко", "Апельсин", "Груша"]
alert(fruits);
```

### Внутреннее устройство массива

Массив – это особый подвид объектов. Квадратные скобки, используемые для того, чтобы получить доступ к свойству arr[0] –
это по сути обычный синтаксис доступа по ключу, как obj[key], где в роли obj у нас arr, а в качестве ключа – числовой
индекс.

Массивы расширяют объекты, так как предусматривают специальные методы для работы с упорядоченными коллекциями данных, а
также свойство length. Но в основе всё равно лежит объект.

Следует помнить, что в JavaScript существует 8 основных типов данных. Массив является объектом и, следовательно, ведёт
себя как объект.

### Эффективность

Метод pop не требует перемещения, потому что остальные элементы остаются с теми же индексами. Именно поэтому он
выполняется очень быстро.

Аналогично работает метод push.

### Перебор элементов

Одним из самых старых способов перебора элементов массива является цикл for по цифровым индексам:

```js
let arr = ["Яблоко", "Апельсин", "Груша"];

for (let i = 0; i < arr.length; i++) {
    alert(arr[i]);
}
```

Но для массивов возможен и другой вариант цикла, for..of:

```js


let fruits = ["Яблоко", "Апельсин", "Слива"];

// проходит по значениям
for (let fruit of fruits) {
    alert(fruit);
}
```

Цикл `for..of` не предоставляет доступа к номеру текущего элемента, только к его значению, но в большинстве случаев
этого
достаточно. А также это короче.

### Немного о «length»

Свойство length автоматически обновляется при изменении массива. Если быть точными, это не количество элементов массива,
а наибольший цифровой индекс плюс один.

Например, единственный элемент, имеющий большой индекс, даёт большую длину:

```js
let fruits = [];
fruits[123] = "Яблоко";

alert(fruits.length); // 124
```

Обратите внимание, что обычно мы не используем массивы таким образом.

Ещё один интересный факт о свойстве length – его можно перезаписать.

Если мы вручную увеличим его, ничего интересного не произойдёт. Зато, если мы уменьшим его, массив станет короче. Этот
процесс необратим, как мы можем понять из примера:
Ещё один интересный факт о свойстве length – его можно перезаписать.

Если мы вручную увеличим его, ничего интересного не произойдёт. Зато, если мы уменьшим его, массив станет короче. Этот
процесс необратим, как мы можем понять из примера:

```js
let arr = [1, 2, 3, 4, 5];

arr.length = 2; // укорачиваем до двух элементов
alert(arr); // [1, 2]

arr.length = 5; // возвращаем length как было
alert(arr[3]); // undefined: значения не восстановились
```

Таким образом, самый простой способ очистить массив – это arr.length = 0;.

### new Array()

Существует ещё один вариант синтаксиса для создания массива:

```js
let arr = new Array("Яблоко", "Груша", "и тд");
```

Он редко применяется, так как квадратные скобки [] короче. Кроме того, у него есть хитрая особенность.

Если new Array вызывается с одним аргументом, который представляет собой число, он создаёт массив без элементов, но с
заданной длиной.

### Не сравнивайте массивы при помощи ==

В JavaScript, в отличие от некоторых других языков программирования, массивы не следует сравнивать при помощи оператора
==.

У этого оператора нет специального подхода к массивам, он работает с ними, как и с любыми другими объектами.

Вместо этого сравните их поэлементам в цикле или используя методы итерации, описанные в следующей главе.