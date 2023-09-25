# Primitive types

# What are the primitive types?

The list of primitive types in JavaScript
- undefined
- string
- number
- boolean
- symbol
- bigint
- null

# The `typeof` operator

The `typeof` operator **always returns a string** that tells you the type.

```js
// incorrect usage
typeof myVariable === undefined 

// correct usage
typeof myVariable === 'undefined'
```

Caveats to watch out for:

```js
const v = null
typeof v // returns "object"!
```

```js
const v = function() {}
typeof v // returns "function" (altough functions are not officially considered a 'type' at the top level)
```

```js
const v = [1,2,3]
typeof v // returns "object"
```

# NaN & isNaN

A better mental model for `NaN` is not `is not a number` but rather it means that is a `invalid number`.

Bear in mind that `NaN` is the only value in JavaScript that is not equal to itself.

```js
const myAge = Number('0o46') // 38
myAge === myAge // false
```

How do we check if a value is `NaN`? We can use the `isNaN` function.

**Imporant**: `isNaN` coerces it's input into a number before checking to see if it's `NaN`. This means that `isNaN` will return `true` for any value that can't be coerced into a number.

```js  
isNaN(myAge) // false
```

If you want to avoid the coercion, you can use the `Number.isNaN` function.

```js
Number.isNaN(myAge) // false
```