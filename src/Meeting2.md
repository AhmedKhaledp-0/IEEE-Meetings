# IEEE FrontEnd committee: Second Lecture

## 1 Wrap-up of the Last Meeting

In our previous meeting, we covered:

- **HTML Basics and Structure**
- **Commonly Used Tags and Their Purpose**
- **Introduction to Forms and Input Types**
- **Semantic HTML and Its Importance**

## 2 Challenges and Questions Raised

- **Understanding the difference between block and inline elements.**
- **When to use `div` vs semantic elements like `section` or `article`.**
- **Best practices for structuring forms and handling user input.**
- **Using VS Code shortcuts effectively to improve coding speed.**

## 3 Pending Discussions and Improvements

- **Deep dive into HTML Forms and Input Types.**
- **Advanced Semantic Elements and their usage.**
- **More real-world examples of well-structured web pages.**
- **Setting up a small project to practice front-end development concepts.**

Today, we will build on that foundation and dive deeper into essential front-end concepts.

---

## Semantic HTML & Forms

### What is Semantic HTML?

> SEO topic

Semantic HTML refers to using **meaningful** HTML elements that describe their purpose, making web pages more accessible and easier to understand.

### Why Use Semantic HTML?

- Improves **SEO** (Search Engine Optimization).
- Enhances **accessibility** for screen readers.
- Provides better **code readability** and structure.

### Common Semantic Elements

| Element     | Purpose                                          |
| ----------- | ------------------------------------------------ |
| `<header>`  | Defines the header section of a webpage          |
| `<nav>`     | Contains navigation links                        |
| `<section>` | Represents a standalone section                  |
| `<article>` | Represents independent content (e.g., blog post) |
| `<aside>`   | Used for sidebars, additional info               |
| `<footer>`  | Defines the footer section                       |

### Example of Semantic HTML page

```html
<header>
  <h1>Welcome to My Website</h1>
</header>
<nav>
  <ul>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
<section id="about">
  <h2>About Us</h2>
  <p>We build amazing web applications.</p>
</section>
<footer>
  <p>&copy; 2025 My Website</p>
</footer>
```

---

## HTML Forms & Inputs

### What is an HTML Form?

An HTML form collects user input and sends it to a server for processing.

### Basic Form Structure

```html
<form action="/submit" method="POST">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required />

  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="4"></textarea>

  <button type="submit">Submit</button>
</form>
```

### Explanation of Form Elements

| Element      | Purpose                                          |
| ------------ | ------------------------------------------------ |
| `<form>`     | Container for input elements                     |
| `<input>`    | Accepts user input (text, email, password, etc.) |
| `<textarea>` | Allows multiline text input                      |
| `<button>`   | Submits the form                                 |
| `<label>`    | Associates text with an input field              |

### Input Types

| Type       | Purpose                                 |
| ---------- | --------------------------------------- |
| `text`     | Single-line text input                  |
| `email`    | Email validation input                  |
| `password` | Hides user input for passwords          |
| `number`   | Accepts numerical values                |
| `radio`    | Select one option from multiple choices |
| `checkbox` | Select multiple options                 |
| `date`     | Select a date                           |
| `file`     | Upload a file                           |

### Example: Form with Various Input Types

```html
<form>
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required />

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required />

  <label>Gender:</label>
  <input type="radio" id="male" name="gender" value="male" />
  <label for="male">Male</label>
  <input type="radio" id="female" name="gender" value="female" />
  <label for="female">Female</label>

  <label for="hobbies">Hobbies:</label>
  <input type="checkbox" id="sports" name="hobbies" value="sports" />
  <label for="sports">Sports</label>
  <input type="checkbox" id="music" name="hobbies" value="music" />
  <label for="music">Music</label>

  <label for="dob">Date of Birth:</label>
  <input type="date" id="dob" name="dob" />

  <button type="submit">Register</button>
</form>
```

---

## Deep Dive into HTML Forms

### Form Validation (Client-Side)

HTML provides built-in validation for form fields to ensure users enter correct data.

Example of validation using `required`, `minlength`, and `pattern`:

```html
<input type="text" name="username" required minlength="4" />
<input type="email" name="email" required />
<input type="password" name="password" required pattern=".{6,}" />
```

### Accessibility in Forms

- Use **`<label>`** for all input fields.
- Use **`aria-label`** or **`aria-describedby`** for better screen reader support.

---

## Comments & VS Code Keyboard Shortcuts

### **How to Use Comments?**

- Comments improve readability and explain complex code.
- In HTML:

```html
<!-- This is a comment -->
```

### **VS Code Keyboard Shortcuts**

| Shortcut              | Function               |
| --------------------- | ---------------------- |
| `Ctrl + /`            | Toggle comments        |
| `Ctrl + D`            | Select next occurrence |
| `Alt + Shift + ↓ / ↑` | Duplicate line         |
| `Ctrl + P`            | Quick file open        |
| `Ctrl + Shift + X`    | Open extensions menu   |

---

## Real-World Web Page Examples

## Discussing Offline Meetings & Upcoming Tasks

- **Should we schedule in-person meetups?**
- **Assigning tasks for members:**
  - Build a semantic webpage.
  - Create a form with validation.

---

## Task

Make a Wep page that contain:

- A Good structure `HTML` page that follow the semantic tags and the comments
- A form with all inputs types.
- A submit button with a `reset` button.

---

## Wrap-Up

### Key Takeaways

- **Semantic HTML improves accessibility and SEO.**
- **Forms allow users to input and submit data.**
- **Different input types serve different purposes.**
- **Validation helps maintain data quality.**
- Important Links
  - [HTML Forms Guide](https://developer.mozilla.org/en-US/docs/Learn/Forms)
  - [VS Code Shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

### Next Steps

- In the next session, we will explore **Accessibility, media embedding**.
