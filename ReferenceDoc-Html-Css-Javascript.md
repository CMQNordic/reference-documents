<h1 id="html-css-javascript">Reference Guide -  Html, Css & Javascript </h1>
<p align=right><a align=right href="https://github.com/CMQNordic/reference-documents#reference-documents">↩ main menu</a></p>

This is a reference document with usefull information about html, css and javascript.
Written while learning for educational purposes and for quick reference and look-up.
<br>
<br>
<p align=right>Written by Martin Czerwinski ®CMQ Nordic AB</p>

---
<p id="table-of-content"></p>

#### **TABLE OF CONTENT**
-   **JavaScript**
     [Vocabulary](#javascript-vocabulary) ◦ [Usefull funtions](#usefull-functions) ◦ [Examples/Typeof/Conditionals](#usefull-examples) ◦ [Arrays](#js-arrays) ◦ [C](#C) ◦ [C](#C) ◦ [C](#C) 
-   **CSS**  
    [Naming in CSS](#class-naming) ◦ [BEM](#bem-in-css) ◦ [Naming variations](#naming-variations) ◦ [CSS Selectors and specificity](#css-specificity)  
    [Flexbox](#flexbox) ◦ [Grid](#css-grid) ◦ [Floating](#floating) ◦ [Xxx](yyy) ◦ [Bootstrap](#bootstrap)  
    [Colors & shades](#colors-and-shades) ◦ [Centering things](#centering-things) ◦ [Float/Flex/Grid](#float-flex-grid)
-   [**HTML**](#html)  
     [Basics](#html-basics) ◦ [Document structure](#html-document-structure) ◦ [Building blocks](#html-page-building-blocks)

-   [**General**](#javascript)
-   [File structure](#file-structure) ◦ [Display and position](#display-and-position)

# [**Java Script**](#)

<p align="right"><a id="javascript-vocabulary" href="#table-of-content">↩ Back To Top</a></p>

#### **Basic JavaScript Vocabulary**
**Short about javascript**  

Low-level languages like C have manual memory management (_malloc()_, _free()_). In contrast **JavaScript** is a **high-level language** meaning that it automatically allocates memory when objects & variables are created, and automatically frees up memory when objects & variables aren't used anymore. Javascript is an **just-in-time compiled/interpreted** language, meaning that it is read and compiled to machine code just when it is executed in (by) browser. As it is a **multi paradigm** language, it can be used in many ways like procedural, functional or object oriented programming (OOB). A negative thing is that it is a **dynamically-typed language**  meaning that types aree not predefined. That might creates many error to be discoverd at run time only. Note that typescript that recently gains in popularity solves this problem. Javascript engine is single threaded with **event loop** catching events, callbacks and promisses (also called **microtasks**) and put back to main call stack in main execution thread. Web APIs like **timers**, **Fetch API**, **Geolocation API**, **DOM** and **Web Authentication** are not part of javascript (**ECMAScript**) specification but add-ons that broswers implement as Web APIs executed in seperate threads.


**Usefull javascript expressions and technologies to to be familiar with**   

`let a;` <-- **deklaration** of variable a (no value assigned)
`let a = 0;` <-- **definition** of variable a (value assigned)
`if () {...}`  <- if **statement** that is an action the program executes.
`3 + 4 `  <- **expression** that always a results in a value.
`let obj = {atr:0}` <- **definition** of an object with an **attribute** atr
`obj = { fnc: function() {...}}` <- **functions** defined in objects/classes are called **methods**
`function fnc(par) {...}`  <-- **function declaration** with a **parameter** (par) to be referenced inside the function.
`fnc = function(par) {..}`  <- **function expression** storing function reference in a variable.
`fnc = (par) => {}` <- **arrow function** declaration.
`add(3, 4);`  <--  The code inside a function is not executed when the function is **defined** but when it is **invoked/called/executed**. Here 3 and 4 are function **arguments** passed in when **invoking** the function.
`((par) => {...})(10)` <- **anonymous arrow funtion** can be invoked like this.
`(function (par) {...})(10)` <- **anonymous funtion** can also be invoked like this.

The fundamental  `differences of objects vs primitives` is that **objects** (_functions,arrays, objects, classes_) are stored on **heap** and copied by **`reference`**, whereas **`primitive`** values (_number, boolean, string, null and undefine_) are always copied by **`value`** and stored on **stack**.
   
`Promises` at creation moment get state **pending**. Later on a promise can be **setteled** eather by becoming **fulfilled** => resolve()/return called inside the promise, or **rejected** => reject()/throw is called inside the promise. 

Functions marked as `async` always automaticallly return an promise in state _pending_. If an `await` statement exists, then at that line** execution waits** for the settlement on the **nested promise**. In no 'await exist at all in a function marked as 'async' then returned value (or undefined in no return statement is defined) is resolved by default. As a rule **always** use await with async statements.

`Babel` is a plugin that **transpiles** (changes/converts) code written in modern javascript into ES5 code in order to ensure **browser backward compability**.

Javascript `runtime`  consists of:  
- **callstack** -> each functions own execution contexts to execute and primitive variables. Initially undefined, that during runtime get values
- **heap**  ->   objects are store here
- **event loop**  -> "main thread" controlling when events, callbacks, promises (microtasks) are returned back to call stack to be execited by maun thread. 

**Execution context** is environment in which a piece of code (i.e a function) is executed.

`Task queue` is a name of various queues (**event queue**, **callback queue**, **microtasks queue**) where events, callbacks, promises that were executed asynchronously in other threads are stored and await to be picked back to execute in call stack (main execution context). Those are picked back to the staxk by **event loop** but ONLY when main call stack **is empty**. Order is of getting tasks from task queues differ on type of que that event loop might handle diffrently (i.e  microtask-queue).

**Web APIs** (in browser environment but called **thread pools** in node.js) are functionality that is run asynchronously in own execution contexts within **seperate threads**. Those api's are not part of javascript specification but can be accessed though global **window** object in browser execution enviroment (not node). 

**Literals** are fixed values used to represent data. We do literally write the content of the variable in the variable definition. I.e. `'one line \n another line'` (string literal) or `['French', 'Colombian',]` (array literal) or `{a: 1}` (object literal)

<p align="right"><a id="usefull-functions" href="#table-of-content">↩ Back To Top</a></p>

### [Usefull functions](#)

|  |  |  |
| :-- | :-- | :-- |
| Math.floor(val) | truncates down 1.99 to 1| Math.floor(1.1) <br>// 1 |
| Math.random() | random 0 <-> 0.999| Math.floor(Math.random() * (20 - 5) + 5) <br> // between 5 and 20|
| console.dir(object) | list object stuctured with key/value on each row. Works in browser's console only. | console.dir(obj)|
| setTimeout(callback, milisec) | Calls callback function after a time. Note! Callback run in diffrent context and may execute after longer time than defined if main execution thread is busy. | setTimeout(()=>{...}, 3000) |
| fetch(url).then().then().catch() | Promise returning response data from an HTTP request. Run asynchronously. | return fetch(url)<br>.then(resp => resp.json())<br>.then(data => return data)<br>.catch(throw Error()) <br><br>  // returning data from an HTTP response |

<p align="right"><a id="usefull-examples" href="#table-of-content">↩ Back To Top</a></p>

### [Usefull examples](#)

```javascript
1 == '1'        // true
1 === '1'       // false

'1' != 1        // false
'1' !== 1       // true

&&              // logical AND
||              // logical OR

let a;                     
console.log(a);              // undefined
console.log(typeof a);       // undefined

let a = null;
console.log(a);              // null
console.log(typeof a);       // object (a bug)

null == undefined            // true
null === undefined           // false

Number.isInteger(1)          // true
Number.isInteger(1.5)        // false
Number.isInteger('')         // false
Number.isInteger('1')        // false
Number.isInteger(true)       // false

console.log(1 % 1);          // 0
console.log('1' % 1);        // 0
console.log('' % 1);         // 0
console.log(true % 1);       // 0
console.log(null % 1);       // 0
console.log('1.5' % 1);      // 0.5         
console.log('-1.5' % 1);     // -0.5         
console.log(1.5 % 1);        // 0.5 
console.log('-1.5' % 1);     // -0.5 
console.log(undefined % 1);  // NaN
console.log('hej' % 1);      // NaN
console.log({} % 1);         // NaN

console.log('22' + 2);       // 222  Note! + always turns other to string
console.log('22' - '2' - 2); // 18
console.log('22' / 2);       // 11
console.log('22' * 2);       // 44

let val = 1 + 1 + '2';       // 22
val -= 2;                    // 20

if (Array.isArray(val)) {
    // 100% val is array
}

if (val && typeof val === 'object' && !Array.isArray(val)) {
    // 100% val is object (not null, not array.. as those are objects too)
}

String(3)       // "3"
String(false)   // "false"
Number('23')    // 23
Number('hej')   // NaN
Boolean(null)   // false
Boolean('')     // false
Boolean('hej')  // true
Boolean({})     // true
```

### [Typeof](#)

```javascript
typeof undefined            // "undefined"   
typeof true                 // "boolean"
typeof 1                    // "number"
typeof 1.5                  // "number"
typeof NaN                  // "number"
typeof "1"                  // "string"
typeof `hej`                // "string"
typeof `${any expression}`  // "string"
typeof new String("1")      // "object"
typeof []                   // "object"
typeof {}                   // "object"
typeof null                 // "object"
typeof (()=>{})             // "function"
typeof String               // "function"
typeof Object               // "function"
typeof object               // "undefined"

```

### [Conditionals](#)
```javascript
// Stops only null/undefined.
// Most self explanatory and easy to understand but much writing.
if (val !== null && val !== undefined) {
    // Here NOT null or undefined. Everything else passes. 
    // Passes: 0, 1, '1', '', NaN, true, false, {}
}

// Stops only null/undefined.
// Popular and same as above but much shorter, but easy for misstake '!=='
if (val != null) {
    // Here NOT null or undefined. Everything else passes. 
    // Passes: 0, 1, '1', '', NaN, true, false, {}
}

// Popular, but easy for an error. Be carefull with "==" and do not use "===".
// Stops: Everything else except null/undefined
if (val == null) {
    // Here only null and undefined
}

// Used for boolean evaluation of to stop values that exist or not (falsy values). 
// Stops: false & falsy values (0, "", null, undefined, NaN). Note! Do not stop "0".
// Stops strings with no value (empty)
// Stops numbers without a value (0)
// Stops: Not set objects nor variables (null/undefined/NaN)
if (val) {
    // Here only true, 1, -1, "0", "str", [] or {}
}

// Stops everthing except a whole numbers. 
// Stops: 2.5, "2", "hej", true/false, NaN and {}
if (Number.isInteger(val)) { 
    // Here only whole integer numbers.
    // Passes: -2, 0, 12
}

// Stops everything except whole numbers or string as whole numbers. 
// Stops: 2.5, "2.5", "hej", true/false, NaN and {}
if (Number.isInteger(Number(String(val)))) { 
    // Here only whole numbers or string as whole numbers.
    // Passes: -2, "-2", 0, "0", 12, "12"
}

// Stops everything else except decimal numbers
// Stops: 0, 1, "1", "1.5", true/false, NaN and {}
if (typeof val === 'number' && Math.abs(val) % 1 != 0) { 
    // Here only decimal numbers.
    // Passes: 1.5, -2.5
}

// Stops everything  except decimal numbers or decimal numbers as string
// Stops: 0, 1, "1", "-2", null, true/false, NaN and {}
if (Math.abs(val) % 1 != 0) { 
    // Here only decimal numbers or strings as decimal numbers.
    // Passes: 1.5, "1.5", -2.5, "-2.5"
}

// This will assert when val is not an whole integer number only
// With babel and extension XXX, then console.log row is completely removed nad
// this asserts only in development and not in production.
!Number.isInteger(val) ?  console.log(null.val_is_not_whole_number) : ''

val == null ? console.log(null.val_is_null_or_undefined) : ''

typeof val != 'string' ?  console.log('null.val_is_not_a_string') : ''
```

<p align="right"><a id="js-arrays" href="#table-of-content">↩ Back To Top</a></p>

## [**Arrays**](#)

Some examples
```javascript
let cats = ['Bob', { name: 'Willy' }, 'Mini'];

a = cats.length;          // 3
a = cats[0];              // Bob
a = cats[0].name;         // undefined
a = cats[10].name;        // TypeError: Cannot read property 'name' of undefined
a = cats[1];              // Object
a = cats[1].name;         // Willy
a = cats[10];             // undefined

arr = [...Array(100).keys()] // 0,1,2...,99

```
### [Iterations](#)

```javascript
const arr = ['a', 'b']
console.log(arr.entires()) // return object {[0, 'a'], [1, 'b']} 

const obj = { 0: 'a', 1: 'b'}
console.log(Object.entries(obj)) // returns array [['0','a'], ['1', 'b']] Shallow copy

TODO 
iterate with forof and for in
```



```javascript
const arr = [100, 101, 102];

// for/of loop (preferred)
// Missing index, otherwise most robust without edge cases like for/in & forEach.
// Can exit with break;
for (const e of arr) {
   console.log(`Element = ${e}`);
}

// for/of (with index)
for (const [i, e] of arr.entries()) {
   console.log(`Element = ${e}, index = ${i}`);
}

// loop
// Can exit with break;
for (let i = 0, n = arr.length; i < n; i++) {
   console.log(`Index = ${i}`);
}

// forEach
// Good for chaining. Easy to write/understand.
// Handles holes in array badly, skips holes.
// Must use arrow func if 'this' is used
// Can not handle async/await functions
arr.forEach((e, i) => console.log(`Element = ${e}, index = ${i}`));

// for/in
// Do not use "for (let i in arr) {}"

```
#### Array operations

**push()** - Add last

```java
let cats = ['Bob'];
newLength = cats.push('Willy');

// Result: cats -> ['Bob', 'Willy'],  newLength -> 2 
// new element added with SHALLOW copy
// cats still refers to SAME object
```

**pop()** - Remove last

```java
let cats = ['Bob', 'Willy'];
removedItem = cats.pop();

// Result: 
// cats -> ['Bob'], removedItem -> 'Willy'
// cats still refers to SAME object
```

**unshift()** - Add first

```java
let cats = ['Bob'];
newLength = cats.unshift('Willy');  // ['Bob'].unshift('Willy')

// Result: 
// cats -> ['Willy', 'Bob'], newLength -> 2 
// new element added with SHALLOW copy
// cats still refers to SAME object
```

**shift()** - Remove first

```java
let cats = ['Willy', 'Bob'];
removedItem = cats.shift(); // ['Willy', 'Bob'].shift()

// Result: 
// cats -> ['Bob'], removedItem -> 'Willy'
// cats still refers to SAME object
```

**splice()** - Remove middle

```java
let cats = ['Bob', 'Alex', 'Willy', 'Anna', 'Mini'];
removedObj = cats.splice(1, 3); // start at index 1 and remove 3 elements

// Result: 
// cats -> ['Bob', 'Mini'], removedObj -> ['Alex', 'Willy', 'Anna']
// cats still refers to SAME object

```

**A.splice(0, A.length)** - empties an array **WITHOUT** changing its reference

```javascript
copyOfA = A.splice(0, A.length)

Removes all elements from A without changing A.
Returns NEW array with all removed but SHALLOW COPIED elements.

A =  [ { name: 'anna' }, { name: 'clas' } ]
let X = A[0]
let RefA = A

copyOfA = A.splice(0, A.length)

copyOfA === A -> false
RefA =>  []

X.name = 'changed' // oint to NEW copied array

copyOfA =>  [ { name: 'changed' }, { name: 'clas' } ]
```

**COPY** - shallow copis items from a to b **WITHOUT** changing array b reference

```javascript
let b = [];
let a = [{ str: 'a' }, { str: 'b' }, { str: 'c' }];

res = b.push(...a);
```

**ForEach/Map/Filter** - high ??? array functions

**Filter**

```javascript
filteredCopyOfA = A.filter((obj) => obj.id === id)

Creates a filtered SHALLOW COPY of A with items that returned true in the callback.
Does not filter nor change A at all.

a =  [ { str: 'anna' }, { str: 'anna' }, { str: 'aster' } ]

b = a.filter((obj) => obj.str === 'anna')

// b ->  [ { str: 'anna' }, { str: 'anna' } ]
// a === b --> false

a[0].str = 'ben';

// a -> [ { str: 'ben' }, { str: 'anna' }, { str: 'aster' } ]
// b -> [ { str: 'ben' }, { str: 'anna' } ]

array.forEach( elem => doSomething(elem) )
newArrayReturnes = array.map( elem => return doSomething(elem) )
sameArrayFiteredTrue = array.filter(elem => return soSomething(elem) : true : false)
```

## [**Objects and Functions**](#)

### **About objects**  

**Reference types** - Pointer to memory area. `Array`, `Function` and `Object`.  
**Primitive types** - - `String`, `Boolean`, `Number` ...

**SHALOW COPY** copies only primitive values.  
**DEEP COPY** copies both primitive and reference values.

**Note**! If there is a chance that values in original object might change after a copy and we do not this change to affect all other references all over the place in memory, then ALWAY do a deep copy (ie with use of lodash functions). Otherwise this can produce nasty hard to discover errors!

Each object have __proto__ property which is a pointer to its prototype object, kind of parent object.

To **add** new property on an object -> `obj.[new-prop-name] = value`
To **delete** a property on an object -> `delete object.[property name]`
Ta **add** new property to an prototype -> Use `Object.setPrototypeOf()` or `obj.prototype.[new-prop-name] = value`


### **About functions**
**Functions** are objects!

**Function declaration** -> `function add(b) {this.a + b}` _(`this` points to obj add)_
**Function expression** -> `const add = function(b) {thisa + b}`  _(`this` points to obj add)_
**Arrow function** -> `let add = (b) => this.a + b`  (`this` points to object that calls add!!!)

Note! Arrow function do not have own `this` in their execution context. This in arrow function **ALWAYS refers** to `this` in the calling parent!

 There are 2 important types of functions that we can **create an object** with: 
 **Constructor functions** - capitalized name, creating objects with the new keyword. All params are assigning to _this_ inside.
 **Factory function** - returning an newly created object
 
 Note! _Classes_ (came with ES6) is just syntetical sugar for creating objects with `constructor functions`!
  
  
### **Some examples**

```javascript

let person = {
  name: 'Rex',
  gender: 'man',
  age: 35,
  fnc1: function() { console.log('In reminder 1') }
  fnc2() { console.log('In reminder 2') }
}

s = 'name'

p = person['name'] // Rex
p = person.name // Rex
p = person[name] // CRASH
p= person.name.last; // CRASH
p = person[s] // Rex
p = person.age // 25
p = person[0] // undefined
p = person.nameXXX // undefined

p = person['fnc1']  // pointer to Function: reminder1
p = person.fnc1  // pointer to Function: reminder1

p(); // function executed -> In reminder 1
person.fnc2(); // function executed -> In reminder 2
person.func();  // CRASH

// Two variables, two distinct objects with the same properties
const fruitA = {name: 'apple'};
const fruitB = {name: 'apple'};

fruitA == fruitB; // return false
fruitA === fruitB; // return false
JSON.stringify(fruitA) == JSON.stringify(fruitB); // return true
```

```jsx
async function run(25) { .. }
const run = async (25) => { .. }
let run (a, b) => a + b + 100; // returns a + b + 100

(function () { console.log('here'); })(); // here

(val => console.log('here ', val))(2);  // here 2
```

**target = Object.assign(target, B, C)** - merge & shallow copy B & C into target

```java
A = Object.assign(Target, B, C)
// A === Target --> true

// Merges B & C objects into object Target and returns Target.
// Target reference unchanged - still point to same object. Performs merge with SHALLOW COPY.

// SHALOW COPY of A
shallowCopyOfA = Object.assign({}, A)
```

**target = lodash.merge(target, B, C)** - merge & deep copy B & C to target

```java
need external plugin -> require('lodash.merge');

A = merge(Target, B, C);
// A === Target -> true

// Merges B & C objects into object Target and returns Target.
// Target reference unchanged - still point to same object.  Performs merge with DEEP COPY.

// DEEP COPY of A
deepCopyOfA = merge({}, A)
```

**Target = {...A, ...B, ...C}** - merge A & B & C to new (SHALLOW copy)

```java
Target = {...A, ...B, ...C}

// Merges objects A & B & C into new object and returns it.
// Properties from right overwrites same properties to left.
// Does not change A, B nor C. Performs merge with SHALLOW COPY.

// SHALLOW COPY of A
shallowCopyOfA = {...A}
```

**JSON.parse(JSON.stringify(A))** - copy A to new object (DEEP copy)

```java
// DEEP COPY of A
deepCopyOfA = JSON.parse(JSON.stringify(A))
```

In practice, we often use ES2015 argument destructuring to simplify the code a bit (especially when we need to call commit multiple times):

```javascript
 increment(this) {
    this.commit('increment')
     this.commit('increment')
  }

 // with argument destructuring

 increment ({ commit }) {
    commit('incrementA')
    commit('incrementB')
    ...
  }
```

## [**Object destructing**](#)

Unpack values from arrays, or properties from objects, into distinct variables.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring

```
let a = 0;
let b = 0;
let obj = { a: 1, b: 2 };
[a, b] = [10, 20];

({ a, b } = obj);

```

## [**Proxy**](#)

```javascript
// Object to wrap in proxy to controll
const object = {
    gender: 'man',
    age: 35,
    name: 'Lee'
};

// Wrap object with proxy with handler without any traps
const personA = new Proxy(object, {});

personA.age = -35;
console.log(personA.name); // Lee
console.log(personA.age); // -35
console.log(personA.address); // undefined

const handler = {
    get: (object, property) => {
        return property in object ? object[property] : 'not found';
    },
    set: (object, property, value) => {
        if (property === 'age' && value < 0) {
            // throw new Error('age can not be negative');
            console.log('error: age can not be negative');
            return false;
        } else {
            object[property] = value;
            return true; // Indicate success
        }
    }
};

// Wrap object with proxy with handler with get/set traps
const personB = new Proxy(object, handler);

console.log(personB.name); // Lee
console.log(personB.age); // -35
console.log(personB.address); // not found

personB.age = 35;
console.log(personB.age); // 35
personB.age = -35; // console> error: age can not be negative
console.log(personB.age); // 35
```

## [**Guards**](#)

```javascript
// a can get any shape
let a = get()
if (a) {
    a -> 1+
    a -> 'a+'
    a -> {}
    a -> []
} else {
    a -> ''
    a -> 0
    a -> null
    a -> undefined
}


// we expect this object
let obj = {
    s: 'a'
};

// first guard if it changes to:
obj = null; //  null/undefined/false/0/''/NaN/Error

// first guard if it changes to:
obj = []; // {}/[]

if (obj && obj.s && obj.s.length) {
    // run only if there is ANY text s
    console.log('run');
} else {
    console.log('not run..');
}


r = generateObject()

if (r) {
    // run ONLY if r IS an object
}


```

## [**Promises and Async**](#)

Example:

```javascript
function getBooks(nbr) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve('a book ' + nbr);
        }, nbr);
    });
}

async function A() {
    console.log('startLoading A');
    let result = await getBooks(800);
    console.log('stop Loading A');
    return result;
}

function B() {
    console.log('start Loading B');
    return getBooks(1500).then((result) => {
        console.log('stop Loading B');
        return result;
    });
}

let resA = A().then((resA) => console.log(`A() result =`, resA));
console.log(`A() =>`, resA);

let resB = B().then((resB) => console.log(`B() result =`, resB));
console.log(`B() =>`, resB);

// Result
// start Loading A
// A() => Promise { <pending> }
// start Loading B
// B() => Promise { <pending> }
// srop Loading A
// A() result = a book 800
// stop Loading B
// B() result = a book 1500
```

A promise can be returned in chains. It is resolved or rejected by the original source then all childes that got the response can catch the result or error.

Problem when executing asyn function is that we nver know when they return. See example below where we want to execute three sets of test one after onother and in end write total number of run tests. Execution order is important.

```javascript
// Child A
functionA(url) // returnes promise
.then((fresult) => {
    // result -> 6 if sucess
    // result -> null if error
})


// Child B
functionA() {
    return FunctionB(url) // returns a promise
    .catch(() => {})
    .finally(() = {
        // Clean up
        // Do somthing when finished
    })
}

// Executor
functionB(url) {
    // Fetch returns promise and resolves it!
    return Fetch(url)
            .then((responseData) => {
                // Do something with responseData
                return 6; // this might me remaining to load
            })
            .catch((err) => {
                // Do something
                return null; // this might indicate error
            })
            .finally(() => {
                // Clean up
                // This will be called BEFORE this function returns!
                // DO NOT RETURN HERE
            })
}



```

```javascript
// This function is async and might take unexpected long time to return
function runAsyncTest(nbr) {
    setTimeout(() => {
        console.log(`[three] Running test ${nbr}`);
        return 1;
    }, 2000 - nbr * 500);
}


function runTestsOne() {
    [1, 2, 3].forEach((t) => console.log(`[one] Running test ${t}`));
    return 3;
}
function runTestsTwo() {
    [1, 2, 3].forEach((t) => console.log(`[two] Running test ${t}`));
    return 3;
}
function runTestsThree() {
    let ret = 0;
    ret += runAsyncTest(1);
    ret += runAsyncTest(2);
    ret += runAsyncTest(3);
    return ret;
}
function runTests() {
    let ret = 0;
    ret += runTestsOne();
    console.log('--> One returned. Tot is ', ret);
    ret += runTestsTwo();
    console.log('--> Two returned. Tot is ', ret);
    ret += runTestsThree();
    console.log('--> Three returned. Tot is ', ret);
    return ret;
}


function Execute() {
    let NbrOfTestsRun = runTests();
    console.log(`--> All tests run. Total number of run tests is = ${NbrOfTestsRun}`);
}

// Run tests
Execute();

// Result
[one] Running test 1
[one] Running test 2
[one] Running test 3
--> One returned. Tot is  3
[two] Running test 1
[two] Running test 2
[two] Running test 3
--> Two returned. Tot is  6
--> Three returned. Tot is  NaN
--> All tests run. Total number of run tests is = NaN
[three] Running test 3
[three] Running test 2
[three] Running test 1
```

Solution with promise and await/async

```javascript
function runAsyncTest(nbr) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log(`[three] Running test ${nbr}`);
            resolve(1);
        }, 2000 - nbr * 500);
    });
}

function runTestsOne() {
    [1, 2, 3].forEach((t) => console.log(`[one] Running test ${t}`));
    return 3;
}
function runTestsTwo() {
    [1, 2, 3].forEach((t) => console.log(`[two] Running test ${t}`));
    return 3;
}
async function runTestsThree() {
    let ret = 0;
    ret += await runAsyncTest(1);
    ret += await runAsyncTest(2);
    ret += await runAsyncTest(3);
    return ret;
}
async function runTests() {
    let ret = 0;
    ret += runTestsOne();
    console.log('--> One returned. Tot is ', ret);
    ret += runTestsTwo();
    console.log('--> Two returned. Tot is ', ret);
    ret += await runTestsThree();
    console.log('--> Three returned. Tot is ', ret);
    return ret;
}

async function Execute() {
    let NbrOfTestsRun = await runTests();
    console.log(`--> All tests run! Total number of run tests is ${NbrOfTestsRun}`);
}

// Run tests
Execute();

// Result
[one] Running test 1
[one] Running test 2
[one] Running test 3
--> One returned. Tot is  3
[two] Running test 1
[two] Running test 2
[two] Running test 3
--> Two returned. Tot is  6
[three] Running test 1
[three] Running test 2
[three] Running test 3
--> Three returned. Tot is  9
--> All tests run! Total number of run tests is 9
```

And more advanced solution wrapping the async function call.

```javascript
function runAsyncTest(nbr) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log(`[three] Running test ${nbr}`);
            resolve(1);
        }, 2000 - nbr * 500);
    });
}

function wrapAsyncTest(func) {
    console.log(`Starting to run an async test`);
    let ret = func();
    return ret;
}

function runTestsOne() {
    [1, 2, 3].forEach((t) => console.log(`[one] Running test ${t}`));
    return 3;
}
function runTestsTwo() {
    [1, 2, 3].forEach((t) => console.log(`[two] Running test ${t}`));
    return 3;
}
async function runTestsThree() {
    let ret = 0;
    ret += await wrapAsyncTest(async () => {
        return await runAsyncTest(1);
    });
    ret += await runAsyncTest(2);
    ret += await runAsyncTest(3);
    return ret;
}

async function runTests() {
    let ret = 0;
    ret += runTestsOne();
    console.log('--> One returned. Tot is ', ret);

    ret += runTestsTwo();
    console.log('--> Two returned. Tot is ', ret);

    ret += await runTestsThree();
    console.log('--> Three returned. Tot is ', ret);
    return ret;
}

function Execute() {
    runTests().then((NbrOfTestsRun) => {
        console.log(`--> All tests run! Total number of run tests is ${NbrOfTestsRun}`);
    });
}

// Run tests
Execute();

// Result
[one] Running test 1t is  6
[one] Running test 2sync test
[one] Running test 3 1
--> One returned. Tot is  3
[two] Running test 1
[two] Running test 2
[two] Running test 3
--> Two returned. Tot is  6
Starting to run an async test
[three] Running test 1
[three] Running test 2
[three] Running test 3
--> Three returned. Tot is  9
--> All tests run! Total number of run tests is 9
```

<br>

# [General](#)

<p align="right"><a id="file-structure" href="#table-of-content">↩ Back To Top</a></p>

## [**File structure**](#)

Example of file structure for a project that mixes html project with vue pr

```java
[root]

- configuration files // ony used by development tools (editor, compiler, extensions)
...
- dist // folder contaning build files ready to get published
src
  - assets  // contain everything we need to build up the page.
    + images  // production
      - logo.png
      ...
    + styles  // divided i global and modules
      - global
          - _colors.css // main theme colors used within the app here
          - _variables.css // variables independent of environment prod/dev
          - _mixins.css // postcss mixins like @media
          - global.css // all global. marked as global CSS in nuxt.config.js
          ...
      - modules
          - my-app-hero.css // specific to blocks add app prefix to ensure uniqueness
          - my-app-btn.css // _ means "partial file" -> to be imported in other files
          - modules.css  // all modules
          ...
      * styles.css // includes all styles from subfolders
    + scripts
      - modules
          - fileX
          ...
      * main.js  // main entry point javascript
    + vue
      - components
          - UI  // general UI elements
              - BaseButton.vue
              - BaseCard.vue
          - TheFooter.vue
          ChatWindow
            - ChatWindow.vue
          ...
      * App.vue  // main entry point Vue app (not needed it only component used)
  -

```


# [**CSS**](#)

<p id="class-naming"></p>

## [Naming in CSS](#)

To start with, read the blog from an authority in the web design industry Nicolas Gallagher on the topic of class names and CSS semantics - [here](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/).

Following is good to keep in mind:
> The most reusable components are those with class names that are **independent of the content**. We shouldn’t be afraid to include **additional HTML elements** if they help create more robust, flexible, and reusable components. Doing so does not make the HTML “unsemantic”, it just means that you use elements beyond the bare minimum needed to markup the content.
>
> The primary purpose of a class name is to be a hook for javascript and css.
>
> Class names should communicate **usefull additional information** to developers. The most reusable components are those with class names that are **independent of the content**.

```html
<!-- Example of BAD class name -->

<div class="news">
    <h2>News</h2>
    [news content]
</div>

<!-- 
    The class name news doesn’t tell you anything that is not already obvious from the content, and it cannot be used with content that isn’t “news”. Much better class name would be "article". 
-->
```

In larger projects there might be a need to have global styles applied to whole application and consistent styling to some common elements. Using unique class names can help ensure that 3rd-party CSS does not apply to your own HTML. For example, many projects use the button, btn, or icon class names. To ensure we recommend a prefix for class name can be used.

### Container vs Wrapper

In programming languages the word **container** is generally used for structures that can contain more than one objects. Bootstrap used container class in the root to center all content of the page for example. A **wrapper** instead is something that wraps around a single object to provide more functionalities and interfaces to it.

```javascript
<section class="container">
    // Surrounds many objects. Used for example to center all articles.
    <article class="wrapper">
      // Surrounds one article. Used for example to apply general rules for one article
      <div>...</div>
    </article>
    <article class="wrapper">
       <div>...</div>
    </article>
</section>

or

<ul class="menu-container">
    <li class="menu-item-wrapper">
        <div class="menu-item">...</div>
    </li>
    <li class="menu-item-wrapper">
        <div class="menu-item">...</div>
    </li>
    <li class="menu-item-wrapper">
        <div class="menu-item">...</div>
    </li>
</ul>
```

<p align="right"><a id="bem-in-css" href="#table-of-content">↩ Back To Top</a></p>

### [**BEM**](#)

With BEM (Block-Element-Modifier methodology) you can create a modular, consistent and reusable structure for your style-sheets which is easier to understand & use. **One of the goals of BEM is to make it clear what a piece of code does just by the class names.** The idea of self-documenting code is that looking at CSS classes, variables, and functions provides enough information on how the code works and how the interface components interact.

**Block**  
Elements are broken up into blocks, which is typically a container that wraps many elements. For example, a footer would be a block.

```
.navbar {...}
```

**Element**  
Many elements make up a block. Usually elements do not have any semantic meaning outside of the block.

```
.navbar__logo {...}
.navbar__brand {...}
.navbar__topNav {...}
.navbar__topNav-item {...}
.navbar__sideNav {...}
.navbar__sideNav-item {...}
.navbar__toggler {...}
```

**Modifier**  
A modifier is focused on changing how the element looks visually and/or controls its behavior.

```
.navbar__topNav--hidden {...}
.navbar__sideNav--hidden {...}
.navbar__toggler--large {...}
.navbar__topNav-item--selected {...}
.navbar__sideNav-item--wide {...}
```

<br>

> In scoped styles as vor example Vue the BEM naming scheme might not seem to be necessary anymore. But still a lot can be gained as having an indicator when to split up your components into multiple smaller ones. One advantage of BEM-ifying class names even if scoped is that it gives you an **indicator when the component could be split** in smaller ones when you start to get out-of class-names. Read more [here](https://markus.oberlehner.net/blog/how-the-bem-css-naming-scheme-can-improve-vue-component-architecture/).

> Scoped styles can have some potential pitfalls when working with a larger team. Advantages of BEM-ifying class names even with scoped classes are:<br> **1)** helps **prevent any conflict with another component** for cases when someone in your team forgot to add `scoped` to the style tag. **2)** **Testing/QA automation** to have enough specificity on class names to distinguish elements. Read more [here](https://spectrum.chat/vue-js/help/bem-and-scoped-styles~f573992a-7ca4-414c-896e-17b37eb18da7?m=MTUyMjgxNTg5OTI5MQ==).<br> **2)** makes it **easier to implement multiple visual appearances** (themes), also personally we feel very comfortable to support styling using BEM because it is easy to follow different visual styles of component. Read more [here](https://medium.com/@imanhodjaev/bem-styled-components-case-with-vue-d15901bf762e).<br> **3)** BEM structure together with CSS nesting can give you reusable components easy to create, read and copy where only the main class name need to be changed as the element & modifier with general naming can be reused.

Note! Nesting CSS descendant selectors goes against BEM philosophy and often create [specificity wars](https://stuffandnonsense.co.uk/archives/css_specificity_wars.html) that can result in unexpected behavior. As the CSS Specificity is one of the most difficult concepts to grasp in Cascading Stylesheets. Applying BEM solves most of the trouble.

```css
BAD - descendant selector

.header {
    ...
    &.button {
        ...
        &.green {
            ...
            color: green;
        }
    }
}

/* Results in a 'descendant selector'. specificity wars - risk for errors  */
.header.button.green {
    color: green;
}
```

```css
GOOD - direct selector

.header {
    ...
    &__button {
        ...
        &--green {
        ...
        color: green;
        }
    }
}

/* Results in a direct class selector, selfexplanatory and with minimal risk of errors */
.header__button--green {
  color: green;
}
```

<p align="right"><a id="naming-variations" href="#table-of-content">↩ Back To Top</a></p>

### [**Naming variations**](#)

TODO add Vue

Component name: TheHeader Class names:  
TheHeader**Wrapper TheHeader**Branding

<p align="right"><a id="css-specificity" href="#table-of-content">↩ Back To Top</a></p>

### [**CSS Selectors and specificity**](#)

CSS specificity is a set of rules used by browsers in determining which out of many developer-defined styles for an element will be applied to a specific element.

Types of elements and selector

```html
<style>
    a {
        color: red;
    }

    .link--bold {
        color: magenta;
    }

    #link {
        color: black;
    }

    a {
        color: gold !important;
    }

    a.link--bold {
        color: orange;
    }

    a[target='_blank'] {
        color: green;
    }

    a:link {
        color: white;
    }

    .link {
        color: yellow;
    }

    .link.bold {
        color: pink;
    }
</style>

<a id="link" class="link bold link--bold" target="_blank" style="color: cyan" href="#"><b>Hello World</b></a>
```

What color ha Hello World when styles are changed **one by one**?

```html
<!-- 
Following order (the more important => higher):
1) a !important
2) (inline) style="color:cyan" 
3) #link
4) .link.bold
5) a:link
6) a[target='_blank']
7) a.link--bold	
8) .link
9) .link--bold	
10) a
-->

Recommended order of pseudo selectors for an element to avoid specificity problems (LVHA-order) :link (when there is ahref and
element links to something) :visited (when link has been clicked) :hover (when mouse is over the element) :active (activation"
typically starts when the user presses down the element)
```

Following table list the importance of the rules in decreasing order:

| Prio | Rule             | Example                             | Internal Prio value   |
| :--- | :--------------- | :---------------------------------- | :-------------------- |
| #1   | Important        | `a { color: cyan !important; }`     | Overwrites all others |
| #2   | Inline style     | `<a style="color: yellow">text</a>` | 1000                  |
| #3   | Id               | `#green { color: green; }`          | 0100                  |
| #4   | Class Class      | `.wrapper .red { color: red; }`     | 0020                  |
| #5   | Element:Accessor | `a:link { color: aqua; }}`          | 0011 (last wins)      |
| #6   | Element:Accessor | `a:hover { color: yellow; }}`       | 0011 (last wins)      |
| #7   | Element Class    | `div.blue { color: blue; } }`       | 0011 (last wins)      |
| #8   | Class            | `.orange { color: orange; }`        | 0010                  |
| #9   | Element Element  | `a div { color: aqua; }`            | 0002                  |
| #10  | Element          | `a { color: black; }`               | 0001                  |

<p align="right"><a id="css-flex" href="#table-of-content">↩ Back To Top</a></p>

## [**Flex**](#)

**justify content: space-between**  
first to left, right all to right, those in between with even space

**flex-wrap: wrap** if one of flex item too wide, then place it on new row.

**flex-basis: 100%** set on flex item and forces it to be as wide as parent (therfore placed on new row)

```html
<div style="display: flex, justify-content: space-between; flex-wrap: wrap;">
    <span>Elem 1</span>
    <span>Elem 2</span>
    <span style="flex-basis: 100%">Elem 3</span>
</div>

<!-- this will set the 3 flex items as follow -->

|Elem 1| |Elem2| | Elem 3 |
```

## [**Commonly performed tasks**](#)

---

<p align="right"><a id="colors-and-shades" href="#table-of-content">↩ Back To Top</a></p>

### [**Colors & shades**](#)

Nice gray shadow with light rounded border

```css
.card {
    border: thin solid rgba(0, 0, 0, 0.1);
    box-shadow: -3px 2px 3px 2px rgba(0, 0, 0, 0.05), rgba(0, 0, 0, 0.1) 0px 1px 6px;
    border-radius: 0.5rem;
}
```

<p align="right"><a id="centering-things" href="#table-of-content">↩ Back To Top</a></p>

### [**Centering things**](#)

Flexbox is most widely and secure way of positioning.

If we want to position something AND overlap other elements then we must do it with position absolute.

**Parent is Block. Child are Inline.**  
When parent has `text-align: center` then all texts in children that are `inline` will be centered. Mostly used within simple components.

**Parent is Block. Children are mixed.**  
Use flex to place children symmetrically. when parent has position: flex then all children become bloc elements (true??? TODO).

**Child overlays other Children in Parent.**  
Parent (i.e image or a wide box) must be position:relative. Then parent set "position:absolute" and aligned relative to it parent overlaying other children. Centered with: top, left transform( (translate))

<p align="right"><a id="float-flex-grid" href="#table-of-content">↩ Back To Top</a></p>

### [**Float/Flex/Grid**](#)

#### [**Float**](#)

    TODO

#### [**Grid**](#)

    TODO

# [**HTML**](#)

---

<p align="right"><a id="html-basics" href="#table-of-content">↩ Back To Top</a></p>


#### [Basics](#)

**Display types:** There exists many elements types i.e. block, inline and inline-block elements exist. 
- **block** - one element per row. If no content/margin/padding then do not take any any space. `<div></div>` if empty is invisible, but empty `<p></p>` has a margin set by default and even if empty is takes up a whole line! Setting margin to 0 makes it disappear though. Example: `<header>, <section>, <article>,<p>, <div>` 
- **inline** - take up only contaning content width. No width/height. No top & bottom margin/padding. Examples: `<a>, <span>, <button>, <code>`
- **Inline-block** - same as inline but accept width/height and top/bottom margin/padding.
Read more about diffrences between those 3 types [here](https://stackoverflow.com/questions/9189810/css-display-inline-vs-inline-block).
- **flex** - all childeren become inline-block. With more option axis and direction for childeren can be changed i.e. `justify-content: space-between`.

```javascript
display="inline"
display="block"
display="inline-block"

display="flex",
justify-content: space-between
```

**Position:** This element _property_ specifies  an elementhow an element is positions relative to others.
- **static** - (default) no position, follow. normal flow of the page.
- **relative** - nothing happend but we can relate to it in children

- **absolute** - Taken out of the flow. Overlays others. Top left corner aligned with relative parent.

- **fixed** - Taken out of the flow. Overlay others. Do not scroll. Top left corner aligned with html/window

- **sticky** -  Nothing happens initially. Scrolls. Once it scrolled to top/bottom it gets fixed.

```html
<div position="relative">
    ...
    <div position="asolute">
        On top of eferything in parent. Reletive to parent. 
    </div>
    
</div>
```

**Box-sizing:** When defining _width_ and _height_ the total size can take margin and padding into account or not.
- **content-box** - margin/margin is then outside the set total size. 
- **border-box** - margin/padding are included in the set total size. Bootstrap for example is changing the global box-sizing from content-box to border-box.


```css
* {
    box-sizing: border-box;
}
```

<p align="right"><a id="html-document-structure" href="#table-of-content">↩ Back To Top</a></p>

#### [Document structure](#)

```html
<main>
    <header>
        A header for a document or a section
        <nav>
            Set of navigation links
        </nav>
    </header>
    
    <article>
        Used for wrapping self-containing content on a page in such a way that the content wrapped 
        in article can simply be be removed from a page and pasted into another page. It can contain
        several `section` tags inside it, that are similar to the `div` tag, but it is more meaningful
        since it wraps logical groups of related content (e.g. a chapter of an article can be wrapped
        into a secrion).
        
        <h1>What is JavaScript?</h1>
        <p>JavaScript is ...</p>
        <section>
            <h2>Javascript syntax</h2>
            <p>Syntax of js is ...</p>
        </section>
        <section>
            <h2>Javascript purpose</h2>
            <p>Purpose of js is ...</p>
        </section>
        <section>
            <h2>Javascript examples</h2>
            <p>Some js examples ...</p>
        </section>
    </article>
    
    <aside>
        Content aside from the content (like a sidebar)
    </aside>
    
    <footer>
        A footer for a document or a section
    </footer>
</main>
```

<p align="right"><a id="html-page-building-blocks" href="#table-of-content">↩ Back To Top</a></p>

### [Building blocks of a page](#)

A page is build of modules (small building blocks sometimes called components or widgets). There is a special naming for blocks with different purposes.

- **Container** 
    Basic layout component, often containing main content of the page. Often used to to position main page content i.e by bootstrap: `class="container"` `class="container-fluid"`.

- **Row** - 

- **Column** -  

- **Panel** - 

- **Form** 
    Element used to collect different types of input elements like: text fields, checkboxes, radio buttons, submit buttons and post a HTTP Post Request with data to the derver.

- **Modal** -  
    It is a



