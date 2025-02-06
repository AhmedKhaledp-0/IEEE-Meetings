# IEEE FrontEnd committee: First Lecture

## Introduction to Web Development

### What is Web Development?

Web development is the process of **building websites and web applications** that people use daily, like Google, YouTube, and Amazon.

### The Two Main Parts of Web Development

1. **Front-End (Client-Side)** → What users see and interact with (UI/UX).
2. **Back-End (Server-Side)** → Manages data, databases, and server operations.

**Analogy:**

- Think of a website as a **car**:
  - **Front-End** = The car's **dashboard, design, and controls** (what you see and interact with).
  - **Back-End** = The **engine and mechanics** (how it works behind the scenes).

---

## What is Front-End Development?

Front-end developers **create the user interface (UI) and experience (UX)** using three main technologies:

| Technology                           | Purpose                      |
| ------------------------------------ | ---------------------------- |
| **HTML** (HyperText Markup Language) | Structure of a webpage       |
| **CSS** (Cascading Style Sheets)     | Styling and layout           |
| **JavaScript**                       | Adds interactivity and logic |

### Example

- When you open **Google.com**:
  - **HTML** creates the search bar and buttons.
  - **CSS** makes it look nice.
  - **JavaScript** makes the search function work.

---

## Overview of IDEs & Environment Setup

### What is an IDE?

An **IDE (Integrated Development Environment)** is a tool where developers write and edit code. Popular choices:

- **VS Code** (Recommended)
- WebStorm
- Sublime Text

### Setting Up VS Code for Web Development

1. Download and install **VS Code** from [https://code.visualstudio.com/](https://code.visualstudio.com/).
2. Install extensions:
   - **Live Server** → Auto-refresh your webpage.
   - **Prettier** → Auto-format your code.
3. Create a new project folder and open it in VS Code.
4. Create a new file: `index.html`.

---

## Basic HTML Structure

**HTML (HyperText Markup Language)** provides the **foundation** of any webpage. It consists of elements enclosed in tags (`<>`).

### Basic Structure of an HTML Document

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My First Webpage</title>
  </head>
  <body>
    <h1>Welcome to Web Development</h1>
    <p>This is a basic webpage structure.</p>
    <a href="#" target="_blank">Visit IEEE</a>
    <button onclick="alert('Hello!')">Click Me</button>
  </body>
</html>
```

### Explanation

- `<html>` → The entire webpage.
- `<head>` → Metadata (title, character set, etc.).
- `<body>` → The visible content.
- `<h1>` → Heading.
- `<p>` → Paragraph.
- `<a>` → Hyperlink.
- `<button>` → Interactive button.

---

## Hands-On Challenge

### Task

Modify the given HTML file by adding:

- A second heading (`<h2>`) with any text.
- A list (`<ul>` or `<ol>`) with at least three items.
- An image (`<img>` tag) with a valid URL.

**Example Solution:**

```html
<h2>Why Learn Front-End Development?</h2>
<ul>
  <li>It is fun and creative!</li>
  <li>It is in high demand.</li>
  <li>It helps you build real-world projects.</li>
</ul>
<img src="https://via.placeholder.com/150" alt="Placeholder Image" />
```

---

## Wrap-Up

### Key Takeaways

- **Web development = Front-end + Back-end.**
- **Front-end uses HTML, CSS, and JavaScript.**
- **HTML is the foundation of every webpage.**

### Next Steps

- In the next session, we will explore **Semantic HTML** and **Form**
