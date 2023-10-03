# Primitive types (value types)

# What are the primitive types?

The list of primitive types in JavaScript
- undefined
- string
- number
- boolean
- symbol
- bigint
- null

A `primitive type` can be defined as: not an object and has no methods or properties. It is `immutable` and cannot be altered. It can also be referred to as `value type`.

# Auto-boxing in JavaScript

A primitive type has no methods, but they behave as if they do.

For example:

```js
const myString = 'hello world'
myString.includes('hello') // how can this work if a string is no object and doesn't have the property includes?
```

When properties are accessed on primitive types, JavaScript `auto-boxes` the value into a wrapper object and accesses the property on that object instead.

So what really happens is:

```js
// a new String object is created
new String(myString).prototype.includes('hello')
```

Therefore the following will not work:

```js
const myString = 'hello world'
myString.foo = 'bar'
```

Because `myString.foo = 'bar'` will not assign the propery `foo` to `myString`, but it will assign it to the wrapper object that was created by `new String(myString)`.

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