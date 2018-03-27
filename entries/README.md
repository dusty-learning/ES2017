# Object.entries

`Object.entries` is a new method built into the Object type it's purpose is to create an arrays of arrays with the key value pairing.

## Syntax

The syntax is essentially the same as `Object.keys` and `Object.values`.

```js
Object.entries(obj);
```

## Usage

`Object.keys` has been around since ES5 (It was given some improvements with the release of ES6 however) which gave back the keys of an object but not the values.

Here is an example comparing the two:

```js
const obj = { a: 1, b: 2, c: 3 };

Object.keys(obj); // => ['a', 'b', 'c']

Object.entries(obj); // => [['a', 1], ['b', 2], ['c', 3]]
```

A fitting use case for this method could be taking advantage of the array mapping, or making the object (which is not an iterable) into an array (Which is an iterable).

```js
Object.entries({ a: 1, b: 2, c: 3 }).map(([key, val]) => console.log(`key: ${key} value: ${val}.`));
// => key: a value: 1.
// => key: b value: 2.
// => key: c value: 3.
```

That's all there is to using and understanding the new `Object.entries` from ES2017.

## Browser Support

| Browser       | Support       | Vers  |
| ------------- |:-------------:| -----:|
| Chrome        | Yes           | 54+   |
| Firefox       | Yes           | 47+   |
| Edge          | Yes           | NA    |
| IE            | No            | NA    |
| Safari        | Yes           | 10.1+ |
| Opera         | Yes           | 41+   |
