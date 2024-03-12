# Array

В массиве все ключи приводятся к строке. Кроме Symbol.
[7.1.19 ToPropertyKey](https://262.ecma-international.org/14.0/?_gl=1*1o9qp6n*_ga*MTQyNDgwNTM3MC4xNzAyODE5MTM4*_ga_TDCK4DWEPP*MTcwMjk2MjYwOS4zLjAuMTcwMjk2MjYwOS4wLjAuMA..&_ga=2.178324580.1901384635.1702962610-1424805370.1702819138#sec-topropertykey)

```js
var arr = [];
arr[0] = 'A'; // ['A']

// но на самом деле 0 будет преобразован в строковый литерал
arr['0'] = 'B'; // ['B']

// и даже так
arr['000'] = 'C'; // ['B', 000: 'C']
```
