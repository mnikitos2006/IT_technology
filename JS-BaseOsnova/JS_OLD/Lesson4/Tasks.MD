## Задача 1.

Проверить как отрабатывает приведение типов

true + false,
12 / "6",
"number" + 15 + 3,
15 + 3 + "number",
[1] > null,
"foo" + + "bar",
'true' == true,
false == 'false',
null == '',
!!"false" == !!"true",
[‘x’] == ‘x’,
[] + null + 1,
0 || "0" && {},
[1,2,3] == [1,2,3],
{}+[]+{}+[1],
!+[]+[]+![],
new Date(0) - 0,
new Date(0) + 0,

## Задача 2.

Написать программу, которая принимает три аргумента: два элемента для сравнения и знак сравнения.
Если пользователь ввел строки, то сравнивать как строки, если ввел числа, то сравнивать как числа. Если ввел один
аргумент число, а второй аргумент строку, выдать сообщение о том что не корректно сравнивать строку с числом. Написать
тесты. Обработать такие значения как null, undefined.

console.log(example(2,4,"<"))
true
##

console.log(example("Kit","Kot,"<"))
false

