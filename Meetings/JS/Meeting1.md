# JavaScript First Lecture: Welcome to the Fun Side of Coding

## What We'll Learn Today

- What is JavaScript? (And why it's AWESOME!)
- Your first "Hello World" program
- Variables: The magic boxes of programming
- Numbers and text

---

## What is JavaScript?

JavaScript is a **high-level, interpreted programming language** that brings web pages to life!

JavaScript was created in just **10 days** in 1995 by Brendan Eich at Netscape! Despite its name, it has no relation to Java programming language.

**Web Technologies Stack:**

- **HTML** = Structure and content (the skeleton)
- **CSS** = Styling and layout (the appearance)
- **JavaScript** = Behavior and interactivity (the brain)

**Key Characteristics:**

- **Dynamic Typing**: Variables can hold different data types without declaration
- **Interpreted Language**: Code runs directly without compilation
- **Object-Oriented & Functional**: Supports multiple programming paradigms
- **Event-Driven**: Responds to user interactions and system events

### Dynamic Typing

>loosely typed

Unlike languages like C++ or Java, JavaScript uses **dynamic typing**:

```javascript
let myVariable = 42; // Number
console.log(typeof myVariable); // "number"

myVariable = "Hello World"; // Now it's a String
console.log(typeof myVariable); // "string"

myVariable = true; // Now it's a Boolean
console.log(typeof myVariable); // "boolean"
```

> `typeof()` is a special operator that tells you the type of a variable.

---

## Your First JavaScript Code

```javascript
// This is your first JavaScript code!
console.log("Hello, World! 🌍");
console.log("Welcome to JavaScript! 🎉");
```

**What just happened?**

- `console.log()` is like a megaphone that shouts to the console
- Everything inside the quotes `" "` is exactly what gets displayed
- The `//` makes a comment (notes for humans, ignored by computer)

### Console Debugging

1. Open your browser
2. Press `F12` (or right-click → Inspect)
3. Go to "Console" tab
4. Type: `console.log("My name is [YOUR NAME]!")`

---

## Variables: Data Storage in JavaScript

Variables are containers that store data values. In JavaScript, we have three ways to declare variables, each with different characteristics.

### Variable Declaration Keywords

#### 1. `let` - Modern Block-Scoped Variable

```javascript
let playerName = "Alex";
let playerScore = 100;

// Can be reassigned
playerScore = 150;
console.log("New score: " + playerScore);
```

**Characteristics of `let`:**

- Block-scoped (limited to { } blocks)
- Can be reassigned
- Cannot be redeclared in same scope
- Temporal Dead Zone (must declare before use)

### 2. `const` - Constant Values

```javascript
const GAME_NAME = "Space Adventure";
const MAX_PLAYERS = 4;
const CONFIG = {
  difficulty: "medium",
  sound: true,
};

// This would cause an error:
// GAME_NAME = "New Game"; // ❌ Cannot reassign const
```

**Characteristics of `const`:**

- Block-scoped
- Cannot be reassigned
- Cannot be redeclared
- Must be initialized when declared
- Objects/arrays can have their contents modified

#### 3. `var` - Legacy Function-Scoped Variable

```javascript
var oldStyleVariable = "I'm from the past";
var globalCounter = 0;

// var has function scope, not block scope
function example() {
  var functionScoped = "only accessible in this function";
}
```

**Characteristics of `var` (Legacy):**

- Function-scoped (not block-scoped)
- Can be reassigned and redeclared
- Hoisted (can be used before declaration)
- Can cause unexpected behavior

### Best Practices for Variable Declaration

1. **Use `const` by default** - for values that won't change
2. **Use `let`** - when you need to reassign the variable
3. **Avoid `var`** - it's legacy and can cause issues

```javascript
// Good practices
const userName = "John Doe"; // Won't change
const userAge = 25; // Won't change
let currentScore = 0; // Will change during game
let isGameActive = true; // Will toggle

```

### Data Types in JavaScript

JavaScript has several built-in data types:

```javascript
// Primitive Data Types
let numberValue = 42; // Number
let stringValue = "Hello World"; // String
let booleanValue = true; // Boolean
let undefinedValue; // Undefined
let nullValue = null; // Null
let symbolValue = Symbol("id"); // Symbol (ES6)
let bigIntValue = 123n; // BigInt (ES2020)

// Non-Primitive Data Type
let objectValue = {
  // Object
  name: "John",
  age: 30,
};
let arrayValue = [1, 2, 3, 4, 5]; // Array (special object)

// Check data types
console.log(typeof numberValue); // "number"
console.log(typeof stringValue); // "string"
console.log(typeof booleanValue); // "boolean"
console.log(typeof objectValue); // "object"
console.log(typeof arrayValue); // "object" (arrays are objects)
```

### Game Example: Character Creation

```javascript
// Let's create a game character!
let characterName = "Lightning McQueen";
let characterLevel = 5;
let characterHealth = 100;
let characterPower = "Super Speed";

console.log("Character Created!");
console.log("Name: " + characterName);
console.log("Level: " + characterLevel);
console.log("Health: " + characterHealth + "%");
console.log("Special Power: " + characterPower);
```

---

## JavaScript Operators

Operators are symbols that perform operations on values and variables. JavaScript provides several categories of operators.

### Arithmetic Operators

```javascript
let a = 10;
let b = 3;

console.log("Addition: " + a + " + " + b + " = " + (a + b)); // 13
console.log("Subtraction: " + a + " - " + b + " = " + (a - b)); // 7
console.log("Multiplication: " + a + " * " + b + " = " + a * b); // 30
console.log("Division: " + a + " / " + b + " = " + a / b); // 3.333...
console.log("Modulus (remainder): " + a + " % " + b + " = " + (a % b)); // 1
console.log("Exponentiation: " + a + " ** " + b + " = " + a ** b); // 1000

// Increment and Decrement
let counter = 5;
console.log("Original counter: " + counter); // 5
console.log("Pre-increment: " + ++counter); // 6 (increment first, then use)
console.log("Post-increment: " + counter++); // 6 (use first, then increment)
console.log("After post-increment: " + counter); // 7
console.log("Pre-decrement: " + --counter); // 6 (decrement first, then use)
console.log("Post-decrement: " + counter--); // 6 (use first, then decrement)
console.log("Final counter: " + counter); // 5
```

### Assignment Operators

```javascript
let score = 100;

score += 50; // score = score + 50;  → 150
score -= 20; // score = score - 20;  → 130
score *= 2; // score = score * 2;   → 260
score /= 4; // score = score / 4;   → 65
score %= 10; // score = score % 10;  → 5
score **= 2; // score = score ** 2;  → 25

console.log("Final score: " + score); // 25
```

### Comparison Operators

```javascript
let x = 5;
let y = "5";
let z = 10;

// Equality (loose - type coercion)
console.log(x == y); // true (5 == "5" → true, converts string to number)
console.log(x == z); // false (5 == 10 → false)

// Strict equality (no type coercion)
console.log(x === y); // false (5 === "5" → false, different types)
console.log(x === 5); // true (same value and type)

// Inequality
console.log(x != y); // false (5 != "5" → false, converts string to number)
console.log(x !== y); // true (5 !== "5" → true, different types)

// Relational operators
console.log(x < z); // true (5 < 10)
console.log(x > z); // false (5 > 10)
console.log(x <= 5); // true (5 <= 5)
console.log(x >= z); // false (5 >= 10)
```

### Logical Operators

```javascript
let isLoggedIn = true;
let hasPermission = false;
let isAdmin = true;

// AND operator (&&) - all conditions must be true
console.log(isLoggedIn && hasPermission); // false
console.log(isLoggedIn && isAdmin); // true

// OR operator (||) - at least one condition must be true
console.log(isLoggedIn || hasPermission); // true
console.log(hasPermission || false); // false

// NOT operator (!) - inverts the boolean value
console.log(!isLoggedIn); // false
console.log(!hasPermission); // true
console.log(!!isLoggedIn); // true (double negation)
```

### String Operators

```javascript
let firstName = "John";
let lastName = "Doe";

// Concatenation with +
let fullName = firstName + " " + lastName;
console.log(fullName); // "John Doe"

// Concatenation assignment
let greeting = "Hello, ";
greeting += firstName;
console.log(greeting); // "Hello, John"

// Template literals (ES6) - more powerful string concatenation
let age = 25;
let message = `My name is ${firstName} ${lastName} and I am ${age} years old.`;
console.log(message); // "My name is John Doe and I am 25 years old."
```

> try to do the character creation example with template literals

### Ternary (Conditional) Operator

```javascript
let age = 18;
let canVote = age >= 18 ? "Yes" : "No";
console.log("Can vote: " + canVote); // "Can vote: Yes"

// Multiple conditions
let score = 85;
let grade = score >= 90 ? "A" : score >= 80 ? "B" : score >= 70 ? "C" : "F";
console.log("Grade: " + grade); // "Grade: B"
```

### typeof Operator

```javascript
console.log(typeof 42); // "number"
console.log(typeof "Hello"); // "string"
console.log(typeof true); // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object" (this is a known quirk)
console.log(typeof {}); // "object"
console.log(typeof []); // "object"
console.log(typeof function () {}); // "function"
```

### Math Operations with Real Examples

```javascript
// Shopping cart calculation
const itemPrice = 29.99;
const quantity = 3;
const taxRate = 0.08;

const subtotal = itemPrice * quantity;
const tax = subtotal * taxRate;
const total = subtotal + tax;

console.log("Item price: $" + itemPrice.toFixed(2));
console.log("Quantity: " + quantity);
console.log("Subtotal: $" + subtotal.toFixed(2));
console.log("Tax (8%): $" + tax.toFixed(2));
console.log("Total: $" + total.toFixed(2));

// Game score calculation
let baseScore = 1000;
let timeBonus = 500;
let accuracyMultiplier = 1.5;
let penalties = 200;

let finalScore = (baseScore + timeBonus) * accuracyMultiplier - penalties;
console.log("Final game score: " + Math.round(finalScore));

// Temperature conversion
let celsius = 25;
let fahrenheit = (celsius * 9) / 5 + 32;
let kelvin = celsius + 273.15;

console.log(celsius + "°C = " + fahrenheit + "°F = " + kelvin + "K");
```

---

## Working with Text (Strings)

Text in programming is called "strings" (like a string of letters!)

```javascript
let firstName = "John";
let lastName = "Doe";
let fullName = firstName + " " + lastName;

console.log("First name: " + firstName);
console.log("Last name: " + lastName);
console.log("Full name: " + fullName);

// Fun with strings!
let message = "JavaScript";
let exclamation = "is awesome!";
let fullMessage = message + " " + exclamation + " 🎉";

console.log(fullMessage);
```

### String Magic Tricks

```javascript
let word = "JavaScript";

console.log("Length of the word: " + word.length);
console.log("In UPPERCASE: " + word.toUpperCase());
console.log("in lowercase: " + word.toLowerCase());
```

---

## Mini Project: Personal Introduction

Let's combine everything we learned to create a personal introduction!

```javascript
// Your personal info
let name = "Put your name here";
let age = 20; // Your age
let hobby = "Your favorite hobby";
let favoriteFood = "Your favorite food";
let dreamJob = "Your dream job";

// Create introduction
console.log(`🌟 Meet ${name}!`);
console.log(`📅 Age: ${age} years old`);
console.log(`🎨 Hobby: ${hobby}`);
console.log(`🍕 Favorite food: ${favoriteFood}`);
console.log(`💼 Dream job: ${dreamJob}`);
console.log(`🚀 Currently learning: JavaScript!`);

console.log(`Meet ${name}, a ${age}-year-old who loves ${hobby} and enjoys ${favoriteFood}. Their dream job is to become a ${dreamJob}.`);

// Calculate something fun
let yearsToGraduate = 4;
let graduationYear = 2025 + yearsToGraduate;
console.log(`🎓 Will graduate in: ${graduationYear}`);
```

---

## Practice Challenges

### Challenge 1: Advanced Calculator

Create a comprehensive calculator using all operators:

```javascript
let num1 = 15;
let num2 = 4;

// Arithmetic operations
console.log("=== ARITHMETIC OPERATIONS ===");
console.log(`${num1} + ${num2} = ${num1 + num2}`);
console.log(`${num1} - ${num2} = ${num1 - num2}`);
console.log(`${num1} * ${num2} = ${num1 * num2}`);
console.log(`${num1} / ${num2} = ${num1 / num2}`);
console.log(`${num1} % ${num2} = ${num1 % num2}`);
console.log(`${num1} ** ${num2} = ${num1 ** num2}`);

// Comparison operations
console.log("=== COMPARISON OPERATIONS ===");
console.log(`${num1} == ${num2}: ${num1 == num2}`);
console.log(`${num1} === ${num2}: ${num1 === num2}`);
console.log(`${num1} > ${num2}: ${num1 > num2}`);
console.log(`${num1} < ${num2}: ${num1 < num2}`);
```

## Remember This

> "Programming is not about what you know; it's about what you can figure out. Master the fundamentals, and complex problems become manageable." 🌟

---

## Task (Essential Practice)

You are creating a program that calculate and show the citizen if he can vote or not based on his birth year.

```javascript
const name = "Ahmed";
const birthYear = 2004;
```

- The citizen can vote if his age is greater than or equal to 18.
- display a message like "Ahmed can vote! your age is 21" or "Ahmed cannot vote yet. you can vote 2 years latter" based on the age.
- hint `const currentYear = new Date().getFullYear();` to get the current year.
- Hint user ternary operator to display the message.
