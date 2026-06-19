## Создание массива через конструктор Array()

Конструктор `Array` позволяет создавать массивы несколькими способами.

```javascript
const arr1 = new Array();
const arr2 = new Array(5);
const arr3 = new Array(1, 2, 3, 4, 5);

console.log(arr1); // []
console.log(arr2); // [ <5 empty items> ]
console.log(arr3); // [1, 2, 3, 4, 5]
```

⚠️ Особенность:

```javascript
new Array(5);
```

Создает массив длиной 5 с пустыми слотами, а не массив `[5]`.

Чтобы создать массив с одним числом внутри:

```javascript
const arr = [5];
```

---

### Array.of()

Метод `Array.of()` устраняет неоднозначность конструктора.

```javascript
const arr = Array.of(5);

console.log(arr); // [5]
```

Несколько элементов:

```javascript
const numbers = Array.of(1, 2, 3, 4, 5);
```

---

### Array.from()

Создает массив из итерируемого объекта или псевдомассива.

Из строки:

```javascript
const chars = Array.from('JavaScript');

console.log(chars);
```

Результат:

```javascript
['J', 'a', 'v', 'a', 'S', 'c', 'r', 'i', 'p', 't']
```

Из Set:

```javascript
const unique = new Set([1, 2, 3]);

const arr = Array.from(unique);

console.log(arr);
```

Из NodeList:

```javascript
const divs = document.querySelectorAll('div');

const arr = Array.from(divs);
```

С функцией преобразования:

```javascript
const doubled = Array.from([1, 2, 3], x => x * 2);

console.log(doubled);
```

---

## Пустые слоты (Sparse Arrays)

JavaScript позволяет создавать разреженные массивы.

```javascript
const arr = [];

arr[10] = 'Hello';

console.log(arr);
console.log(arr.length);
```

Результат:

```javascript
[ <10 empty items>, 'Hello' ]
11
```

Между индексами 0 и 9 находятся пустые слоты.

Проверка:

```javascript
0 in arr; // false
10 in arr; // true
```

---

## Свойство length

Каждый массив имеет специальное свойство `length`.

```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

console.log(fruits.length);
```

Результат:

```javascript
3
```

---

### Увеличение длины

```javascript
const arr = [1, 2, 3];

arr.length = 10;

console.log(arr);
```

Результат:

```javascript
[1, 2, 3, <7 empty items>]
```

---

### Уменьшение длины

```javascript
const arr = [1, 2, 3, 4, 5];

arr.length = 2;

console.log(arr);
```

Результат:

```javascript
[1, 2]
```

Все элементы после второго будут удалены.

---

# 3. Доступ к элементам массива

По индексу:

```javascript
const colors = ['red', 'green', 'blue'];

console.log(colors[0]);
console.log(colors[1]);
console.log(colors[2]);
```

---

### Получение последнего элемента

Классический способ:

```javascript
const last = arr[arr.length - 1];
```

Современный способ:

```javascript
const last = arr.at(-1);
```

Пример:

```javascript
const numbers = [10, 20, 30];

console.log(numbers.at(-1));
```

---

### Получение предпоследнего элемента

```javascript
arr.at(-2);
```

---

# 4. Добавление элементов

## push()

Добавляет элемент в конец массива.

```javascript
const fruits = ['Apple'];

fruits.push('Banana');

console.log(fruits);
```

Результат:

```javascript
['Apple', 'Banana']
```

Несколько элементов:

```javascript
fruits.push('Orange', 'Kiwi');
```

---

## unshift()

Добавляет элементы в начало.

```javascript
const arr = [2, 3];

arr.unshift(1);

console.log(arr);
```

Результат:

```javascript
[1, 2, 3]
```

---

# 5. Удаление элементов

## pop()

Удаляет последний элемент.

```javascript
const arr = [1, 2, 3];

const removed = arr.pop();

console.log(removed);
console.log(arr);
```

---

## shift()

Удаляет первый элемент.

```javascript
const arr = [1, 2, 3];

const removed = arr.shift();

console.log(removed);
console.log(arr);
```

---

# 6. Поиск элементов

## indexOf()

Возвращает индекс найденного элемента.

```javascript
const arr = ['A', 'B', 'C'];

console.log(arr.indexOf('B'));
```

Результат:

```javascript
1
```

Если элемент отсутствует:

```javascript
-1
```

---

## lastIndexOf()

Поиск с конца массива.

```javascript
const arr = [1, 2, 3, 2];

console.log(arr.lastIndexOf(2));
```

---

## includes()

Проверка существования элемента.

```javascript
const arr = [1, 2, 3];

console.log(arr.includes(2));
```

Результат:

```javascript
true
```

---

# 7. Перебор массивов

## for

Классический цикл.

```javascript
const arr = [10, 20, 30];

for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

---

## for...of

Самый удобный способ.

```javascript
for (const item of arr) {
    console.log(item);
}
```

---

## forEach()

```javascript
arr.forEach(item => {
    console.log(item);
});
```

Также доступны индекс и массив:

```javascript
arr.forEach((item, index, array) => {
    console.log(item, index);
});
```

---

# 8. Трансформация массивов

## map()

Создает новый массив.

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
```

Результат:

```javascript
[2, 4, 6]
```

---

## filter()

Фильтрация элементов.

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const even = numbers.filter(num => num % 2 === 0);

console.log(even);
```

Результат:

```javascript
[2, 4, 6]
```

---

## reduce()

Самый мощный метод массивов.

Сумма элементов:

```javascript
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((acc, current) => {
    return acc + current;
}, 0);

console.log(sum);
```

---

Поиск максимального значения:

```javascript
const max = numbers.reduce((a, b) => {
    return Math.max(a, b);
});
```

---

Преобразование массива в объект:

```javascript
const users = [
    { id: 1, name: 'Alex' },
    { id: 2, name: 'John' }
];

const map = users.reduce((acc, user) => {
    acc[user.id] = user;
    return acc;
}, {});

console.log(map);
```

---

# 9. Проверка условий

## some()

Хотя бы один элемент соответствует условию.

```javascript
const numbers = [1, 2, 3];

const result = numbers.some(n => n > 2);

console.log(result);
```

---

## every()

Все элементы должны соответствовать условию.

```javascript
const result = numbers.every(n => n > 0);
```

---

# 10. Поиск объектов

## find()

Возвращает найденный объект.

```javascript
const users = [
    { id: 1, name: 'Alex' },
    { id: 2, name: 'John' }
];

const user = users.find(user => user.id === 2);

console.log(user);
```

---

## findIndex()

Возвращает индекс объекта.

```javascript
const index = users.findIndex(user => user.id === 2);
```

---

## findLast()

Поиск с конца массива.

```javascript
const result = users.findLast(user => user.active);
```

---

## findLastIndex()

Возвращает индекс найденного элемента с конца.

```javascript
const index = users.findLastIndex(user => user.active);
```

---

# 11. Изменение массива

## splice()

Универсальный инструмент.

Удаление:

```javascript
const arr = [1, 2, 3, 4];

arr.splice(1, 2);

console.log(arr);
```

Результат:

```javascript
[1, 4]
```

---

Вставка:

```javascript
arr.splice(1, 0, 'Hello');
```

---

Замена:

```javascript
arr.splice(1, 1, 'New');
```

---

# 12. Копирование массива

## slice()

Создает поверхностную копию.

```javascript
const arr = [1, 2, 3];

const copy = arr.slice();
```

---

Через spread оператор:

```javascript
const copy = [...arr];
```

---

Через Array.from()

```javascript
const copy = Array.from(arr);
```

---

# 13. Объединение массивов

## concat()

```javascript
const result = [1, 2].concat([3, 4]);
```

---

## Spread Operator

```javascript
const result = [...arr1, ...arr2];
```

---

# 14. Сортировка

## sort()

⚠️ По умолчанию сортирует как строки.

```javascript
[10, 2, 5].sort();
```

Результат:

```javascript
[10, 2, 5]
```

Неправильная числовая сортировка.

Правильно:

```javascript
[10, 2, 5].sort((a, b) => a - b);
```

Результат:

```javascript
[2, 5, 10]
```

По убыванию:

```javascript
[10, 2, 5].sort((a, b) => b - a);
```

---

# 15. Разворот массива

## reverse()

```javascript
const arr = [1, 2, 3];

arr.reverse();
```

---

Современный аналог без мутации:

```javascript
const reversed = arr.toReversed();
```

---

# 16. Новые методы ECMAScript 2023+

## toSorted()

Не изменяет исходный массив.

```javascript
const sorted = arr.toSorted((a, b) => a - b);
```

---

## toSpliced()

Немутирующая версия splice.

```javascript
const result = arr.toSpliced(1, 2);
```

---

## with()

Замена элемента без изменения оригинала.

```javascript
const arr = [1, 2, 3];

const newArr = arr.with(1, 100);

console.log(newArr);
```

Результат:

```javascript
[1, 100, 3]
```

---

# 17. Многомерные массивы

Двумерный массив:

```javascript
const matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
```

Получение элемента:

```javascript
matrix[1][2];
```

Результат:

```javascript
6
```

---

# 18. Flattening

## flat()

```javascript
const arr = [1, [2, 3], [4, 5]];

console.log(arr.flat());
```

---

Глубокое выравнивание:

```javascript
arr.flat(Infinity);
```

---

## flatMap()

```javascript
const result = [1, 2, 3]
    .flatMap(x => [x, x * 2]);
```

---

# 19. Производительность массивов

Самые быстрые операции:

✅ Доступ по индексу — O(1)

```javascript
arr[100];
```

✅ push() — O(1)

```javascript
arr.push(value);
```

Средняя сложность:

```javascript
splice()
sort()
```

Медленные операции:

```javascript
shift()
unshift()
```

Они требуют смещения всех элементов массива.

---

# 20. Лучшие практики

### Используйте const

```javascript
const users = [];
```

Массив можно изменять даже при `const`.

---

### Предпочитайте map/filter/reduce вместо ручных циклов

Плохо:

```javascript
const result = [];

for (let i = 0; i < arr.length; i++) {
    result.push(arr[i] * 2);
}
```

Хорошо:

```javascript
const result = arr.map(x => x * 2);
```

---

### Избегайте мутаций

Предпочитайте:

```javascript
toSorted()
toReversed()
toSpliced()
with()
```

Вместо:

```javascript
sort()
reverse()
splice()
```

---

# Заключение

Массивы — одна из фундаментальных структур данных JavaScript. Практически любое приложение, будь то React, Node.js, Express, Vue, Angular, Next.js или чистый JavaScript, активно использует массивы для хранения и обработки данных.

Глубокое понимание методов массивов (`map`, `filter`, `reduce`, `find`, `some`, `every`, `flatMap`, `sort`, `splice` и других) позволяет писать более чистый, производительный и поддерживаемый код, а знание современных немутирующих методов ECMAScript делает код безопаснее и предсказуемее.
