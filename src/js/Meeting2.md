# JavaScript Second Lecture: Control Flow and Functions

## What We'll Learn Today

- Control structures: Making decisions with if/else
- Loops: Repeating actions efficiently
- Functions: Building reusable code blocks
- Arrays: Storing multiple values
- Problem-solving with real examples

---

## Control Structures: Making Decisions

Control structures allow your program to make decisions and execute different code based on conditions.

### If Statements

The `if` statement executes code only when a condition is true:

```javascript
let temperature = 25;

if (temperature > 20) {
    console.log("It's a warm day! 🌞");
}

// With else
let age = 17;

if (age >= 18) {
    console.log("You can vote! 🗳️");
} else {
    console.log("You're not old enough to vote yet.");
}
```

### If-Else If-Else Chain

Handle multiple conditions with else if:

```javascript
let grade = 85;

if (grade >= 90) {
    console.log("Excellent! Grade: A 🌟");
} else if (grade >= 80) {
    console.log("Great job! Grade: B 👍");
} else if (grade >= 70) {
    console.log("Good work! Grade: C 👌");
} else if (grade >= 60) {
    console.log("You passed! Grade: D 📝");
} else {
    console.log("Need improvement. Grade: F 📚");
}
```

### Switch Statements

When you have many conditions based on a single value:

```javascript
let dayOfWeek = 3;
let dayName;

switch (dayOfWeek) {
    case 1:
        dayName = "Monday";
        break;
    case 2:
        dayName = "Tuesday";
        break;
    case 3:
        dayName = "Wednesday";
        break;
    case 4:
        dayName = "Thursday";
        break;
    case 5:
        dayName = "Friday";
        break;
    case 6:
        dayName = "Saturday";
        break;
    case 7:
        dayName = "Sunday";
        break;
    default:
        dayName = "Invalid day";
}

console.log(`Today is ${dayName}`);
```

### Game Example: Player Status Checker

```javascript
const playerName = "Alex";
const playerLevel = 15;
const playerHealth = 75;
const hasSpecialWeapon = true;

console.log(`=== ${playerName}'s Status ===`);

// Check player level
if (playerLevel >= 20) {
    console.log("🏆 Expert Player!");
} else if (playerLevel >= 10) {
    console.log("⭐ Intermediate Player");
} else {
    console.log("🌱 Beginner Player");
}

// Check health status
if (playerHealth > 80) {
    console.log("💚 Health: Excellent");
} else if (playerHealth > 50) {
    console.log("💛 Health: Good");
} else if (playerHealth > 20) {
    console.log("🧡 Health: Low - Find health pack!");
} else {
    console.log("❤️ Health: Critical - Danger!");
}

// Check equipment
if (hasSpecialWeapon && playerLevel >= 10) {
    console.log("⚔️ Ready for boss battle!");
} else if (hasSpecialWeapon) {
    console.log("🗡️ You have a special weapon, but need more experience");
} else {
    console.log("🔨 Find better weapons to improve your chances");
}
```

---

## Loops: Repeating Actions

Loops allow you to execute code multiple times without writing it repeatedly.

### For Loop

Perfect when you know how many times to repeat:

```javascript
// Basic for loop
console.log("Counting to 5:");
for (let i = 1; i <= 5; i++) {
    console.log(`Count: ${i}`);
}

// Loop with different step
console.log("\nEven numbers from 2 to 10:");
for (let i = 2; i <= 10; i += 2) {
    console.log(i);
}

// Countdown
console.log("\nRocket launch countdown:");
for (let i = 10; i >= 1; i--) {
    console.log(`${i}...`);
}
console.log("🚀 Blast off!");
```

### While Loop

Continues while a condition is true:

```javascript
let password = "";
let attempts = 0;
const maxAttempts = 3;

// Simulate password attempts
while (password !== "secret123" && attempts < maxAttempts) {
    attempts++;
    console.log(`Attempt ${attempts}: Enter password`);
    
    // Simulate different password attempts
    if (attempts === 1) password = "wrong1";
    else if (attempts === 2) password = "wrong2";
    else password = "secret123";
    
    if (password === "secret123") {
        console.log("✅ Access granted!");
    } else if (attempts < maxAttempts) {
        console.log("❌ Wrong password, try again");
    }
}

if (attempts >= maxAttempts && password !== "secret123") {
    console.log("🔒 Account locked! Too many failed attempts");
}
```

### Do-While Loop

Executes at least once, then checks condition:

```javascript
let userChoice;

do {
    console.log("\n=== Game Menu ===");
    console.log("1. Start Game");
    console.log("2. View Scores");
    console.log("3. Exit");
    
    // Simulate user input
    userChoice = Math.floor(Math.random() * 4) + 1; // Random choice 1-4
    console.log(`You chose: ${userChoice}`);
    
    switch (userChoice) {
        case 1:
            console.log("🎮 Starting new game...");
            break;
        case 2:
            console.log("📊 Displaying high scores...");
            break;
        case 3:
            console.log("👋 Thanks for playing!");
            break;
        default:
            console.log("❓ Invalid choice, please try again");
    }
} while (userChoice !== 3);
```

### Loop Control: Break and Continue

```javascript
console.log("Finding first number divisible by 7:");
for (let i = 1; i <= 50; i++) {
    if (i % 7 === 0) {
        console.log(`Found it: ${i}`);
        break; // Exit the loop
    }
}

console.log("\nOdd numbers from 1 to 10:");
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        continue; // Skip even numbers
    }
    console.log(i);
}
```

---

## Functions: Building Reusable Code

Functions are reusable blocks of code that perform specific tasks.

### Function Declaration

```javascript
// Basic function
function greetUser() {
    console.log("Hello! Welcome to our website! 👋");
}

// Call the function
greetUser();

// Function with parameters
function greetUserByName(name) {
    console.log(`Hello, ${name}! Welcome to our website! 👋`);
}

greetUserByName("Sarah");
greetUserByName("Ahmed");
```

### Functions with Return Values

```javascript
// Function that returns a value
function addNumbers(a, b) {
    return a + b;
}

let result = addNumbers(5, 3);
console.log(`5 + 3 = ${result}`);

// Function with multiple parameters and calculations
function calculateArea(length, width) {
    const area = length * width;
    return area;
}

function calculatePerimeter(length, width) {
    const perimeter = 2 * (length + width);
    return perimeter;
}

const roomLength = 12;
const roomWidth = 8;

console.log(`Room dimensions: ${roomLength}m × ${roomWidth}m`);
console.log(`Area: ${calculateArea(roomLength, roomWidth)} square meters`);
console.log(`Perimeter: ${calculatePerimeter(roomLength, roomWidth)} meters`);
```

### Function Expressions and Arrow Functions

```javascript
// Function expression
const multiply = function(a, b) {
    return a * b;
};

// Arrow function (ES6)
const divide = (a, b) => {
    return a / b;
};

// Short arrow function (for single expressions)
const square = x => x * x;
const double = x => x * 2;

console.log(`multiply(4, 5) = ${multiply(4, 5)}`);
console.log(`divide(20, 4) = ${divide(20, 4)}`);
console.log(`square(6) = ${square(6)}`);
console.log(`double(7) = ${double(7)}`);
```

### Functions with Default Parameters

```javascript
function createProfile(name, age = 18, country = "Unknown") {
    return `Name: ${name}, Age: ${age}, Country: ${country}`;
}

console.log(createProfile("John"));
console.log(createProfile("Sarah", 25));
console.log(createProfile("Ahmed", 30, "Egypt"));
```

### Real-World Function Examples

```javascript
// Temperature conversion functions
function celsiusToFahrenheit(celsius) {
    return (celsius * 9/5) + 32;
}

function fahrenheitToCelsius(fahrenheit) {
    return (fahrenheit - 32) * 5/9;
}

// Grade calculator
function calculateGrade(score) {
    if (score >= 90) return "A";
    if (score >= 80) return "B";
    if (score >= 70) return "C";
    if (score >= 60) return "D";
    return "F";
}

// Password strength checker
function checkPasswordStrength(password) {
    let strength = 0;
    let feedback = [];
    
    if (password.length >= 8) {
        strength += 1;
    } else {
        feedback.push("Use at least 8 characters");
    }
    
    if (/[A-Z]/.test(password)) {
        strength += 1;
    } else {
        feedback.push("Include uppercase letters");
    }
    
    if (/[0-9]/.test(password)) {
        strength += 1;
    } else {
        feedback.push("Include numbers");
    }
    
    if (/[!@#$%^&*]/.test(password)) {
        strength += 1;
    } else {
        feedback.push("Include special characters");
    }
    
    const strengthLevels = ["Very Weak", "Weak", "Fair", "Good", "Strong"];
    return {
        level: strengthLevels[strength],
        feedback: feedback
    };
}

// Test the functions
console.log("=== Temperature Conversion ===");
console.log(`25°C = ${celsiusToFahrenheit(25)}°F`);
console.log(`77°F = ${fahrenheitToCelsius(77).toFixed(1)}°C`);

console.log("\n=== Grade Calculator ===");
console.log(`Score 95: Grade ${calculateGrade(95)}`);
console.log(`Score 73: Grade ${calculateGrade(73)}`);

console.log("\n=== Password Strength ===");
let passwordTest = checkPasswordStrength("MyPass123!");
console.log(`Strength: ${passwordTest.level}`);
if (passwordTest.feedback.length > 0) {
    console.log("Suggestions:", passwordTest.feedback.join(", "));
}
```

---

## Arrays: Storing Multiple Values

Arrays allow you to store multiple values in a single variable.

### Creating and Accessing Arrays

```javascript
// Creating arrays
let fruits = ["apple", "banana", "orange", "grape"];
let numbers = [1, 2, 3, 4, 5];
let mixed = ["John", 25, true, "Developer"];

// Accessing array elements (0-indexed)
console.log("First fruit:", fruits[0]);
console.log("Second fruit:", fruits[1]);
console.log("Last fruit:", fruits[fruits.length - 1]);

// Array properties
console.log("Number of fruits:", fruits.length);
console.log("Is array empty?", fruits.length === 0);
```

### Array Methods

```javascript
let shoppingList = ["milk", "bread", "eggs"];

// Adding elements
shoppingList.push("cheese"); // Add to end
shoppingList.unshift("butter"); // Add to beginning

console.log("Updated list:", shoppingList);

// Removing elements
let lastItem = shoppingList.pop(); // Remove from end
let firstItem = shoppingList.shift(); // Remove from beginning

console.log("Removed:", lastItem, "and", firstItem);
console.log("Final list:", shoppingList);

// Finding elements
let position = shoppingList.indexOf("bread");
console.log("Bread is at position:", position);

let hasEggs = shoppingList.includes("eggs");
console.log("List includes eggs:", hasEggs);
```

### Looping Through Arrays

```javascript
let students = ["Alice", "Bob", "Charlie", "Diana"];

// For loop
console.log("=== Using for loop ===");
for (let i = 0; i < students.length; i++) {
    console.log(`${i + 1}. ${students[i]}`);
}

// For...of loop (modern way)
console.log("\n=== Using for...of loop ===");
for (let student of students) {
    console.log(`Student: ${student}`);
}

// forEach method
console.log("\n=== Using forEach method ===");
students.forEach(function(student, index) {
    console.log(`${index + 1}. ${student}`);
});

// Arrow function with forEach
students.forEach((student, index) => {
    console.log(`#${index + 1}: ${student}`);
});
```

### Array with Functions

```javascript
function analyzeScores(scores) {
    let total = 0;
    let highest = scores[0];
    let lowest = scores[0];
    
    for (let score of scores) {
        total += score;
        if (score > highest) highest = score;
        if (score < lowest) lowest = score;
    }
    
    return {
        average: total / scores.length,
        highest: highest,
        lowest: lowest,
        total: total
    };
}

let testScores = [85, 92, 78, 96, 87, 91];
let analysis = analyzeScores(testScores);

console.log("=== Score Analysis ===");
console.log(`Scores: ${testScores.join(", ")}`);
console.log(`Average: ${analysis.average.toFixed(1)}`);
console.log(`Highest: ${analysis.highest}`);
console.log(`Lowest: ${analysis.lowest}`);
console.log(`Total: ${analysis.total}`);
```

---

## Mini Project: Student Grade Manager

Let's combine everything we learned to create a student grade management system!

```javascript
// Student Grade Manager
let students = [];

// Function to add a student
function addStudent(name, ...grades) {
    const student = {
        name: name,
        grades: grades,
        average: calculateAverage(grades),
        letterGrade: ""
    };
    
    student.letterGrade = getLetterGrade(student.average);
    students.push(student);
    
    console.log(`✅ Added ${name} with average ${student.average.toFixed(1)} (${student.letterGrade})`);
}

// Function to calculate average
function calculateAverage(grades) {
    let sum = 0;
    for (let grade of grades) {
        sum += grade;
    }
    return sum / grades.length;
}

// Function to get letter grade
function getLetterGrade(average) {
    if (average >= 90) return "A";
    if (average >= 80) return "B";
    if (average >= 70) return "C";
    if (average >= 60) return "D";
    return "F";
}

// Function to display all students
function displayAllStudents() {
    console.log("\n=== CLASS ROSTER ===");
    if (students.length === 0) {
        console.log("No students enrolled yet.");
        return;
    }
    
    for (let i = 0; i < students.length; i++) {
        const student = students[i];
        console.log(`${i + 1}. ${student.name}`);
        console.log(`   Grades: ${student.grades.join(", ")}`);
        console.log(`   Average: ${student.average.toFixed(1)} (${student.letterGrade})`);
        console.log("");
    }
}

// Function to find top student
function findTopStudent() {
    if (students.length === 0) return null;
    
    let topStudent = students[0];
    for (let student of students) {
        if (student.average > topStudent.average) {
            topStudent = student;
        }
    }
    return topStudent;
}

// Function to get class statistics
function getClassStatistics() {
    if (students.length === 0) {
        console.log("No students to analyze.");
        return;
    }
    
    let totalAverage = 0;
    let gradeCount = { A: 0, B: 0, C: 0, D: 0, F: 0 };
    
    for (let student of students) {
        totalAverage += student.average;
        gradeCount[student.letterGrade]++;
    }
    
    console.log("\n=== CLASS STATISTICS ===");
    console.log(`Total Students: ${students.length}`);
    console.log(`Class Average: ${(totalAverage / students.length).toFixed(1)}`);
    console.log("Grade Distribution:");
    for (let grade in gradeCount) {
        console.log(`  ${grade}: ${gradeCount[grade]} students`);
    }
    
    const topStudent = findTopStudent();
    console.log(`🏆 Top Student: ${topStudent.name} (${topStudent.average.toFixed(1)})`);
}

// Add some students
addStudent("Alice Johnson", 95, 88, 92, 90);
addStudent("Bob Smith", 78, 82, 85, 80);
addStudent("Charlie Brown", 92, 95, 89, 94);
addStudent("Diana Prince", 88, 91, 87, 90);

// Display results
displayAllStudents();
getClassStatistics();
```

---

## Practice Challenges

### Challenge 1: Number Guessing Game

```javascript
function numberGuessingGame() {
    const secretNumber = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;
    const maxAttempts = 7;
    
    console.log("🎯 Welcome to the Number Guessing Game!");
    console.log("I'm thinking of a number between 1 and 100");
    console.log(`You have ${maxAttempts} attempts to guess it!`);
    
    // Simulate guesses for demonstration
    const guesses = [50, 75, 62, 68, 71, 69, 70];
    
    for (let guess of guesses) {
        attempts++;
        console.log(`\nAttempt ${attempts}: You guessed ${guess}`);
        
        if (guess === secretNumber) {
            console.log("🎉 Congratulations! You found the number!");
            console.log(`You won in ${attempts} attempts!`);
            break;
        } else if (guess < secretNumber) {
            console.log("📈 Too low! Try a higher number.");
        } else {
            console.log("📉 Too high! Try a lower number.");
        }
        
        if (attempts >= maxAttempts) {
            console.log(`\n😞 Game over! The number was ${secretNumber}`);
            break;
        }
    }
}

// Run the game
numberGuessingGame();
```

### Challenge 2: Simple Calculator

```javascript
function calculator(num1, operator, num2) {
    let result;
    
    switch (operator) {
        case "+":
            result = num1 + num2;
            break;
        case "-":
            result = num1 - num2;
            break;
        case "*":
            result = num1 * num2;
            break;
        case "/":
            if (num2 === 0) {
                return "Error: Cannot divide by zero!";
            }
            result = num1 / num2;
            break;
        case "**":
            result = num1 ** num2;
            break;
        default:
            return "Error: Invalid operator!";
    }
    
    return `${num1} ${operator} ${num2} = ${result}`;
}

// Test the calculator
console.log("=== CALCULATOR TESTS ===");
console.log(calculator(10, "+", 5));
console.log(calculator(10, "-", 3));
console.log(calculator(6, "*", 4));
console.log(calculator(15, "/", 3));
console.log(calculator(2, "**", 8));
console.log(calculator(10, "/", 0));
console.log(calculator(5, "%", 2));
```

---

## Remember This

> "Functions are the building blocks of larger programs. Master them, and you'll be able to solve complex problems by breaking them into smaller, manageable pieces." 🧩

---

## Task (Essential Practice)

Create a **Personal Budget Tracker** that includes:

1. **Variables** for monthly income and expenses
2. **Functions** to calculate budget summary
3. **Arrays** to store expense categories and amounts
4. **Control structures** to provide budget advice
5. **Loops** to process all expenses

```javascript
// Starter code - complete this program
const monthlyIncome = 3000;

// Two separate arrays for expense categories and amounts
const expenseCategories = ["Rent", "Food", "Transportation", "Utilities", "Entertainment"];
const expenseAmounts = [1200, 400, 200, 150, 300];

// TODO: Create functions to:
// 1. Calculate total expenses using a loop
// 2. Calculate remaining budget (income - total expenses)
// 3. Find the highest expense category and amount
// 4. Provide budget advice based on remaining money
// 5. Display a complete budget report

// Your solution here...
```

**Requirements:**

- Use a loop to calculate total expenses from the expenseAmounts array
- Use if-else statements to provide different advice based on budget status
- Use functions to organize your code
- Display results in a user-friendly format with category names and amounts
- Handle the case where expenses exceed income

**Bonus:** Add a function that suggests which expense category to reduce if the budget is negative!
