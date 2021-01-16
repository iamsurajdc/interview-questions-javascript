# Javascript Interview Questions

## Table of Contents

| Sl.No | Questions                                                                                                  |
| ----- | ---------------------------------------------------------------------------------------------------------- |
| 1.    | [What is Context in Javascript?](#what-is-context-in-javascript)                                           |
| 2.    | [What are Constructors in Javascript?](#what-are-constructors-in-javascript)                               |
| 3.    | [What is Call Apply and Bind?](#what-is-call-apply-and-bind)                                               |
| 4.    | [What is SetTimeout and ClearTimeout?](#what-is-settimeout-and-cleartimeout)                               |
| 5.    | [What are Prototypes in Javascript?](#what-are-prototypes-in-javascript)                                   |
| 6.    | [What is the difference between Proto and Prototype?](#what-is-the-difference-between-proto-and-prototype) |
| 7.    | [What is Prototype Inheritance Chain?](#what-is-prototype-inheritance-chain)                               |
| 8.    | [What is Synchronous and Asynchronous Code?](#what-is-synchronous-and-asynchronous-code)                   |
| 9.    | [What is an Event Loop?](#what-is-an-event-loop)                                                           |
| 10.   | [What is execution context in Javascript?](#what-is-execution-context-in-javascript)                       |

<br/>

1. ### What is Context in Javascript?

Context is nothing but the value of `this` keyword in javascript. The `this` keyword basically refers to the object that the function is executing in.

```js
var person = {
  name: "Aman",
  age: 25,
  hello: function(){
    console.log(this);
  }
}

person.hello();

{name: "Abhishek", age: 25, hello: [Function: hello]}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

2. ### What are Constructors in Javascript?

Constructors in Javascript are functions which are used to initialize a set of values or set default values for the objects.

```js
function Person(name, age, email) {
  this.name = name;
  this.age = age;
  this.email = email;
}

var myself = new Person("Abhishek", 25, "abc@gmail.com");
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

3. ### What is Call, Apply and Bind?

The Call, Apply and Bind methods are generally used to set the value of `this` keyword irrespective of the way in which a function is called.

`Call()`<br/>
The call method executes the function with a given <i>this</i> value with arguments provided individually.

```js
var obj1 = {
  num: 3,
};

var addTo = function (a, b, c) {
  return this.num + a + b + c;
};

console.log(addTo.call(obj1, a, b, c));
```

`Apply()`<br/>
The apply method is exactly the same as the call method in functionality. The only difference is that the arguments are provided in an array.

```js
var obj2 = {
  num: 3,
};
var addTo = function (a, b, c) {
  return this.num + a + b + c;
};

var arr = [8, 8, 9];

console.log(addTo.apply(obj2, arr));
```

`Bind()`<br/>
The bind method creates a new function that when called has it's <i>this</i> keyword set to the provided value.

```js
var obj3 = {
  num: 3,
};

var addTo = function (a, b, c) {
  return this.num + a + b + c;
};

var newFunc = addTo.bind(obj3);

console.log(newFunc(8, 8, 9));
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

4. ### What is SetTimeout and ClearTimeout?

`setTimeout()`<br/>
The SetTimeout function calls the function or evaluates the function after a specified number of milliseconds.

```js
setTimeout(function () {
  console.log("Hello World!");
}, 2000);

//Hello World! will get printed after 2 seconds (2000 milliseconds).
```

`clearTimeout()`<br/>
The clearTimeout function stops the execution of the function specified in the setTimeout.

```js
var func = setTimeout(function () {
  console.log("Hello World!");
}, 2000);

clearTimeout(func);

//Nothing will get printed in the above case.
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

5. ### What are Prototypes in Javascript?

Prototypes are the mechanism through which Javascript objects inherits properties and methods from one another. Whenever a function is created in Javascript, the JS Engine adds a prototype property to the function.

<ul>
<li>Array object inherits from Array.prototype</li>
<li> Date object inherits from Date.prototype</li>
<li> Person object inherits from Person.prototype</li>
</ul>

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

6. ### What is the difference between Proto and Prototype?

The main difference between the two is that `prototype` is a property of the constructor while `__proto__` is a property of the instance of that constructor.

```js
var arr = ["Abhishek", "Aman"];

arr.__proto__;
//[constructor: ƒ, concat: ƒ, copyWithin: ƒ, fill: ƒ, find: ƒ, …]

Array.prototype;
//[constructor: ƒ, concat: ƒ, copyWithin: ƒ, fill: ƒ, find: ƒ, …]
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

7. ### What is Prototype Inheritance Chain?

Every object in Javascript eventually inherits the properties and methods from `Object.prototype`. This is called the Prototype chain.
This is the reason why we say that almost everything in Javascript is an object.

```js
var arr = ["Abhishek", "Aman"];

arr.__proto__;
//[constructor: ƒ, concat: ƒ, copyWithin: ƒ, fill: ƒ, find: ƒ, …]

arr.__proto__.__proto__;
//{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}

arr.__proto__.__proto__.__proto__;
//null
```

In the above example we could see that the `arr` inherits its properties and methods from `Array` Constructor which in turn inherits its properties and methods from the `Object` Constructor which is then pointing to null. This is nothing but the Prototype Chain.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

8. ### What is Synchronous and Asynchronous Code?

A `synchronous` code is a code in which the statements of the code are executed in sequence. Each statement waits for the previous statement to finish before executing.

An `asynchronous` code is the one in which the next statement doesn't wait for the previous statement to finish executing.

`Synchronous`

```js
var a = 10;
function func() {
  console.log(a);
}
func();
```

<br/>

`Asynchronous`

```js
console.log("start");

setTimeout(function () {
  console.log("The wait time is 2 seconds");
}, 1000);

console.log("end");

// start
// end
// The wait time is 2 seconds
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

9. ### What is an Event Loop?

The `event loop` is the secret behind the Javascript asynchronous behaviour. The event loop is like an endless loop which keeps on checking whether there is something to be executed in the `call stack`. If the call stack is found to be empty, the `event queue` is checked. If there are some methods present in the event queue, then the methods are pushed one by one to the call stack where they are executed.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

10. ### What is Execution Context in Javascript?

Execution context refers to the environment in which the code is executed. It is the execution context only which decides which piece of code has access to objects, functions, variables etc.

The Execution context is divided into the following two

<ul>
<li>Global Execution Context</li>
<li>Functional Execution Context</li>
</ul>

`Global Execution Context`<br/>
Whenever your code runs for the very first time, it gets attached to the Global Context. There can only be <i>one</i> Global Execution Context in the entire process.

`Functional Execution Context`<br/>
Whenever the code is being executed and it encounters a function, then a functional execution context is created. There can be several functional Execution contexts depending on the number of functions.

![Screenshot](images/q10_execution_context.png)

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
