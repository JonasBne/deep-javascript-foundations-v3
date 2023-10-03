# Abstract operations

The ECMAScript language implictly performs automatic type conversion as needed.

## Types of abstract operations

`toPrimitive`

In JavaScript functions belong to the object types. Objects can be converted into primitive types with the help of `[Symbol.toPrimitive](hint)`. Based on the hint that's passed to the `toPrimitive` method, the object is converted into a primitive type.


```js
const obj = {
  [Symbol.toPrimitive](hint) {
    switch (hint) {
      case 'string':
        return 'hello world';
      case 'number':
        return 30;
      default:
        return 'default return';
    }
  },
};

console.log(+obj); // 10        — hint is "number"
console.log(`${obj}`); // "hello"   — hint is "string"
console.log(obj + ''); // "true"    — hint is "default"
```

`toString`

It converts primitive types and object types to string primitive values.

```js
null // "null"
undefined // "undefined"
true // "true"
false // "false"
(1) // "1"
(1.1) // "1.1"
-0 // "0" --> Notice that the - character is no longer present
```

When you're trying to perform a toString method on `object types`, what really happens is the `toPrimitive` method is called with the hint set to `string`.

This mean it will first take `toString()` and if that is not present it will take `valueOf()`.

```js
[] // "" --> the brackets are no longer present
[null, undefined] // "," --> when you call toString directly on null or undefined, they are turned into the literal string, but when they're part of an array they are no longer presented as strings. But they are still there in terms of positioning (there is a comma in between them)
({}) // "[object Object]" --> notice that square brackets are now in here
({ a: 1 }) // "[object Object]"
({ toString: () => 'X' }) // "X"
```

`toNumber`

It converts primitive types and object types to number primitive values.

```js
"" // 0
"0" // 0
"1.1" // 1.1
false // 0
true // 1
null // 0
undefined // NaN --> remarkable that undefined becomes Na but null becomes 0
```

When you're trying to perform a toString method on `object types`, what really happens is the `toPrimitive` method is called with the hint set to `number`.

This means it will take `valueOf()` and if that is not present it will take `toString()`.

```js
[""] // 0 --> because an empty string becomes 0
["0"] // 0
["-0"] // 0
[null] // 0
[undefined] // 0
[1,2,3] // NaN
[[[[]]]] 0
```

`toBoolean`

The `toBoolean` methods differs from `toString` and `toNumber` because it does **not perform any coercion**. Instead, it just does a lookup in the list of `falsy values`:

- ""
- 0, -0
- null
- NaN
- false
- undefined

Be aware that `if it is not a falsy value, it is always truthy`!

So for example:

```js
[] // will output truthy because [] is not part of the falsy list
```