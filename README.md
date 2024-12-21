
# JavaScript

## **1. Basics of JavaScript**

### Variables and Data Types
```javascript
let name = "Dinesh";
const age = 25;
var isStudent = true;
```

### Operators
```javascript
let sum = 5 + 10; // Arithmetic
let isEqual = (5 === 10); // Comparison
```

### Control Flow
```javascript
if (age > 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}
```

### Functions
```javascript
function greet() {
  return "Hello, World!";
}
console.log(greet());
```

---

## **2. Execution Context and Hoisting**
### Execution Context
```javascript
function test() {
  console.log(a); // undefined
  var a = 10;
  console.log(a); // 10
}
test();
// Execution context determines how code is parsed and executed line by line.
```

### Hoisting
```javascript
console.log(message); // undefined due to hoisting
var message = "Hoisting example";
```

---

## **3. Scope and Lexical Environment**
### Scope
```javascript
function parent() {
  let outerVar = "I am outer";
  function child() {
    console.log(outerVar); // Accessing outer variable
  }
  child();
}
parent();
```

### Lexical Environment
```javascript
let globalVar = "Global";
function outer() {
  let outerVar = "Outer";
  function inner() {
    console.log(globalVar, outerVar); // Lexical scoping in action
  }
  inner();
}
outer();
```

### Block Scope and Shadowing
```javascript
let x = 10;
{
  let x = 20; // Shadows outer 'x'
  console.log(x); // 20
}
console.log(x); // 10
```

---

## **4. Closures**
### What are Closures?
```javascript
function makeCounter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}
const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## **5. Callback Functions and Event Listeners**
### Callback Functions
```javascript
function processData(data, callback) {
  console.log("Processing: " + data);
  callback();
}
processData("Example", () => {
  console.log("Callback executed");
});
```

### Event Listeners
```javascript
document.querySelector("button").addEventListener("click", () => {
  console.log("Button clicked!");
});
```

---

## **6. Asynchronous JavaScript**
### Promises
```javascript
fetch("https://api.example.com/data")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

### Async/Await
```javascript
async function fetchData() {
  try {
    let response = await fetch("https://api.example.com/data");
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
fetchData();
```

---

## **7. Array Methods: Map, Filter, Reduce**
### Map
```javascript
const numbers = [1, 2, 3];
const squared = numbers.map(num => num ** 2);
console.log(squared); // [1, 4, 9]
```

### Filter
```javascript
const ages = [18, 16, 21, 14];
const adults = ages.filter(age => age >= 18);
console.log(adults); // [18, 21]
```

### Reduce
```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 10
```

---

## **8. DOM Manipulation**
### Selecting and Modifying Elements
```javascript
let title = document.querySelector("h1");
title.textContent = "Updated Title";
```

### Event Handling
```javascript
document.querySelector("button").addEventListener("click", () => {
  alert("Button clicked!");
});
```

---

## **9. Local Storage**
### Working with Local Storage
```javascript
localStorage.setItem("username", "Dinesh");
console.log(localStorage.getItem("username"));
```

---

## **10. Frontend Frameworks**
### React Basics
```javascript
function App() {
  return <h1>Hello, React!</h1>;
}
```

---

## **11. Build Tools**
### Using npm
```bash
npm init -y
npm install react
```

---

## **12. Backend Integration**
### REST APIs
```javascript
fetch("/api/resource", { method: "POST", body: JSON.stringify({ key: "value" }) });
```

---

## **13. Debugging**
### Using Console
```javascript
console.log("Debugging value:", someVariable);
```

---

## **14. Deployment**
### Hosting on Vercel
1. Install Vercel CLI: `npm install -g vercel`
2. Deploy: `vercel`

---

## **15. Error Handling**
### Try-Catch Block
```javascript
try {
  let result = riskyFunction();
  console.log(result);
} catch (error) {
  console.error("An error occurred:", error.message);
}
```

---

## **16. Prototypes and Inheritance**
### Prototypes
```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function () {
  return `Hello, my name is ${this.name}`;
};
let person = new Person("Dinesh");
console.log(person.greet());
```

### Class Syntax
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}
class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}
let dog = new Dog("Rover");
dog.speak();
```

---

## **17. Modules in JavaScript**
### Export and Import
#### Export
```javascript
// utils.js
export function add(a, b) {
  return a + b;
}
```
#### Import
```javascript
// main.js
import { add } from './utils.js';
console.log(add(2, 3));
```

---

## **18. Performance Optimization**
### Debouncing and Throttling
#### Debounce
```javascript
function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => func.apply(this, args), delay);
  };
}
```
#### Throttle
```javascript
function throttle(func, limit) {
  let lastFunc;
  let lastRan;
  return function (...args) {
    const context = this;
    if (!lastRan) {
      func.apply(context, args);
      lastRan = Date.now();
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(() => {
        if (Date.now() - lastRan >= limit) {
          func.apply(context, args);
          lastRan = Date.now();
        }
      }, limit - (Date.now() - lastRan));
    }
  };
}
```

---
