# Cases of coercion

## The addition operator

The addition operator performs string contactenation or numeric addition. 

**Be aware**: when one of the operands is a string, the addition operators performs a string concatenation.

```js
const age = 25;
const name = 'John';

console.log(`${name} is ${age} years old`); // age is implicitly coerced to a string
```

```js
const numA = 5;
const numB = "5"

console.log(numA+numB) // outputs "55"
```

```js
let a = "5";
console.log(a + 1) // outputs 51
```

```js
let a = "5";
console.log(+a + 1) // outputs 6 --> the + operator before the variable calls the toNumber abstract operation
```

## The ++ operator

```js
let a = '5';
console.log(a++); // outputs 5 --> it coerces the string to a number and returns the value before incrementing
```

```js
let a = '5'
console.log(+aa) // outputs 6 --> it coerces the string to a number and returns the value after incrementing
```

## The - operator

The `-` operator performs numeric subtraction. It doesn't exist for strings, which means it always coerces the input to a number via the
toNumber astract operation.

```js
let a = '5';
console.log(a - 1); // outputs 4
```

```js
let a = '5';
console.log(a--); // outputs 5 --> it coerces the string to a number and returns the value before decrementing
```

```js
let a = '5';
console.log(--a); // outputs 4 --> it coerces the string to a number and returns the value after decrementing
```

```js
let a = '5'
console.log(-a) // outputs -5 --> it coerces the string to a number and returns the negative value
```