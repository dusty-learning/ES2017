# Object.values

This is another method that has been added onto the `Object` as a method.

It's primary purpose being to do the same exact thing as `Object.keys` only in this case it gets the values of the object instead of the keys.

## Syntax

The syntax is essentially the same as `Object.keys` and `Object.entries`.

```js
Object.values(obj);
```

## Usage

Much like `Object.keys` and the other half for `Object.entries` it works pretty much the same.

```js
Object.values({ a: 1, b: 2, c: 3 }); // => [1, 2, 3]
```

## Browser Support

| Browser       | Support       | Vers  |
| ------------- |:-------------:| -----:|
| Chrome        | Yes           | 54+   |
| Firefox       | Yes           | 47+   |
| Edge          | Yes           | NA    |
| IE            | No            | NA    |
| Safari        | Yes           | 10.1+ |
| Opera         | Yes           | NA    |

