## 1. Spread Operator

### Definition

The spread operator (`...`) is used to expand iterable elements such as arrays, strings, or objects into individual elements. It helps in copying, merging, and passing values efficiently.

---

### Copying an Array (Shallow Copy)

```js
let arr1 = [1, 2, 3];
let arr2 = [...arr1];

console.log(arr2);
```

Output

```
[1, 2, 3]

```

Description

The spread operator creates a new array by copying the elements of `arr1`.  
This is called a **shallow copy**, meaning primitive values are copied but nested objects will still share memory references.

---

### Merging Arrays

```js
let a = [10, 20];
let b = [30, 40];

let merged = [...a, ...b];
console.log(merged);
```

Output

```
[10, 20, 30, 40]

```

Description

The elements of both arrays are expanded and combined into a single new array.  
This approach is cleaner and more readable than using `concat()`.

---

### Adding Elements While Copying

```js
let arr = [1, 2];

let newArr = [...arr, 3, 4];
console.log(newArr);
```

Output

```
[1, 2, 3, 4]

```

Description

The spread operator copies the original array and new elements are appended during creation.  
This follows **immutable programming**, since the original array is not modified.

---

### Spread in Function Arguments

```js
function sum(x, y, z) {
  return x + y + z;
}

let nums = [5, 10, 15];
console.log(sum(...nums));
```

Output

```
30

```

Description

The spread operator expands the array into individual arguments.  
This is useful when a function expects multiple parameters but values are stored in an array.

---

### Spread with Objects

```js
let obj1 = { name: "Sanjay" };
let obj2 = { age: 22 };

let merged = { ...obj1, ...obj2 };
console.log(merged);
```

Output

```
{ name: "Sanjay", age: 22 }

```

Description

Object properties are copied into a new object.  
This technique is commonly used in React state updates and API data handling.

---

### Overriding Properties

```js
let user = { name: "A", age: 20 };

let updated = { ...user, age: 25 };
console.log(updated);
```

Output

```
{ name: "A", age: 25 }

```

Description

If duplicate properties exist, the last value overrides previous ones.  
This is useful for updating object data without mutating the original object.

---

## 2. Template Literals

### Definition

Template literals allow embedding variables and expressions inside strings using backticks.

---

### String Interpolation

```js
let name = "Sanjay";

let msg = `Hello ${name}`;
console.log(msg);
```

Output

```
Hello Sanjay

```

Description

`${}` allows inserting variable values directly into the string.  
This improves readability compared to string concatenation.

---

### Expression Evaluation

```js
let a = 10;
let b = 20;

console.log(`Sum is ${a + b}`);
```

Output

```
Sum is 30

```

Description

Any valid JavaScript expression can be evaluated inside template literals.

---

### Multi-line Strings

```js
let text = `This is
JavaScript
Seminar`;

console.log(text);
```

Output

```
This is
JavaScript
Seminar

```

Description

Template literals preserve line breaks, eliminating the need for `\n`.

---

## 3. Default Parameters

### Definition

Default parameters assign default values to function parameters when no argument or `undefined` is passed.

---

### Basic Default Value

```js
function greet(name = "Guest") {
  console.log(name);
}

greet();
```

Output

```
Guest

```

Description

Since no argument is passed, the default value is used.

---

### Passing Value

```js
greet("Sanjay");
```

Output

```
Sanjay

```

Description

When a value is provided, it overrides the default parameter.

---

### Undefined vs Null

```js
function show(x = 10) {
  console.log(x);
}

show(undefined);
show(null);
```

Output

```
10
null

```

Description

Default values apply only when argument is `undefined`.  
If `null` is passed, it is treated as a valid value.

---

## 4. Destructuring

### Definition

Destructuring allows extracting values from arrays or objects into separate variables.

---

### Array Destructuring

```js
let arr = [10, 20, 30];

let [a, b, c] = arr;

console.log(a, b, c);
```

Output

```
10 20 30

```

Description

Array elements are assigned based on position.

---

### Skipping Values

```js
let [x, , z] = [5, 10, 15];

console.log(x, z);
```

Output

```
5 15

```

Description

Comma can be used to skip unwanted values.

---

### Default Values

```js
let [p = 5, q = 10] = [1];

console.log(p, q);
```

Output

```
1 10

```

Description

Default values are used when array elements are missing.

---

### Rest Pattern

```js
let [first, ...rest] = [1, 2, 3, 4];

console.log(first);
console.log(rest);
```

Output

```
1
[2, 3, 4]

```

Description

Rest operator collects remaining elements into an array.

---

### Object Destructuring

```js
let user = { name: "Sanjay", age: 22 };

let { name, age } = user;

console.log(name, age);
```

Output

```
Sanjay 22

```

Description

Object properties are extracted using property names.

---

### Renaming Variable

```js
let { name: username } = user;

console.log(username);
```

Output

```
Sanjay

```

Description

Variables can be renamed while destructuring.

---
