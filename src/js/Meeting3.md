# JavaScript Third Lecture: Objects, DOM Manipulation, and Events

## What We'll Learn Today

- Objects: Storing related data together
- DOM Manipulation: Making web pages interactive
- Event Handling: Responding to user actions
- Local Storage: Remembering user data
- Building a complete interactive web application

---

## Objects: Organizing Related Data

Objects are collections of related properties and methods. They help us organize data that belongs together.

### Creating Objects

```javascript
// Object literal notation
let student = {
    name: "Sarah",
    age: 20,
    major: "Computer Science",
    gpa: 3.8,
    isEnrolled: true
};

// Accessing object properties
console.log("Student name: " + student.name);
console.log("Student age: " + student.age);
console.log("GPA: " + student.gpa);

// Dot notation vs bracket notation
console.log(student.major);        // Dot notation
console.log(student["major"]);     // Bracket notation (useful for dynamic properties)
```

### Adding and Modifying Properties

```javascript
let car = {
    brand: "Toyota",
    model: "Camry",
    year: 2022
};

// Adding new properties
car.color = "blue";
car.mileage = 15000;

// Modifying existing properties
car.year = 2023;
car.mileage += 5000;

console.log("=== Car Information ===");
console.log(`Brand: ${car.brand}`);
console.log(`Model: ${car.model}`);
console.log(`Year: ${car.year}`);
console.log(`Color: ${car.color}`);
console.log(`Mileage: ${car.mileage} miles`);
```

### Objects with Methods

```javascript
let calculator = {
    // Properties
    brand: "Scientific Calculator",
    version: "1.0",
    
    // Methods (functions inside objects)
    add: function(a, b) {
        return a + b;
    },
    
    subtract: function(a, b) {
        return a - b;
    },
    
    multiply: function(a, b) {
        return a * b;
    },
    
    divide: function(a, b) {
        if (b === 0) {
            return "Error: Cannot divide by zero!";
        }
        return a / b;
    },
    
    // Method using arrow function
    power: (a, b) => {
        return Math.pow(a, b);
    }
};

// Using object methods
console.log("=== Calculator Tests ===");
console.log(`5 + 3 = ${calculator.add(5, 3)}`);
console.log(`10 - 4 = ${calculator.subtract(10, 4)}`);
console.log(`6 * 7 = ${calculator.multiply(6, 7)}`);
console.log(`15 / 3 = ${calculator.divide(15, 3)}`);
console.log(`2^8 = ${calculator.power(2, 8)}`);
```

### Real-World Object Examples

```javascript
// Game player object
let player = {
    username: "GamerPro123",
    level: 15,
    health: 100,
    score: 2500,
    inventory: ["sword", "shield", "potion"],
    
    // Method to take damage
    takeDamage: function(damage) {
        this.health -= damage;
        if (this.health < 0) this.health = 0;
        console.log(`${this.username} took ${damage} damage. Health: ${this.health}`);
    },
    
    // Method to gain experience
    gainExp: function(exp) {
        this.score += exp;
        console.log(`${this.username} gained ${exp} experience. Total score: ${this.score}`);
    },
    
    // Method to add item to inventory
    addItem: function(item) {
        this.inventory.push(item);
        console.log(`${this.username} found ${item}! Inventory: ${this.inventory.join(", ")}`);
    }
};

// Using player methods
player.takeDamage(25);
player.gainExp(100);
player.addItem("magic ring");

// Bank account object
let bankAccount = {
    accountNumber: "12345678",
    ownerName: "John Smith",
    balance: 1000.00,
    accountType: "Checking",
    
    deposit: function(amount) {
        if (amount > 0) {
            this.balance += amount;
            console.log(`✅ Deposited $${amount}. New balance: $${this.balance.toFixed(2)}`);
        } else {
            console.log("❌ Invalid deposit amount");
        }
    },
    
    withdraw: function(amount) {
        if (amount > 0 && amount <= this.balance) {
            this.balance -= amount;
            console.log(`✅ Withdrew $${amount}. New balance: $${this.balance.toFixed(2)}`);
        } else if (amount > this.balance) {
            console.log("❌ Insufficient funds");
        } else {
            console.log("❌ Invalid withdrawal amount");
        }
    },
    
    checkBalance: function() {
        console.log(`💰 Account balance: $${this.balance.toFixed(2)}`);
        return this.balance;
    }
};

// Banking operations
console.log("\n=== Banking Operations ===");
bankAccount.checkBalance();
bankAccount.deposit(250);
bankAccount.withdraw(100);
bankAccount.withdraw(2000); // Should fail
```

---

## DOM Manipulation: Making Web Pages Interactive

The Document Object Model (DOM) allows JavaScript to interact with HTML elements.

### Selecting HTML Elements

```javascript
// HTML structure we're working with:
/*
<div id="container">
    <h1 id="title">Welcome to My Website</h1>
    <p class="description">This is a paragraph</p>
    <button id="changeButton">Click Me!</button>
    <ul id="itemList">
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
</div>
*/

// Selecting elements by ID
let title = document.getElementById("title");
let button = document.getElementById("changeButton");
let container = document.getElementById("container");

// Selecting elements by class name
let description = document.getElementsByClassName("description")[0];

// Selecting elements by tag name
let paragraphs = document.getElementsByTagName("p");

// Modern selectors (recommended)
let titleModern = document.querySelector("#title");           // ID selector
let descModern = document.querySelector(".description");     // Class selector
let firstLi = document.querySelector("li");                  // First li element
let allLis = document.querySelectorAll("li");               // All li elements

console.log("Title element:", title);
console.log("All list items:", allLis);
```

### Changing Content and Styles

```javascript
// Changing text content
title.textContent = "Welcome to JavaScript DOM!";

// Changing HTML content
description.innerHTML = "<strong>This text is now bold!</strong>";

// Changing styles
title.style.color = "blue";
title.style.fontSize = "36px";
title.style.textAlign = "center";

// Adding CSS classes
description.classList.add("highlight");
description.classList.add("important");

// Removing CSS classes
description.classList.remove("old-style");

// Toggling CSS classes
button.classList.toggle("active");

// Changing attributes
button.setAttribute("disabled", "true");
button.removeAttribute("disabled");

// Working with form inputs
/*
<input type="text" id="nameInput" placeholder="Enter your name">
<input type="number" id="ageInput" placeholder="Enter your age">
*/

let nameInput = document.querySelector("#nameInput");
let ageInput = document.querySelector("#ageInput");

// Getting input values
let userName = nameInput.value;
let userAge = parseInt(ageInput.value);

// Setting input values
nameInput.value = "John Doe";
ageInput.value = 25;
```

### Creating and Adding Elements

```javascript
// Creating new elements
let newParagraph = document.createElement("p");
newParagraph.textContent = "This paragraph was created with JavaScript!";
newParagraph.style.color = "green";

// Adding elements to the page
container.appendChild(newParagraph);

// Creating a list item and adding to existing list
let itemList = document.querySelector("#itemList");
let newItem = document.createElement("li");
newItem.textContent = "Item 3 (Added by JavaScript)";
itemList.appendChild(newItem);

// Creating a more complex element
let infoDiv = document.createElement("div");
infoDiv.innerHTML = `
    <h3>Dynamic Content</h3>
    <p>This entire section was created with JavaScript!</p>
    <button onclick="alert('Hello from dynamic button!')">Dynamic Button</button>
`;
infoDiv.style.border = "2px solid #333";
infoDiv.style.padding = "10px";
infoDiv.style.margin = "10px 0";

container.appendChild(infoDiv);
```

---

## Event Handling: Responding to User Actions

Events allow your JavaScript to respond to user interactions like clicks, key presses, and form submissions.

### Basic Event Handling

```javascript
// Method 1: Using onclick property
let clickButton = document.querySelector("#changeButton");
clickButton.onclick = function() {
    alert("Button was clicked!");
};

// Method 2: Using addEventListener (recommended)
clickButton.addEventListener("click", function() {
    console.log("Button clicked with addEventListener!");
});

// Method 3: Arrow function with addEventListener
clickButton.addEventListener("click", () => {
    title.style.color = title.style.color === "red" ? "blue" : "red";
});
```

### Different Types of Events

```javascript
// Click events
button.addEventListener("click", function() {
    console.log("Button clicked!");
});

// Mouse events
button.addEventListener("mouseenter", function() {
    button.style.backgroundColor = "lightblue";
});

button.addEventListener("mouseleave", function() {
    button.style.backgroundColor = "";
});

// Keyboard events
let textInput = document.querySelector("#nameInput");

textInput.addEventListener("keydown", function(event) {
    console.log("Key pressed:", event.key);
});

textInput.addEventListener("keyup", function(event) {
    let inputValue = event.target.value;
    console.log("Current input:", inputValue);
});

// Form events
let form = document.querySelector("#userForm");

form.addEventListener("submit", function(event) {
    event.preventDefault(); // Prevent page refresh
    
    let name = nameInput.value;
    let age = ageInput.value;
    
    if (name === "" || age === "") {
        alert("Please fill in all fields!");
        return;
    }
    
    console.log(`Form submitted - Name: ${name}, Age: ${age}`);
});

// Window events
window.addEventListener("load", function() {
    console.log("Page fully loaded!");
});

window.addEventListener("resize", function() {
    console.log("Window resized to:", window.innerWidth, "x", window.innerHeight);
});
```

### Interactive Examples

```javascript
// Color changer
let colorButtons = document.querySelectorAll(".color-btn");
let colorBox = document.querySelector("#colorBox");

colorButtons.forEach(function(button) {
    button.addEventListener("click", function() {
        let color = button.dataset.color; // Get data-color attribute
        colorBox.style.backgroundColor = color;
        colorBox.textContent = `Color: ${color}`;
    });
});

// Counter application
let counter = 0;
let counterDisplay = document.querySelector("#counterDisplay");
let incrementBtn = document.querySelector("#incrementBtn");
let decrementBtn = document.querySelector("#decrementBtn");
let resetBtn = document.querySelector("#resetBtn");

function updateDisplay() {
    counterDisplay.textContent = counter;
    counterDisplay.style.color = counter > 0 ? "green" : counter < 0 ? "red" : "black";
}

incrementBtn.addEventListener("click", function() {
    counter++;
    updateDisplay();
});

decrementBtn.addEventListener("click", function() {
    counter--;
    updateDisplay();
});

resetBtn.addEventListener("click", function() {
    counter = 0;
    updateDisplay();
});

// Initialize display
updateDisplay();
```

---

## Local Storage: Remembering User Data

Local Storage allows you to save data in the user's browser that persists between sessions.

### Basic Local Storage Operations

```javascript
// Saving data to local storage
localStorage.setItem("userName", "John Doe");
localStorage.setItem("userAge", "25");
localStorage.setItem("userScore", "1500");

// Getting data from local storage
let savedName = localStorage.getItem("userName");
let savedAge = localStorage.getItem("userAge");
let savedScore = localStorage.getItem("userScore");

console.log("Saved name:", savedName);
console.log("Saved age:", savedAge);
console.log("Saved score:", savedScore);

// Removing specific item
localStorage.removeItem("userAge");

// Clearing all local storage
// localStorage.clear(); // Uncomment to clear all data

// Checking if item exists
if (localStorage.getItem("userName") !== null) {
    console.log("User name is saved");
} else {
    console.log("User name not found");
}
```

### Saving Complex Data

```javascript
// Saving objects and arrays (convert to JSON)
let userPreferences = {
    theme: "dark",
    language: "English",
    notifications: true,
    volume: 75
};

let favoriteColors = ["blue", "green", "purple"];

// Save object as JSON string
localStorage.setItem("userPreferences", JSON.stringify(userPreferences));
localStorage.setItem("favoriteColors", JSON.stringify(favoriteColors));

// Retrieve and parse JSON data
let savedPreferences = JSON.parse(localStorage.getItem("userPreferences"));
let savedColors = JSON.parse(localStorage.getItem("favoriteColors"));

console.log("Saved preferences:", savedPreferences);
console.log("Saved colors:", savedColors);

// Safe JSON parsing with error handling
function getStoredData(key) {
    try {
        let data = localStorage.getItem(key);
        return data ? JSON.parse(data) : null;
    } catch (error) {
        console.error("Error parsing stored data:", error);
        return null;
    }
}

let preferences = getStoredData("userPreferences");
if (preferences) {
    console.log("Theme:", preferences.theme);
    console.log("Language:", preferences.language);
}
```

---

## Mini Project: Interactive To-Do List

Let's combine everything we learned to create a complete to-do list application!

```javascript
// To-Do List Application
let todoApp = {
    tasks: [],
    
    // Load tasks from local storage
    loadTasks: function() {
        let savedTasks = localStorage.getItem("todoTasks");
        if (savedTasks) {
            this.tasks = JSON.parse(savedTasks);
        }
        this.displayTasks();
    },
    
    // Save tasks to local storage
    saveTasks: function() {
        localStorage.setItem("todoTasks", JSON.stringify(this.tasks));
    },
    
    // Add new task
    addTask: function(taskText) {
        if (taskText.trim() === "") {
            alert("Please enter a task!");
            return;
        }
        
        let newTask = {
            id: Date.now(), // Simple ID generation
            text: taskText,
            completed: false,
            createdAt: new Date().toLocaleDateString()
        };
        
        this.tasks.push(newTask);
        this.saveTasks();
        this.displayTasks();
        
        console.log("Task added:", newTask);
    },
    
    // Remove task
    removeTask: function(taskId) {
        this.tasks = this.tasks.filter(task => task.id !== taskId);
        this.saveTasks();
        this.displayTasks();
        console.log("Task removed:", taskId);
    },
    
    // Toggle task completion
    toggleTask: function(taskId) {
        let task = this.tasks.find(task => task.id === taskId);
        if (task) {
            task.completed = !task.completed;
            this.saveTasks();
            this.displayTasks();
            console.log("Task toggled:", task);
        }
    },
    
    // Display all tasks
    displayTasks: function() {
        let taskList = document.querySelector("#taskList");
        let taskCount = document.querySelector("#taskCount");
        
        // Clear existing tasks
        taskList.innerHTML = "";
        
        // Display each task
        this.tasks.forEach(task => {
            let taskElement = document.createElement("div");
            taskElement.className = "task-item";
            taskElement.innerHTML = `
                <div class="task-content ${task.completed ? 'completed' : ''}">
                    <input type="checkbox" ${task.completed ? 'checked' : ''} 
                           onchange="todoApp.toggleTask(${task.id})">
                    <span class="task-text">${task.text}</span>
                    <span class="task-date">${task.createdAt}</span>
                </div>
                <button class="delete-btn" onclick="todoApp.removeTask(${task.id})">
                    🗑️ Delete
                </button>
            `;
            
            taskList.appendChild(taskElement);
        });
        
        // Update task count
        let completedCount = this.tasks.filter(task => task.completed).length;
        taskCount.textContent = `Total: ${this.tasks.length} | Completed: ${completedCount}`;
    },
    
    // Clear all completed tasks
    clearCompleted: function() {
        this.tasks = this.tasks.filter(task => !task.completed);
        this.saveTasks();
        this.displayTasks();
        console.log("Completed tasks cleared");
    },
    
    // Get app statistics
    getStats: function() {
        let total = this.tasks.length;
        let completed = this.tasks.filter(task => task.completed).length;
        let pending = total - completed;
        
        return {
            total: total,
            completed: completed,
            pending: pending,
            completionRate: total > 0 ? Math.round((completed / total) * 100) : 0
        };
    }
};

// Initialize the app when page loads
document.addEventListener("DOMContentLoaded", function() {
    todoApp.loadTasks();
    
    // Add event listener for form submission
    let addTaskForm = document.querySelector("#addTaskForm");
    let taskInput = document.querySelector("#taskInput");
    
    addTaskForm.addEventListener("submit", function(event) {
        event.preventDefault();
        todoApp.addTask(taskInput.value);
        taskInput.value = ""; // Clear input
    });
    
    // Add event listener for clear completed button
    let clearBtn = document.querySelector("#clearCompleted");
    clearBtn.addEventListener("click", function() {
        if (confirm("Are you sure you want to clear all completed tasks?")) {
            todoApp.clearCompleted();
        }
    });
    
    // Display stats button
    let statsBtn = document.querySelector("#showStats");
    statsBtn.addEventListener("click", function() {
        let stats = todoApp.getStats();
        alert(`📊 Todo List Stats:
Total Tasks: ${stats.total}
Completed: ${stats.completed}
Pending: ${stats.pending}
Completion Rate: ${stats.completionRate}%`);
    });
});

// Keyboard shortcuts
document.addEventListener("keydown", function(event) {
    // Press 'n' to focus on new task input
    if (event.key === 'n' && !event.target.matches('input')) {
        let taskInput = document.querySelector("#taskInput");
        taskInput.focus();
        event.preventDefault();
    }
    
    // Press 'c' to clear completed tasks
    if (event.key === 'c' && !event.target.matches('input')) {
        todoApp.clearCompleted();
        event.preventDefault();
    }
});
```

---

## Practice Challenges

### Challenge 1: Interactive Quiz App

```javascript
let quizApp = {
    questions: [
        {
            question: "What does JavaScript stand for?",
            options: ["Java Script", "Just Script", "JavaScript", "None of the above"],
            correct: 2
        },
        {
            question: "Which symbol is used for comments in JavaScript?",
            options: ["//", "/*", "#", "Both A and B"],
            correct: 3
        },
        {
            question: "What is the correct way to declare a variable?",
            options: ["var x;", "let x;", "const x = 5;", "All of the above"],
            correct: 3
        }
    ],
    
    currentQuestion: 0,
    score: 0,
    
    startQuiz: function() {
        this.currentQuestion = 0;
        this.score = 0;
        this.displayQuestion();
    },
    
    displayQuestion: function() {
        if (this.currentQuestion >= this.questions.length) {
            this.showResults();
            return;
        }
        
        let question = this.questions[this.currentQuestion];
        let quizContainer = document.querySelector("#quizContainer");
        
        quizContainer.innerHTML = `
            <h3>Question ${this.currentQuestion + 1} of ${this.questions.length}</h3>
            <p class="question-text">${question.question}</p>
            <div class="options">
                ${question.options.map((option, index) => `
                    <button class="option-btn" onclick="quizApp.selectAnswer(${index})">
                        ${option}
                    </button>
                `).join('')}
            </div>
            <p class="score">Score: ${this.score}/${this.questions.length}</p>
        `;
    },
    
    selectAnswer: function(selectedIndex) {
        let question = this.questions[this.currentQuestion];
        
        if (selectedIndex === question.correct) {
            this.score++;
            alert("Correct! 🎉");
        } else {
            alert(`Wrong! The correct answer was: ${question.options[question.correct]}`);
        }
        
        this.currentQuestion++;
        this.displayQuestion();
    },
    
    showResults: function() {
        let percentage = Math.round((this.score / this.questions.length) * 100);
        let quizContainer = document.querySelector("#quizContainer");
        
        let grade = percentage >= 80 ? "Excellent!" : 
                   percentage >= 60 ? "Good!" : 
                   percentage >= 40 ? "Fair" : "Need more practice";
        
        quizContainer.innerHTML = `
            <h2>Quiz Complete! 🏆</h2>
            <p>Your Score: ${this.score}/${this.questions.length} (${percentage}%)</p>
            <p>Grade: ${grade}</p>
            <button onclick="quizApp.startQuiz()">Take Quiz Again</button>
        `;
        
        // Save high score
        let highScore = localStorage.getItem("quizHighScore") || 0;
        if (this.score > highScore) {
            localStorage.setItem("quizHighScore", this.score);
            alert("New high score! 🌟");
        }
    }
};
```

---

## Remember This

> "The DOM is your canvas, events are your brushes, and JavaScript is your paint. With these tools, you can create any interactive experience you can imagine!" 🎨

---

## Task (Essential Practice)

Create a **Personal Expense Tracker** that includes:

1. **Objects** to store expense data
2. **DOM manipulation** to update the interface
3. **Event handling** for user interactions
4. **Local storage** to persist data
5. **Dynamic content** creation

```html
<!-- HTML structure (add this to your HTML file) -->
<div id="expenseTracker">
    <h2>💰 Personal Expense Tracker</h2>
    
    <form id="expenseForm">
        <input type="text" id="expenseDescription" placeholder="Expense description" required>
        <input type="number" id="expenseAmount" placeholder="Amount ($)" required step="0.01">
        <select id="expenseCategory">
            <option value="food">🍕 Food</option>
            <option value="transport">🚗 Transportation</option>
            <option value="entertainment">🎬 Entertainment</option>
            <option value="utilities">⚡ Utilities</option>
            <option value="other">📦 Other</option>
        </select>
        <button type="submit">Add Expense</button>
    </form>
    
    <div id="expenseSummary"></div>
    <div id="expenseList"></div>
    <button id="clearAll">Clear All Expenses</button>
</div>
```

```javascript
// Starter code - complete this program
let expenseTracker = {
    expenses: [],
    
    // TODO: Complete these methods
    addExpense: function(description, amount, category) {
        // Create expense object with id, description, amount, category, date
        // Add to expenses array
        // Save to localStorage
        // Update display
    },
    
    removeExpense: function(expenseId) {
        // Remove expense from array by id
        // Save to localStorage
        // Update display
    },
    
    displayExpenses: function() {
        // Show all expenses in the expenseList div
        // Each expense should have description, amount, category, date, and delete button
    },
    
    calculateSummary: function() {
        // Calculate total expenses
        // Calculate expenses by category
        // Display in expenseSummary div
    },
    
    loadExpenses: function() {
        // Load expenses from localStorage
        // Update display
    },
    
    saveExpenses: function() {
        // Save expenses array to localStorage as JSON
    }
};

// TODO: Add event listeners for:
// 1. Form submission to add new expense
// 2. Clear all button
// 3. Page load to initialize the app
```

**Requirements:**

- Use objects to structure expense data (id, description, amount, category, date)
- Use DOM manipulation to create and update expense list dynamically
- Use event handling for form submission and delete buttons
- Use local storage to persist expenses between browser sessions
- Display summary statistics (total spent, spending by category)
- Add proper form validation

**Bonus Features:**

- Add expense editing functionality
- Implement expense filtering by category
- Add date range filtering
- Create visual indicators for high spending categories!
