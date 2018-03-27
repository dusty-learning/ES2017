# Async & Await

One of the most prominent features added with ES2017 is Async/Await which makes working with async functionality that much easier.

These guys work a LOT like [ES2015 Promises](https://github.com/dusty-learning/es6/tree/master/promises) which you can checkout in the es6 repo.

Why do they work so well with promises? Well simply because under the hood that's all Async/Await is this is syntax sugar for us.

## Async

Creates an asynchronous function. Async functions are essentially a cleaner way to work with async code in JavaScript. In order to understand what they are and how they work, you should make sure you also understand JavaScript [Promises](https://github.com/dusty-learning/es6/tree/master/promises).


### Variants

The following variantes of async functions exist, please make note of the keyword `async` everywhere.

- Async function declaration: `async function foo() {}`
- Async function expression: `const foo = async function() {};`
- Async arrow function expression: `const foo = async () => {};`
- Async method definitions: `let obj = { async foo() {} };`

### Async Functions Always Return a Promise

It is important to note this, since async/await work on the same level as promises, you can expect a promise to be returned with an `async` function.

Fulfilling the Promise of an `async` function:

```js
const myAsyncFunc = async () => {
  return 123;
};

myAsyncFunc().then(x => console.log(x)); // => 123
```

Rejecting the PRomise of an `async` function:

```js
const myAsyncFunc = async () => {
  throw new Error('Something went wrong!');
};

myAsyncFunc().catch(err => console.log(err)); // => Error: 'Something went wrong!'
```

Now it is important to also note this isn't the conventional way of handling an `async` function we will be diving into that with `await`.

I am going to introduce `await` now and then we will introduce the concept of using the two together.

## Await

It's easy to forget to use `await` when making an `async` function call. You can only use `await` within an `async` function

```js
const myAsyncFunc = async () => {
  const value = someOtherAsyncFunc(); // Missing the await keyword
}
```

In the above example `value` is set to a promise which isn't what you usually want in an async function

`await` can even make sense if an async function doesn’t return anything. Then its Promise is simply used as a signal for telling the caller that it is finished. For example:

```js
const myAsyncFunc = async () =>
  await someOtherAsyncFunc();

```

So this above example does a little combination of the two but let's delve more into using them together

## Using Async/Await Together

Let's jump right into some examples (Also take note that my await always lives within an async function)

Handling a single asynchronous result:

```js
const myAsyncFunc = async () => {
  const result = await someOtherAyncFunc();

  console.log(result);
};

// This is equivalent to:
const myAsyncFunc = () =>
  someOtherAsyncFunc()
    .then(result => console.log(result));
```

Handling multiple asynchronous results sequentially:

```js
const myAsyncFunc = async () => {
  const set1 = await someAsyncCall1();

  console.log(set1);

  const set2 = await someAsyncCall2();

  console.log(set2);
};

// This is equivalent to:
const myAsyncFunc = () =>
  someAsyncCall1()
    .then(set1 => {
      console.log(set1);

      return someAsyncCall2();
    })
    .then(set2 => console.log(set2));
```

Handling multiple asynchronous results in parallel:

```js
const myAsyncFunc = async () => {
  const [set1, set2] = await Promise.all([someAsyncCall1(), someAsyncCall2()]);

  console.log(set1, set2);
};

// This is equivalent to:
const myAsyncFunc = () =>
  Promise.all([someAsyncCall1(), someAsyncCall2()])
    .then(([set1, set2]) => console.log(set1, set2));
```

## Handling Errors

Handling errors with async/await is slightly different than promises.

We have to (sadly) revert back to our trusty old try/catch ways

For example:

```js
const myAsyncFunc = async () => {
  try {
    await someAsyncCall();
  } catch (err) {
    console.error(err);
  }
};

// This is equivalent to:
const myAsyncFunc = () =>
  someAsyncCall()
    .catch(err => console.error(err));
```

So sadly error handling is not as majestic as the rest...

## Browser Support

| Browser       | Support       | Vers  |
| ------------- |:-------------:| -----:|
| Chrome        | Yes           | 55+   |
| Firefox       | Yes           | 52+   |
| Edge          | Yes           | NA    |
| IE            | No            | NA    |
| Safari        | Yes           | 10.1+ |
| Opera         | Yes           | 42+   |
