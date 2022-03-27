# JavaScript (Интенсив).

`Работа с языком JavaScript + HTML + CSS + React.js`

## Contents

1. [Chapter I](#chapter-i)
2. [Chapter II](#chapter-ii) \
   2.1. [Типы данных](#типы-данных)
   2.2 [Объявление переменных и область видимости](#объявление-переменных-и-область-видимости)
3. [Chapter III](#chapter-iii) \
   3.1 [Объявление переменных и область видимости](#объявление-переменных-и-область-видимости) \
   3.2 [Функции](#Функции) \
   3.3 [Замыкания](#Замыкания) \
   3.4 [Всплытие](#Всплытие) \
   3.5 [Каррирование](#Каррирование) \
   3.6 [Рекурсия](#Рекурсия)
 4. [Chapter IIII](#chapter-iiii) \
   4.1 [Операторы сравнения](#Операторы-сравнения) \
   4.2 [Условные операторы ](#Условные-операторы ) \
   4.3 [Логические операторы](#Логические-операторы) \
   4.4 [Циклы](#Циклы) \
   4.5 [Методы массивов, строк и объектов](#Методы-массивов,-строк-и-объектов)
<br>

## Chapter I
<br>
JavaScript - мультипарадигменный язык программирования, который используют для написания frontend- и backend-частей сайтов, а также мобильных приложений.
Это язык программирования высокого уровня, то есть код на нем понятный и хорошо читается.
Во frontend-части сайтов язык используют для создания интерактива (анимаций, всплывающих форм, автозаполнения), так как он связан с HTML и CSS и может ими манипулировать

HTML - это язык разметки, который мы используем для визуального и смыслового структурирования нашего web контента, например, определяем параграфы, заголовки, таблицы данных, или вставляем изображения и видео на страницу.
CSS - это язык стилей с помощью которого мы придаём стиль отображения нашего HTML контента, например придаём цвет фону (background) и шрифту, придаём контенту многоколоночный вид.

Где применяется:
Клиентская часть веб—приложений (frontend).
Это интерфейс страницы, то есть всё, что видит пользователь: контент, кнопки, формы обратной связи, меню.
С помощью JS интерфейс реагирует на действия пользователя (клики мыши, нажатия клавиш), также язык отвечает за запоминание данных и автозаполнение форм.
Серверная часть веб—приложений (backend).

Серверный код пишут на платформе Node.js. На JS работают, например, запросы AJAX (asynchronous javascript and XML), которые отправляются на сервер в фоновом режиме,
без перезагрузки веб-страницы, и push-уведомления — всплывающие сообщения в браузере, которые реализуются с помощью технологии Comet.
Такие уведомления приходят со специального Comet-сервера, который постоянно поддерживает соединение с браузером. Как раз с помощью JavaScript устанавливается это соединение.

Мобильные приложения на Android, iOS, Windows Mobile — когда нужно кросс-платформенное приложение или адаптация веб-приложения,
а языков Kotlin (для Android) и Swift (для iOS) недостаточно, то используется JavaScript.

Подробнее о истории создания JS'a можете узнать в этой [статье](https://habr.com/ru/company/livetyping/blog/324196/)

## Chapter II

<br>

### Типы данных

<br>

_В JavaScript есть 8 основных типов_

`-` number для любых чисел: целочисленных или чисел с плавающей точкой; целочисленные значения ограничены диапазоном ±(2^53-1)

`-` bigint для целых чисел произвольной длинны

`-` string для строк. Строка может содержать ноль или больше символов, **нет отдельного символьного типа**

`-` boolean для true/false

`-` undefined для неприсвоенных значений – отдельный тип, имеющий одно значение undefined. (undefined в JavaScript можно получить при доступе к неинициализированным переменным, несуществующим свойствам объекта, несуществующим элементам массива, etc)

`-` null для неизвестных значений – отдельный тип, имеющий одно значение null (Null всегда задается явно, представляет собой намеренное отсутствие какого-либо значения )

`-` object для более сложных структур данных. Представляет из собя набор пар {ключ : значение}

`-` symbol для уникальных идентификаторов

<br/>


<br>

### Объявление переменных и область видимости

<br>

Переменную можно объявить тремя способами c помощью **ключевых слов** **var** **let** и **const**

```
var string = 'string';
let string1 = 'string1';
const string2 = 'string2';
```

<br>

**JavaScript является слабо типизированным или динамическим языком** Это значит, что вам не нужно определять тип переменной заранее. Тип определится автоматически во время выполнения программы. Также это значит, что вы можете использовать одну переменную для хранения данных различных типов:

```
var string = 'string; // тут мы объявили перемунную и присвоили ей значение типа string
string = 123; // тут мы переопределили значение на тип number
string = [1,2,3]; // тут переопределили значение на тип array
```

const - immutable, let-mutable, var-mutable
Переменные, объявленные с помощью ключевых слова const и let могут иметь блочную, функциональную или модульную область видимости, а переменные, объявленные с помощью ключевого слова var, не имеют блочной области видимости.

Блочная область видимости означает, что переменная будет доступна только в текущем блоке, в котором была объявлена (функция, блок if/else etc).

В данном примере описана функция, которая внутри создает переменную, присваивает ей значение 0 и возвращает ее. Если попробовать получить доступ к объявленной переменной вне ее блока (функции), то в консоли мы увидим undefined (компилятор дает нам понять, что в данная переменная в текущем месте непроинициализированна)

```
function example () {
  const count = 0;
  return count;
}

console.log(count)
```


### Функции

<br>

Функция в JavaScript специальный тип объектов, позволяющий формализовать средствами языка определённую логику поведения и обработки данных.

Как можно объявить функцию в JavaScript:

`-` Function constructor:
```
new Function ([arg1[, arg2[, ...argN]],] functionBody)
```
`-` Function declaration:
```
function name([param[, param,[..., param]]]) {
   [statements]
}
```
`-` Function expression:
```
const myFunc = function [name]([param1[, param2[, ..., paramN]]]) {
   statements
}
```
`-` Arrow function:
```
(param1, param2, …, paramN) => { statements }
(param1, param2, …, paramN) => expression
```
`-` Object Method:
```
const obj = {
  property( parameters… ) {},
  [property]( parameters… ) {},
};
```

Область видимости функций:
Переменные объявленные в функции не могут быть доступными где-нибудь вне этой функции, поэтому переменные (которые нужны именно для функции) объявляют только в scope функции.
При этом функция имеет доступ ко всем переменным и функциям, объявленным внутри её scope.

Анонимная функция (еще можно встретить такое название как лямбды) - функция без имени.
Может быть использована в момент объявления, можно присвоить переменной и много чего еще.
Анонимные функции очень часто используются для выполнения какого-то кода в коллбэках, где в целом не нужно создавать отдельную именную функцию под это действие.
Пример такой функции можно увидеть в разделе [Замыкания](#Замыкания)

Выражения стрелочных функций имеют более короткий синтаксис по сравнению с функциональными выражениями и лексически привязаны к значению this (но не привязаны к собственному this, arguments, super, или new.target(если вы не знаете что такое this и остальные слова в скобках, не стейсняйтесь гуглить)). Выражение стрелочных функций не позволяют задавать имя, поэтому стрелочные функции анонимны, если их ни к чему не присвоить.

```
const func = x => x * x;                  // краткий синтаксис,
                                        // неявно возвращает результат
const func = (x, y) => { return x + y; }; // блочный синтаксис,
                                        // явно возвращает результат
```

<br>

### Замыкания

<br>

JavaScript формируют так называемые замыкания. Замыкание — это комбинация функции и лексического окружения, в котором эта функция была объявлена.
Это окружение состоит из произвольного количества локальных переменных, которые были в области действия функции во время создания замыкания.
В примере ниже plusNumber — это ссылка на экземпляр функции plus, созданной в результате выполнения plusNumber.
Экземпляр функции plus в свою очередь сохраняет ссылку на своё лексическое окружение, в котором есть переменная number.
По этой причине, когда происходит вызов функции plusNumber, переменная number остаётся доступной для использования и сохранённое в ней значение цифры передаётся в функцию plus.


```
function plusNumber(x) {
  const number = x
  return function plus(y) {
    return number + y;
  };
};

var plus5 = plusNumber(5);
var plus10 = plusNumber(10);

console.log(plus5(3));  // 8
console.log(plus10(4)); // 1
```

<br>
### Всплытие

<br>

Этап создания - это этап, в котором JavaScript-движок вызвал функцию, но само ее выполнение еще не началось.
На этапе создания контекста JavaScript-движок находится на фазе компиляции (сборки), то есть он сначала просматривает и анализирует код этой функции для последующего его выполнения.


```
showText();
console.log(value);

var value = "Переменная value";

function showText() {
 console.log("Вызов функции showText()");
}
// "Вызов функции showText()"
// undefined
console.log(plus10(4)); // 1
```

Именно из-за формирования записи окружения и выделения памяти под переменные до выполнения кода к ним можно обращаться до их объявления в программе.
 Такое поведения называется “всплытие” или hoisting.
 К сожалению, в некоторых ресурсах всплытие описывают так, что объявление переменной или функции физически поднимается в начало вашего кода, хотя в действительности это не так.
 На самом же деле, объявления переменных остаются в коде на том же месте, где вы их объявили, только память под них выделяется с самого начала, еще до выполнения кода.

<br>


### Каррирование

<br>

Каррирование – продвинутая техника для работы с функциями. Она используется не только в JavaScript, но и в других языках.
Цель каррирования – это трансформация функций таким образом, чтобы они принимали аргументы не как f(a, b, c), а как f(a)(b)(c).

При вызове каррированной функции с передачей ей одного аргумента, она возвращает новую функцию, которая ожидает поступления следующего аргумента.
Новые функции, ожидающие следующего аргумента, возвращаются при каждом вызове каррированной функции — до тех пор, пока функция не получит все необходимые ей аргументы.
Ранее полученные аргументы, благодаря механизму замыканий, ждут того момента, когда функция получит всё, что ей нужно для выполнения вычислений.
После получения последнего аргумента функция выполняет вычисления и возвращает результат.


```
function curry(callback) { // curry(f) выполняет каррирование
  return function(arg1) {
    return function(arg2) {
      return callback(arg1, arg2);
    };
  };
}

// использование
function multiply(a, b) {
  return a * b;
}

const curriedMultiply = curry(multiply);

console.log( curriedMultiply(3)(4) ); // 12
```
<br>



### Рекурсия

<br>
Рекурсивной функцией называется функция, которая в теле вызывает сама себя.

Пример рекурсивной функции, которая суммирует числа от единицы до заданного:

```
function sum(number){
  if (number === 0) {
      return 0;
  } else {
      return number + sum(number -= 1)
  }
}
console.log(sum(4)); //10
```

<br>

## Chapter IIII

### Операторы сравнения

<br>

Многие операторы сравнения известны нам из математики.
Операторы сравнения сравнивают значения операндов и возвращают логическое значение – true или false в зависимости от результатов проверки.
В JavaScript они записываются так:

`-` Больше/меньше: a > b, a < b.
`-` Больше/меньше или равно: a >= b, a <= b.
`-` Равно: a == b. Обратите внимание, для сравнения используется двойной знак равенства ==. Один знак равенства a = b означал бы присваивание. '1' == 1 //true
`-` Строгое равно: a === b. Оператор строгого равенства проверяет равенство без приведения типов, в отличие от обычного, другими словами если a и b разных типов, то будет возвращено false
`-` Не равно. В математике обозначается символом ≠, но в JavaScript записывается как a != b.

<br>


### Условные операторы

<br>
Формы условных операторов в JavaScript:
*условный оператор if (с одной ветвью);

```
if (true) {
  console.log('yes')
}
```

`-` условный оператор if...else (с двумя ветвями);

```
if (false) {
  console.log('yes')
} else {
  console.log('no')
}
```
`-` условный оператор else if... (с несколькими ветвями);
`-` тернарный оператор (?:);
```
true ? console.log('yes') : console.log('no')
```

`-` Оператор нулевого слияния (??);
 Оператор нулевого слияния - это логический оператор, который возвращает значение правого операнда когда значение левого операнда равно null или undefined, в противном случае будет возвращено значение левого операнда.

 ```
  const number = 23
  const nullable = null
  const example1 = number ?? 0 // 23
  const example2 = nullable ?? 1024 // 1024
 ```

`-` оператор выбора switch.
```
switch('string') {
  case '1':
  //do smth
  break
  case 'string':
  //do smth
  break
  default:
}
```

### Логические операторы
<br>

`-` && - логическое "И";
`-` || - логическое "ИЛИ";
`-` ! - логическое "НЕ".
`-` ?? - оператор нулевого слияния(который возвращает значение правого операнда когда значение левого операнда равно null или undefined, в противном случае будет возвращено значение левого операнда.)

<br>
<br>

### Циклы

<br>

При написании кода, часто необходимо совершить однотипное действие несколько раз. Тогда нам на помощь приходят циклы.

`-` Цикл for - повторяет действия, пока не произойдёт какое-либо специальное событие завершения цикла

for ([начало]; [условие]; [шаг]) выражениe
```
for (let i = 0; i < 5; i++) {
  console.log(i + 'student');
}
```

`-` Цикл do...while - повторяется пока заданное условие истинно.
do
  выражениe
while (условие)
```
do {
  i += 1;
  console.log(i + 'student');
} while (i < 5);
```
<br>

`-` Цикл while - выполняет выражения пока условие истинно.
while (условие)
  выражения
  ```
let i = 0
while (i < 5); {
i += 1;
console.log(i + 'student');
}
```
<br>

`-` Цикл for...in - проходит по всем перечислимым свойствам объекта. JavaScript выполнит указанные выражения для каждого отдельного свойства.

for (variable in object) {
  выражениe
}
```
const obj = {
  firstName:'Vasya',
  lastName:'Cvetkov',
}

for (let key in obj) {
  console.log(obj[key])
}
```
<br>

`-` Цикл for...of создаёт цикл, проходящий по перечислимым объектам, вызывая на каждой итерации функцию с выражениями, которые надо выполнить для получения значения каждого отдельного свойства.
for (variable of object) {
  выражения
}
```
const obj = {
  firstName:'Vasya',
  lastName:'Cvetkov',
}

for (let key of obj) {
  console.log(obj[key])
}
```
<br>
У вас наверно возник вопрос: В чем же разница между циклами for...in и for...of ? Выясните это самостоятельно)

Управление циклом:
`-` Оператор break - завершает выполнение текущего цикла.
`-` Оператор continue - останавливает текущую итерацию цикла и запускает новую итерацию.
<br>

### Методы массивов, строк и объектов

Все значения в JavaScript, за исключением null и undefined, содержат набор вспомогательных функций и значений.
Такие функции называют «методами», а значения – «свойствами».

<br>
Пример вызова метода:

```
const string = 'STRING'
console.log(string.toLowerCase()); //string
```

Подробнее о разных методах, можно почитать в источниках ниже

Методы массивов:https://habr.com/ru/company/plarium/blog/483958
<br>
Методы строк: https://html5css.ru/js/js_string_methods.php
<br>
Методы объектов:https://www.8host.com/blog/metody-obektov-v-javascript

<br>
