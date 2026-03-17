# 1. Callback Function

A callback function is a function that is **given to another function to run later.**

Simple Example:

```js
function washClothes(callback) {
  console.log("Washing clothes...");
  callback();
}

function dryClothes() {
  console.log("Drying clothes...");
}

washClothes(dryClothes);
```

Here, `dryClothes` is a callback.  
It runs after washing.

Real life idea:  
Mother says: "After washing, dry the clothes."

---

# 2. Higher Order Function

A higher order function is a function that:

- takes another function as input
- or returns a function

Example:

```js
function doWork(task) {
  task();
}

function study() {
  console.log("Studying JavaScript");
}

doWork(study);
```

Here `doWork` is a higher order function.

---

# 3. Shallow Copy vs Deep Copy

Shallow copy means **copy only outer values.  
Inner objects still share memory.**

Example:

```js
let person1 = {
  name: "Sanjay",
  address: { city: "Hyderabad" },
};

let person2 = { ...person1 };

person2.address.city = "Bangalore";

console.log(person1.address.city);
```

Output:

```
Bangalore

```

Because both share same inner object.

Deep copy means **completely separate copy.**

```js
let person2 = JSON.parse(JSON.stringify(person1));
```

Now changing one will not affect the other.

---

# 4. What are Callbacks (Concept)

Callbacks are mainly used when work **takes time.**

Example:

```js
setTimeout(function () {
  console.log("Food is ready");
}, 2000);
```

After 2 seconds callback runs.

Used in:

- API calls
- database work
- timers
- events

---

# 5. Events in JavaScript

Events are **user actions.**

Examples:

- clicking button
- typing keyboard
- submitting form

Example:

```js
button.addEventListener("click", function () {
  console.log("Button clicked");
});
```

---

# 6. Data Types in JavaScript

Primitive Data Types:

- string → "hello"
- number → 10
- boolean → true
- undefined
- null
- bigint
- symbol

Non-Primitive:

- object
- array
- function

---

# 7. Import Function From Another File

## File: add.js

```js
function add(a, b) {
  return a + b;
}

module.exports = add;
```

Here we are **exporting the function** so other files can use it.

---

## File: main.js

```js
const add = require("./add");

console.log(add(2, 3));
```

Here we are **importing the function** from another file.

---

## Output

```
5

```

---

# 8. Truthy and Falsy Values

Falsy values are values that behave like false.

They are:

- false
- 0
- ""
- null
- undefined
- NaN

Everything else is truthy.

---

# 9. Why let is better than var

`let` is safer.

Example:

```js
if (true) {
  let a = 10;
}

console.log(a);
```

This gives error.

But var:

```js
if (true) {
  var a = 10;
}

console.log(a);
```

This works.

So var can create bugs.

---

# 10. Type of null

```js
typeof null;
```

Output:

```
object

```

---

# 11. What is NPM

NPM is used to **install packages.**

Example:

```
npm install express

```

It helps us use libraries written by others.

---

# 12. What is NVM

NVM helps us **switch Node versions.**

Example:

```
nvm install 18
nvm use 18

```

Useful when different projects need different Node versions.

---

# 13. Spread Operator

The spread operator (`...`) is used to **expand elements of an iterable (like array or object) into individual elements.**

Example:

```js
let a = [1, 2];
let b = [...a, 3];

console.log(b);
```

Output:

```
[1,2,3]

```

---

# 14. Rest Operator

Rest collects many values into one array.

Example:

```js
function total(...nums) {
  console.log(nums);
}

total(1, 2, 3, 4);
```

Output:

```
[1,2,3,4]

```

---

# 15. map() in JavaScript

map is used to **change every value in array.**

Example:

```js
let marks = [10, 20, 30];

let newMarks = marks.map(function (m) {
  return m + 5;
});

console.log(newMarks);
```

Output:

```
[15,25,35]

```
