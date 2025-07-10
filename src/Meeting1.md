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

### Task: Create your First WebPage

#### Objective

Create a webpage that demonstrates your understanding of essential HTML elements and basic webpage structure.

#### Requirements

Create an HTML file named `index.html` that includes:

1. A proper HTML document structure:
   - `<!DOCTYPE>`
   - `<html>`
   - `<head>`
   - `<body>`
2. A title for your webpage
3. At least two different levels of headings
4. A paragraph about your favorite hobby
5. An unordered list of your top 3 favorite foods
6. An ordered list of your daily routine (at least 3 items)
7. An image (you can use any appropriate image)
8. A link to your favorite website

#### Bonus

- Search for Semantic HTML tags and use them

---

## Wrap-Up

### Key Takeaways

- **Web development = Front-end + Back-end.**
- **Front-end uses HTML, CSS, and JavaScript.**
- **HTML is the foundation of every webpage.**

### Next Steps

- In the next session, we will explore **Semantic HTML** and **Form**
