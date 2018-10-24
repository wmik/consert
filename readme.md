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
