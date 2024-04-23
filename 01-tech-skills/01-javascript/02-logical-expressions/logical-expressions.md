# Logical expressions / && || ?? / Логические выражения

[Binary Logical Operators](https://262.ecma-international.org/14.0/?_gl=1*1o9qp6n*_ga*MTQyNDgwNTM3MC4xNzAyODE5MTM4*_ga_TDCK4DWEPP*MTcwMjk2MjYwOS4zLjAuMTcwMjk2MjYwOS4wLjAuMA..&_ga=2.178324580.1901384635.1702962610-1424805370.1702819138#sec-binary-logical-operators)

```js
(leftExpression) && (rightExpression)
(leftExpression) || (rightExpression)
(leftExpression) ?? (rightExpression)
```

:warning: Важная особенность логических выражений в том, что правое выражение не анализируется агентом до старта кода. Оно может быть сколь угодно сложным, но агент не будет его анализировать (только базовый синтаксис языка). После старта кода сначала вычисляется левое выражение. И если должно вернуться значение левого выражения, то правая часть даже не вычисляется:

```js
// notDefinedIdentifier нигде не определён в коде
var x = 'yo' || notDefinedIdentifier; // x = 'yo'
x = notDefinedIdentifier; // ReferenceError: notDefinedIdentifier is not defined
x = 'yo' && notDefinedIdentifier; // ReferenceError: notDefinedIdentifier is not defined
```

Отсюда важный вывод - логические выражения оптимизируют код

## Алгоритм

1. Вычислить `leftExpression`. Получить `leftVal` значение этого выражения
2. Выполнить [`ToBoolean(leftVal)`](https://262.ecma-international.org/14.0/?_gl=1*1o9qp6n*_ga*MTQyNDgwNTM3MC4xNzAyODE5MTM4*_ga_TDCK4DWEPP*MTcwMjk2MjYwOS4zLjAuMTcwMjk2MjYwOS4wLjAuMA..&_ga=2.178324580.1901384635.1702962610-1424805370.1702819138#sec-toboolean) - преобразовать в boolean по алгоритму:

Если `leftVal`:

- `boolean` - return `leftVal`
- `undefined`, `null`, `+0`, `-0`, `0`, `NaN`, `""` (пустая строка) - return `false`.
- Иначе return `true`

3. Вернуть результат выполнений `leftVal` или `rightVal` в зависимости от оператора.

## && - Логическое И

Если результат левого выражения приводится к `true` (через `ToBoolean`), то возвращается результат _правого_ выражения.

- Если `ToBoolean(leftVal)` === `false` -> return `leftVal`
- Иначе return `rightVal`

```js
4 && 5; // 5
0 && 5; // 0
true && 5; // 5
true && false; // false
false && false; // false
'' && 'hello'; // ''
var x = {} && 'yo'; // x = 'yo'
x = [].length && 'yo'; // x = 0
x = [1, 2, 3].length && 'yo'; // x = 'yo'
x = [1, 2, 3] && 'yo'; // x = 'yo'
```

## || - Логическое ИЛИ

Если результат левого выражения приводится к `true` (через `ToBoolean`), то возвращается результат _левого_ выражения. Правое выражение даже не вычисляется.

- Если `ToBoolean(leftVal)` === `true` -> return `leftVal`
- Иначе return `rightVal`

```js
4 || 5; // 4
0 || 5; // 5
true || 5; // true
true || false; // true
false || false; // false
'' || 'hello'; // 'hello'
var x = {} || 'yo'; // x = {}
x = [].length || 'yo'; // x = 'yo'
x = [1, 2, 3].length || 'yo'; // x = 3
x = [1, 2, 3] || 'yo'; // x = [1, 2, 3]
```

## ?? - Объединение выражений (нулевое слияние)

Удобно для присвоения значения по умолчанию.

```js
var condition = undefined;
var x = conditioin ?? 'defaul value'; // 'default value'
```

Если результат левого выражения равен `undefined` или `null` ( НЕ через `ToBoolean`), то возвращается результат _правого_ выражения. Иначе значение _левого выражения_

- `leftVal` === `undefined` или `null` -> return `rightVal`
- Иначе return `leftVal`

```js
4 ?? 5; // 4
0 ?? 5; // 0
true ?? 5; // true
true ?? false; // true
false ?? false; // false
'' ?? 'hello'; // ''
var x = {} ?? 'yo'; // x = {}
x = [].length ?? 'yo'; // x = 0
x = [1, 2, 3].length ?? 'yo'; // x = 3
x = [1, 2, 3] ?? 'yo'; // x = [1, 2, 3]
```
