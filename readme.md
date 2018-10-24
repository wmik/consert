# consert

This little script is designed to serve as an introduction to testing.

It is specifically targeted towards the beginner/novice however if you are a seasoned developer, feel free to follow along.

## Introduction

The task is simple.

In order to understand how testing works, you will attempt to build a miniature testing framework using vanilla javascript in your preferred environment.

We recommend using the browser console so you can follow along as you code for a more hands on experience.

Let's get started!

## Analysis & Design

The framework will use [`console.assert`](https://stackoverflow.com/a/17054137/8126654) as the core to run assertion tests.

Take a moment to think about how the framework will be used because that is the framework's `API`.

For simplicity, the framework will use the callback pattern illustrated below.
```js
test(description, callback);
```
This is a common pattern in a number of frameworks such as [ava]() where assertions happen within the callback function.
The description works like an `id` for tracking passing and failing tests.

For simplicity, the callback function will receive only one parameter - the assertion object which holds the `API`.

The `API` will closely resemble [ava]()'s hence a general idea of how the framework will work is illustrated below.

```js
test("it should do something", c => {
  c.is(expected, actual); // checks equality
  c.notEqual(expected, actual); // checks inequality
  c.true(condition); // checks condition
})
```

## Implementation

Nothing too complex. Only about [`22 LLOC`](https://en.wikipedia.org/wiki/Source_lines_of_code)
```js
var assert, // the object that will hold the api
message; // provides more context for failing tests

assert = {} // initialize empty object
// TODO: assert.is = is;
// TODO: assert.notEqual = notEqual;
// TODO: assert.true = truthy;

/**
  * Test
  * @param {any} description - Test description
  * @param {any} callback - Test function
*/
function test(description, callback) {
  callback(assert);
}
```

The function above runs the callback function which in turn runs the assertions within it hence executing the test.

Go ahead and implement the `is` feature that will be used to run simple equality checks as shown below *(comments not required)*.
```js
/**
  * Checks equality
  * @param {any} expected - Expected value
  * @param {any} actual - Actual value
*/
function is(expected, actual) {
  message = `Expected ${expeced} but received ${actual}`;
  console.assert(expected === actual, { message });
}

assert.is = is;
```

Simply put the function above compares the `actual` value to the `expected` value using `strict equality`. If the check `FAILS`, it will output the `message` provided.

Go ahead and test it.
```js
test("1 should equal 1", assert => {
  assert.is(1, 1); // pass
});

test("2 should equal 2", check => {
  check.is(2, "2"); // fail
});

test("true should be true", verify => {
  verify.is(true, true); // pass
});

test("false should be false", confirm => {
  confirm.is(false, true); // fail
});
```

As you can see the argument name doesn't matter. Use whatever works for you but aim for legibility and simplicity.
