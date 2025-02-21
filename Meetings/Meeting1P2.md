# IEEE FrontEnd committee: First Lecture Part 2 : HTML Tags Documentation

## Table of Contents

- [IEEE FrontEnd committee: First Lecture Part 2 : HTML Tags Documentation](#ieee-frontend-committee-first-lecture-part-2--html-tags-documentation)
  - [Table of Contents](#table-of-contents)
  - [Text Formatting](#text-formatting)
  - [Lists](#lists)
  - [Tables](#tables)
  - [Forms](#forms)
  - [Media](#media)
  - [Semantic Elements](#semantic-elements)
  - [Interactive Elements](#interactive-elements)

## Text Formatting

| Tag            | Inline/Block | Description                                             | Important Attributes   |
| -------------- | ------------ | ------------------------------------------------------- | ---------------------- |
| `<p>`          | Block        | Defines a paragraph                                     | -                      |
| `<strong>`     | Inline       | Makes text bold                                         | -                      |
| `<em>`         | Inline       | Emphasizes text (italic)                                | -                      |
| `<mark>`       | Inline       | Highlights text                                         | -                      |
| `<sup>`        | Inline       | Superscript text                                        | -                      |
| `<sub>`        | Inline       | Subscript text                                          | -                      |
| `<blockquote>` | Block        | Represents a block of quoted text                       | -                      |
| `<pre>`        | Block        | Preformatted text with preserved spaces and line breaks | -                      |
| `<abbr>`       | Inline       | Represents an abbreviation                              | `title` (tooltip text) |
| `<cite>`       | Inline       | Represents the title of a work                          | -                      |
| `<code>`       | Inline       | Represents inline code snippets                         | -                      |

## Lists

| Tag    | Inline/Block | Description                       | Important Attributes   |
| ------ | ------------ | --------------------------------- | ---------------------- |
| `<ul>` | Block        | Unordered list                    | -                      |
| `<ol>` | Block        | Ordered list                      | `type` (1, a, A, i, I) |
| `<li>` | Block        | List item inside `<ul>` or `<ol>` | -                      |

## Tables

| Tag       | Inline/Block | Description                        | Important Attributes          |
| --------- | ------------ | ---------------------------------- | ----------------------------- |
| `<table>` | Block        | Defines a table                    | `border` (for border display) |
| `<tr>`    | Block        | Defines a row in a table           | -                             |
| `<th>`    | Block        | Defines a header cell in a table   | `colspan`, `rowspan`          |
| `<td>`    | Block        | Defines a standard cell in a table | `colspan`, `rowspan`          |

## Forms

| Tag          | Inline/Block | Description                     | Important Attributes          |
| ------------ | ------------ | ------------------------------- | ----------------------------- |
| `<form>`     | Block        | Defines an HTML form            | `action`, `method`            |
| `<input>`    | Inline       | Defines an input field          | `type`, `name`, `placeholder` |
| `<textarea>` | Block        | Defines a multi-line text input | `rows`, `cols`                |
| `<button>`   | Inline       | Defines a clickable button      | `type`                        |

## Media

| Tag        | Inline/Block | Description                              | Important Attributes            |
| ---------- | ------------ | ---------------------------------------- | ------------------------------- |
| `<img>`    | Inline       | Embeds an image                          | `src`, `alt`, `width`, `height` |
| `<audio>`  | Block        | Embeds audio content                     | `controls`, `src`               |
| `<video>`  | Block        | Embeds video content                     | `controls`, `width`, `height`   |
| `<canvas>` | Block        | Used for drawing graphics via JavaScript | `width`, `height`               |

## Semantic Elements

| Tag            | Inline/Block | Description                                 | Important Attributes |
| -------------- | ------------ | ------------------------------------------- | -------------------- |
| `<article>`    | Block        | Represents independent content              | -                    |
| `<aside>`      | Block        | Defines content aside from the main content | -                    |
| `<figure>`     | Block        | Groups media elements                       | -                    |
| `<figcaption>` | Inline       | Provides a caption for `<figure>`           | -                    |

## Interactive Elements

| Tag          | Inline/Block | Description                                    | Important Attributes  |
| ------------ | ------------ | ---------------------------------------------- | --------------------- |
| `<details>`  | Block        | Creates an expandable section                  | -                     |
| `<summary>`  | Inline       | Provides a summary for `<details>`             | -                     |
| `<progress>` | Inline       | Represents a progress bar                      | `value`, `max`        |
| `<meter>`    | Inline       | Represents a scalar measurement within a range | `value`, `min`, `max` |

> Not all the tags will be Shown in today meetings like the rest of **Semantic Elements** and **input types**
