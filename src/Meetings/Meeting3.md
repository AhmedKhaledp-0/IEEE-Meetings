# Lecture 3: Web Accessibility

## 1. Key Accessibility Concepts

### Alternative Text (alt)

- The `alt` attribute provides alternative text for images, improving screen reader accessibility.
- If an image is purely decorative, an empty `alt=""` can be used.

### ARIA Labels & Descriptions

- `aria-label` and `aria-describedby` enhance accessibility by providing additional descriptions for elements.
- Useful for buttons, icons, and interactive elements that lack visible labels.

### Contrast

- Sufficient contrast between text and background is necessary for readability.
- Tools like WebAIM contrast checker can help ensure compliance with WCAG standards.

### Semantic HTML

- Using correct HTML elements (`<header>`, `<nav>`, `<article>`, `<section>`, `<footer>`, etc.) improves screen reader navigation.
- Avoid unnecessary `<div>` elements when semantic tags are available.

### Headings

- Proper use of `<h1>` to `<h6>` creates a logical document structure.
- Avoid skipping heading levels (e.g., jumping from `<h1>` to `<h3>`).

### Language Attribute in HTML

- Use the `lang` attribute to specify the document language. Example: `<html lang="en">`.
- Accessibility guidelines for content:
  - Use **short, clear sentences**.
  - **Avoid excessive symbols** that may confuse screen readers.
  - Maintain **formal and professional language**.

### Good Link Text

- Use descriptive text for links instead of generic terms like "Click here."
- Example:
  - **Bad:** `<a href="docs.pdf">Click here</a>`
  - **Good:** `<a href="docs.pdf">Download the documentation</a>`

### Tables and Accessibility

- Use `<th>` for table headers and `<caption>` for descriptions.
- Use lists (`<ol>`, `<ul>`, `<li>`, `<p>`) where possible instead of tables.
- **Avoid using tables for layout** – use **CSS Grid or Flexbox** instead.
- Use `scope="row"` or `scope="col"` to define relationships between table headers and data.
- Use `colspan` or `rowspan` to merge cells when needed.
- Assign `id` attributes to link cells with headers.

### Data Attributes for Accessibility

- Use `data-message` and `tabindex` to enhance accessibility.
- Example

```html
<input type="text" data-message="Enter your name" tabindex="0" />
```

### Captions & Figures

- Use `<caption>` for tables and `<figcaption>` for images.
- Example:

  ```html
  <figure>
    <img src="diagram.jpg" alt="System architecture diagram" />
    <figcaption>Diagram showing system architecture.</figcaption>
  </figure>
  ```

- Sometimes, an empty `alt=""` is acceptable for decorative images.

### Role Attribute & Media Embedding

- Use the `role` attribute to define the purpose of elements (e.g., `role="navigation"`, `role="button"`).
- Ensure media elements (`<video>` & `<audio>`) have captions, transcripts, or alternative text.

---

## Task: Create an Accessible Webpage

### Requirements

- Design a webpage that follows all accessibility best practices covered in this lecture.
- Ensure proper use of:
  - Semantic HTML elements
  - `alt` attributes for images
  - ARIA attributes where necessary
  - Contrast and readable fonts
  - Accessible tables and forms
  - Properly structured headings
  - Captions for media

### Hint

- Use the **WAVE Accessibility Evaluation Tool** or **Lighthouse in Chrome DevTools** to test your webpage.
- Validate your HTML using [W3C Validator](https://validator.w3.org/).

## Bonus

> Search for Virion control and the difference between `git` and `gitHub`
