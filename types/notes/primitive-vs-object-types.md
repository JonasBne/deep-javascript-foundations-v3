# Primitive vs. object types

## How do primitive types and object types differ?

Let's take a look at a primitive type:

```js
let x = 10;
let y = x;

x = 20;

console.log(x) // outputs 20
console.log(y) // outputs 10
```

When working with primitive types, the value is copied from one variable to another. The value is stored inside the variable. So when we change the value of `x`, `y` is not affected.

Now let's take a look at an object type:

```js
let x = { value: 10 };
let y = x;

x.value = 20;

console.log(x.value) // outputs 20
console.log(y.value) // outputs 20
```

An object is not stored inside a variable. It refers to an address in memory. When we copy an object from one variable to another, we are copying the address of the object. So when we change the value of `x`, `y` is also affected.

Another interesting example:

```js
let number = 10;

function increase(number) {
    number++;
}

increase(number);
console.log(number); // outputs 10
```

When we pass a primitive type to a function, we are passing a copy of the value. So when we change the value of `number` inside the function, the original value is not affected.

When you try to log `number` outside of the function, it will still output `10` because `number++` does not exist outside of the scope of the function.

But when working with objects, the behaviour is different. This is due to the fact that the function receives a reference to the object in memory.

```js
let number = { value: 10 };

function increase(number) {
    number++;
}

increase(number.value);
console.log(number.value); // outputs 11
```

## Conclusion

Primitive types are copied by their value, object types are copied by their reference.