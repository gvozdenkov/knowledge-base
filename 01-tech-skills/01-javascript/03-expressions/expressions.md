# Expressions / Выражения

Выражение - конструкция языка, которая позволяет результат выполнения этой конструкции передать в другую конструкцию. А другая конструкция, которая является выражением поверх этого выражения может взять этот результат и с ним делать что-то дальше.

`( )` - скобки похожи на скобки в математике. Они группируют части выражения, чтобы определить части выражения и порядок их выполнения.

```js
10 + 5 + 3;
```

1. Выполняется выражение `10 + 5 => res`
2. Результат передаётся в выражение `res + 3`

## Суть выражения

```js
'string'[0]; // 's'
```

Кажется, что в этом примере мы просто определили индекс символа, который хотим получить.

На самом деле эта строка представляет из себя 3 выражения js:

1. 'string' - строковый литерал
2. 2
3. [2]
4. ; - empty statment
5. 'string'[0];

Почему такое поведение при `+`?

```js
false + 1; // 1
false + '1'; // 'false1'
+false + '1'; // '01' -  сначала false приводится к числу, затем конкатенация строк
![]; // false
!![]; // true
+[]; // 0
![] + []; // 'false'
1 + []; // '1'
1 + [1]; // '11'
```

Перед сложением числа с объектом, сначала будет вызван метод `valueOf()`, затем `toString()` у объекта

```js
[].valueOf().toString(); // ''
```