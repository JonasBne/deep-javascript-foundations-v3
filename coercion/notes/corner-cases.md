# Corner cases

There are two particular corner cases that are worth mentioning.

## Empty string

```js
let a = '';
console.log(Number(a)); // 0

let a = '  \t\n';
console.log(Number(a)); // 0 --> all whitespace is stripped away from the string so it becomes and empty string
// and hence becomes 0
```

## Boolean values

```js
Number(true) // 1
Number(false) // 0
```

This has quite some unexpected side-effects:

```js
1 < 2 // true

1 < 2 < 3 // true --> this is a positive false result because it happens by accident! 
// it is evaluated as follows
(1 < 2) < 3
true < 3
1 < 3 // since true is coerced to 1 
```

```js
3 > 2 // true

3 > 2 > 1 // false
(3 > 2) > 1
true > 1
1 > 1 // false!
```