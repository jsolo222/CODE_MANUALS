# HTML - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Document Structure](#document-structure)
4. [Basic Elements](#basic-elements)
5. [Text Elements](#text-elements)
6. [Links & Navigation](#links--navigation)
7. [Images & Media](#images--media)
8. [Lists](#lists)
9. [Tables](#tables)
10. [Forms](#forms)
11. [Semantic HTML5](#semantic-html5)
12. [Metadata & SEO](#metadata--seo)
13. [Best Practices](#best-practices)
14. [Common Patterns](#common-patterns)
15. [Resources](#resources)

---

## Introduction

### What is HTML?

HTML (HyperText Markup Language) is the standard markup language for creating web pages and web applications. HTML describes the structure of a web page semantically and provides the foundation for web content. HTML elements tell the browser how to display content and are the building blocks of all websites.

### Why Learn HTML?

HTML is valuable for:

1. **Web Foundation**: Essential for all web development
2. **Universal Language**: Works in all browsers and platforms
3. **Simple to Learn**: Easy syntax, immediate visual results
4. **Career Essential**: Required skill for web developers
5. **SEO**: Proper HTML structure improves search rankings
6. **Accessibility**: Semantic HTML improves accessibility
7. **Framework Foundation**: Understanding HTML helps with React, Vue, Angular
8. **Content Management**: Understanding HTML structure for CMS work

### Key Features

- **Markup Language**: Uses tags to define elements
- **Semantic Structure**: Elements have meaning beyond presentation
- **Platform Independent**: Works across all devices and browsers
- **Extensible**: HTML5 adds many new elements and APIs
- **Accessibility**: Semantic HTML improves screen reader support
- **SEO Friendly**: Proper structure helps search engines
- **Integration**: Works seamlessly with CSS and JavaScript

---

## Getting Started

### Creating Your First HTML File

**Basic HTML Document:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First HTML Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>Welcome to HTML.</p>
</body>
</html>
```

**Save and Open:**
1. Save file with `.html` extension (e.g., `index.html`)
2. Open in any web browser
3. View source (right-click → View Page Source) to see HTML

---

## Document Structure

### Overview

HTML documents have a specific structure that browsers interpret. Understanding the basic structure is essential for creating valid HTML pages.

### Key Concepts

- **DOCTYPE Declaration**: Tells browser HTML version
- **html Element**: Root element of HTML document
- **head Element**: Contains metadata and links
- **body Element**: Contains visible content
- **Meta Tags**: Provide metadata about the document

### HTML Document Structure

**What this demonstrates:** Basic HTML document structure.

**Code:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    <!-- Content goes here -->
    <h1>Welcome</h1>
    <p>This is a paragraph.</p>
</body>
</html>
```

**Explanation:**
- `<!DOCTYPE html>`: HTML5 document type declaration
- `<html lang="en">`: Root element with language attribute
- `<head>`: Contains metadata (not visible in page)
- `<meta charset="UTF-8">`: Character encoding
- `<meta name="viewport" ...>`: Mobile responsive viewport
- `<title>`: Page title (shown in browser tab)
- `<body>`: Contains visible content

**Key Takeaways:**
- Always include `<!DOCTYPE html>`
- Use `<html lang="...">` for language
- `<head>` for metadata, `<body>` for content
- Include viewport meta tag for responsive design

---

## Basic Elements

### Overview

HTML provides various elements for structuring content. Understanding basic elements is fundamental to HTML development.

### Key Concepts

- **Elements**: Tags that define content structure
- **Attributes**: Provide additional information
- **Nesting**: Elements can contain other elements
- **Self-Closing Tags**: Tags that don't need closing
- **Block vs Inline**: Different display behaviors

### Basic Elements

**What this demonstrates:** Common HTML elements.

**Code:**
```html
<!-- Headings -->
<h1>Heading 1 - Main Title</h1>
<h2>Heading 2 - Section</h2>
<h3>Heading 3 - Subsection</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>

<!-- Paragraphs -->
<p>This is a paragraph. Paragraphs are block-level elements.</p>
<p>This is another paragraph.</p>

<!-- Line break -->
<p>Line 1<br>Line 2</p>

<!-- Horizontal rule -->
<hr>

<!-- Comments -->
<!-- This is a comment and won't be displayed -->
```

**Explanation:**
- Headings: `<h1>` through `<h6>` (h1 is most important)
- Paragraphs: `<p>` for text blocks
- Line break: `<br>` creates new line
- Horizontal rule: `<hr>` creates thematic break
- Comments: `<!-- -->` for documentation

**Key Takeaways:**
- Use one `<h1>` per page (SEO best practice)
- Use headings in order (don't skip levels)
- `<br>` for line breaks, `<p>` for paragraphs

---

## Text Elements

### Overview

HTML provides semantic and presentational elements for text formatting. Semantic elements convey meaning, while presentational elements affect appearance.

### Key Concepts

- **Semantic Elements**: Convey meaning (strong, em)
- **Presentational Elements**: Affect appearance (b, i)
- **Text Formatting**: Bold, italic, underline, etc.
- **Semantic Text**: Quotes, citations, code, etc.
- **Accessibility**: Semantic elements help screen readers

### Text Formatting

**What this demonstrates:** Text formatting elements.

**Code:**
```html
<!-- Bold and Strong -->
<p><b>Bold text</b> (presentational)</p>
<p><strong>Strong importance</strong> (semantic)</p>

<!-- Italic and Emphasis -->
<p><i>Italic text</i> (presentational)</p>
<p><em>Emphasized text</em> (semantic)</p>

<!-- Underline -->
<p><u>Underlined text</u></p>

<!-- Strikethrough -->
<p><s>Strikethrough text</s></p>
<p><del>Deleted text</del> (semantic deletion)</p>
<p><ins>Inserted text</ins> (semantic insertion)</p>

<!-- Small -->
<p><small>Small text (fine print)</small></p>

<!-- Highlighted -->
<p><mark>Highlighted text</mark></p>

<!-- Superscript and Subscript -->
<p>E = mc<sup>2</sup> (superscript)</p>
<p>H<sub>2</sub>O (subscript)</p>

<!-- Abbreviations -->
<p><abbr title="HyperText Markup Language">HTML</abbr></p>

<!-- Code -->
<p>Use the <code>&lt;code&gt;</code> tag for inline code.</p>

<pre>
Preformatted text
    preserves    spacing
        and line breaks
</pre>

<!-- Quotes -->
<blockquote cite="https://example.com">
    This is a block quotation.
</blockquote>
<p>Einstein said, <q>Imagination is more important than knowledge.</q></p>
```

**Explanation:**
- `<strong>`: Important text (semantic, use instead of `<b>`)
- `<em>`: Emphasized text (semantic, use instead of `<i>`)
- `<mark>`: Highlighted text
- `<code>`: Inline code
- `<pre>`: Preformatted text (preserves spacing)
- `<blockquote>`: Block quotation
- `<q>`: Inline quotation
- Prefer semantic elements: `<strong>` over `<b>`, `<em>` over `<i>`

**Key Takeaways:**
- Use semantic elements (`<strong>`, `<em>`) when possible
- `<code>` for inline code, `<pre>` for code blocks
- `<blockquote>` for block quotes, `<q>` for inline quotes
- Semantic elements improve accessibility

---

## Links & Navigation

### Overview

Links connect web pages and resources. HTML provides various types of links for navigation and resource linking.

### Key Concepts

- **Anchor Tag**: `<a href="...">` creates links
- **URL Types**: Absolute, relative, anchor links
- **Link Attributes**: target, rel, download, etc.
- **Navigation**: Internal and external links
- **Security**: Use `rel="noopener noreferrer"` for external links

### Links

**What this demonstrates:** Creating links.

**Code:**
```html
<!-- External link -->
<p><a href="https://www.example.com">External link</a></p>

<!-- Open in new tab (secure) -->
<p><a href="https://www.example.com" target="_blank" rel="noopener noreferrer">
    Open in new tab
</a></p>

<!-- Internal link -->
<p><a href="about.html">Internal page link</a></p>

<!-- Anchor link (same page) -->
<p><a href="#top">Jump to top of page</a></p>

<!-- Email link -->
<p><a href="mailto:user@example.com">Send email</a></p>
<p><a href="mailto:user@example.com?subject=Hello&body=Message">
    Email with subject and body
</a></p>

<!-- Phone link -->
<p><a href="tel:+15551234567">Call us: +1 (555) 123-4567</a></p>

<!-- Download link -->
<p><a href="document.pdf" download>Download PDF</a></p>
<p><a href="document.pdf" download="my-document.pdf">
    Download with custom filename
</a></p>

<!-- Link attributes -->
<p><a href="https://example.com" 
      title="Tooltip text"
      rel="nofollow">
    Link with tooltip
</a></p>
```

**Explanation:**
- `href`: Destination URL
- `target="_blank"`: Opens in new tab
- `rel="noopener noreferrer"`: Security for external links (required with target="_blank")
- `mailto:`: Email link protocol
- `tel:`: Phone link protocol
- `download`: Triggers download instead of navigation
- `title`: Tooltip text on hover
- `rel="nofollow"`: Tells search engines not to follow

**Key Takeaways:**
- Always use `rel="noopener noreferrer"` with `target="_blank"`
- Use `mailto:` for email links
- `download` attribute triggers file download
- `title` provides tooltip text

---

## Images & Media

### Overview

Images and media elements display visual content. HTML5 provides various elements for images, audio, and video.

### Key Concepts

- **img Tag**: Displays images
- **alt Attribute**: Required for accessibility
- **Responsive Images**: srcset and sizes attributes
- **Picture Element**: Art direction for images
- **Figure Element**: Self-contained media with caption

### Images

**What this demonstrates:** Working with images.

**Code:**
```html
<!-- Basic image -->
<img src="image.jpg" 
     alt="Description of image for accessibility" 
     width="300" 
     height="200"
     loading="lazy">

<!-- Responsive image -->
<img src="small.jpg"
     srcset="small.jpg 300w,
             medium.jpg 600w,
             large.jpg 1200w"
     sizes="(max-width: 600px) 100vw,
            (max-width: 1200px) 50vw,
            33vw"
     alt="Responsive image">

<!-- Picture element (art direction) -->
<picture>
    <source media="(min-width: 1200px)" srcset="large.jpg">
    <source media="(min-width: 600px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive with art direction">
</picture>

<!-- Figure with caption -->
<figure>
    <img src="chart.jpg" alt="Sales chart for 2024">
    <figcaption>
        Figure 1: Annual sales data showing 25% growth
    </figcaption>
</figure>
```

**Explanation:**
- `src`: Image source URL
- `alt`: Alternative text (required for accessibility)
- `width`/`height`: Image dimensions
- `loading="lazy"`: Lazy loading for performance
- `srcset`: Multiple image sources for responsive design
- `sizes`: Size hints for browser
- `<picture>`: Art direction for different screen sizes
- `<figure>`: Self-contained media with `<figcaption>`

**Key Takeaways:**
- Always include `alt` attribute (accessibility)
- Use `loading="lazy"` for images below fold
- Use `srcset` and `sizes` for responsive images
- `<picture>` for art direction
- `<figure>` for images with captions

---

## Lists

### Overview

Lists organize related items. HTML provides three types of lists: unordered, ordered, and description lists.

### Key Concepts

- **Unordered Lists**: `<ul>` for bullet points
- **Ordered Lists**: `<ol>` for numbered items
- **Description Lists**: `<dl>` for term-definition pairs
- **List Items**: `<li>` for list items
- **Nested Lists**: Lists within lists

### Lists

**What this demonstrates:** Creating lists.

**Code:**
```html
<!-- Unordered list -->
<ul>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item
        <ul>
            <li>Nested item 1</li>
            <li>Nested item 2</li>
        </ul>
    </li>
    <li>Fourth item</li>
</ul>

<!-- Ordered list -->
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>

<!-- Ordered list variations -->
<ol type="A">
    <li>Type A (uppercase letters)</li>
    <li>Type A continued</li>
</ol>

<ol start="5">
    <li>Starting at 5</li>
    <li>Number 6</li>
</ol>

<ol reversed>
    <li>Countdown</li>
    <li>Reversed</li>
    <li>List</li>
</ol>

<!-- Description list -->
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
    
    <dt>JavaScript</dt>
    <dd>Programming language for web interactivity</dd>
    <dd>Not related to Java</dd>
</dl>
```

**Explanation:**
- `<ul>`: Unordered list (bullet points)
- `<ol>`: Ordered list (numbered)
- `<li>`: List item
- `type`: Letter/number type for ordered lists (A, a, I, i, 1)
- `start`: Starting number for ordered list
- `reversed`: Reverse numbering
- `<dl>`: Description list
- `<dt>`: Term in description list
- `<dd>`: Definition in description list
- Nested: Lists can contain other lists

**Key Takeaways:**
- Use `<ul>` for unordered lists
- Use `<ol>` for ordered/numbered lists
- Use `<dl>` for term-definition pairs
- Lists can be nested

---

## Tables

### Overview

Tables display tabular data. HTML provides elements for creating structured tables with headers, rows, and cells.

### Key Concepts

- **Table Structure**: table, thead, tbody, tfoot, tr, th, td
- **Table Headers**: `<th>` for header cells
- **Table Data**: `<td>` for data cells
- **Colspan/Rowspan**: Merge cells
- **Accessibility**: Use `<caption>` and proper headers

### Tables

**What this demonstrates:** Creating tables.

**Code:**
```html
<!-- Basic table -->
<table>
    <caption>Employee Data</caption>
    <thead>
        <tr>
            <th>Name</th>
            <th>Position</th>
            <th>Salary</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Alice Johnson</td>
            <td>Developer</td>
            <td>$120,000</td>
        </tr>
        <tr>
            <td>Bob Smith</td>
            <td>Designer</td>
            <td>$95,000</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2">Total</td>
            <td>$215,000</td>
        </tr>
    </tfoot>
</table>

<!-- Table with colspan and rowspan -->
<table border="1">
    <tr>
        <th>Name</th>
        <th colspan="2">Details</th>
    </tr>
    <tr>
        <td rowspan="2">John</td>
        <td>Age</td>
        <td>30</td>
    </tr>
    <tr>
        <td>City</td>
        <td>Houston</td>
    </tr>
</table>
```

**Explanation:**
- `<table>`: Table container
- `<caption>`: Table caption/title
- `<thead>`: Header section
- `<tbody>`: Body section
- `<tfoot>`: Footer section
- `<tr>`: Table row
- `<th>`: Header cell (bold, centered by default)
- `<td>`: Data cell
- `colspan`: Merge columns
- `rowspan`: Merge rows

**Key Takeaways:**
- Use semantic structure (`<thead>`, `<tbody>`, `<tfoot>`)
- Use `<th>` for headers, `<td>` for data
- Use `<caption>` for table titles
- `colspan` and `rowspan` for merged cells

---

## Forms

### Overview

Forms collect user input. HTML provides various input types and form elements for creating interactive forms.

### Key Concepts

- **Form Element**: Container for form inputs
- **Input Types**: text, email, password, number, date, etc.
- **Form Attributes**: action, method, enctype
- **Input Attributes**: required, pattern, placeholder, etc.
- **Form Validation**: HTML5 built-in validation

### Forms

**What this demonstrates:** Creating forms.

**Code:**
```html
<form action="/submit" method="POST" enctype="multipart/form-data">
    <fieldset>
        <legend>Personal Information</legend>
        
        <!-- Text input -->
        <label for="name">Name:</label>
        <input type="text" 
               id="name" 
               name="name" 
               placeholder="Enter your name"
               required
               minlength="2"
               maxlength="50"
               autocomplete="name">
        
        <!-- Email -->
        <label for="email">Email:</label>
        <input type="email" 
               id="email" 
               name="email"
               placeholder="you@example.com"
               required
               autocomplete="email">
        
        <!-- Password -->
        <label for="password">Password:</label>
        <input type="password" 
               id="password" 
               name="password"
               required
               minlength="8"
               pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}">
        
        <!-- Number -->
        <label for="age">Age:</label>
        <input type="number" 
               id="age" 
               name="age"
               min="0"
               max="120"
               step="1"
               value="25">
        
        <!-- Date -->
        <label for="dob">Date of Birth:</label>
        <input type="date" 
               id="dob" 
               name="dob"
               min="1900-01-01"
               max="2024-12-31">
        
        <!-- Radio buttons -->
        <p>Gender:</p>
        <input type="radio" id="male" name="gender" value="male">
        <label for="male">Male</label>
        
        <input type="radio" id="female" name="gender" value="female">
        <label for="female">Female</label>
        
        <!-- Checkboxes -->
        <p>Interests:</p>
        <input type="checkbox" id="coding" name="interests" value="coding">
        <label for="coding">Coding</label>
        
        <!-- Select dropdown -->
        <label for="country">Country:</label>
        <select id="country" name="country" required>
            <option value="">-- Select Country --</option>
            <option value="us">United States</option>
            <option value="uk">United Kingdom</option>
        </select>
        
        <!-- Textarea -->
        <label for="comments">Comments:</label>
        <textarea id="comments" 
                  name="comments"
                  rows="4"
                  cols="50"
                  placeholder="Enter your comments..."></textarea>
        
        <!-- File upload -->
        <label for="file">Upload File:</label>
        <input type="file" 
               id="file" 
               name="file"
               accept=".pdf,.doc,.docx"
               multiple>
        
        <!-- Buttons -->
        <button type="submit">Submit Form</button>
        <button type="reset">Reset Form</button>
    </fieldset>
</form>
```

**Explanation:**
- `<form>`: Form container
- `action`: URL to submit form
- `method`: GET or POST
- `<label>`: Label for input (use `for` attribute)
- `type`: Input type (text, email, password, etc.)
- `required`: Field must be filled
- `placeholder`: Placeholder text
- `pattern`: Regular expression validation
- `<fieldset>`: Groups related fields
- `<legend>`: Fieldset caption
- `<select>`: Dropdown list
- `<textarea>`: Multi-line text input

**Key Takeaways:**
- Always use `<label>` with `for` attribute
- Use `required` for mandatory fields
- Use appropriate `type` for validation
- Use `<fieldset>` to group related fields
- Use semantic input types (email, url, tel, etc.)

---

## Semantic HTML5

### Overview

Semantic HTML5 elements convey meaning beyond presentation. They improve accessibility, SEO, and code maintainability.

### Key Concepts

- **Semantic Elements**: Elements with meaning (header, nav, main, etc.)
- **Document Structure**: header, nav, main, article, section, aside, footer
- **Media Elements**: figure, figcaption
- **Benefits**: Accessibility, SEO, maintainability

### Semantic HTML5 Elements

**What this demonstrates:** Using semantic HTML5 elements.

**Code:**
```html
<body>
    <header>
        <h1>Site Title</h1>
        <nav>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">About</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <article>
            <header>
                <h2>Article Title</h2>
                <time datetime="2024-12-30">2024-12-30</time>
            </header>
            
            <section>
                <h3>Introduction</h3>
                <p>Content...</p>
            </section>
            
            <aside>
                <p>Related information</p>
            </aside>
        </article>
    </main>
    
    <footer>
        <p>&copy; 2024 Company Name</p>
    </footer>
</body>
```

**Explanation:**
- `<header>`: Site or section header
- `<nav>`: Navigation links
- `<main>`: Main content (one per page)
- `<article>`: Self-contained content
- `<section>`: Thematic grouping
- `<aside>`: Tangentially related content
- `<footer>`: Site or section footer
- `<figure>`: Self-contained media
- `<figcaption>`: Caption for figure

**Key Takeaways:**
- Use semantic elements instead of generic `<div>`
- `<main>` should appear once per page
- Semantic elements improve accessibility and SEO
- Use `<article>` for independent content
- Use `<section>` for thematic grouping

---

## Metadata & SEO

### Overview

Metadata provides information about the HTML document. Proper metadata improves SEO and social media sharing.

### Key Concepts

- **Meta Tags**: Provide document metadata
- **Title Tag**: Page title (important for SEO)
- **Description**: Meta description for search engines
- **Open Graph**: Social media metadata
- **Viewport**: Mobile responsive meta tag

### Metadata

**What this demonstrates:** Adding metadata.

**Code:**
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Complete HTML guide">
    <meta name="keywords" content="HTML, HTML5, web development">
    <meta name="author" content="Your Name">
    
    <!-- Open Graph (Facebook, LinkedIn) -->
    <meta property="og:title" content="HTML Guide">
    <meta property="og:description" content="Complete HTML learning resource">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://example.com">
    <meta property="og:image" content="https://example.com/image.jpg">
    
    <!-- Twitter Card -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="HTML Guide">
    
    <title>HTML Guide - Complete Tutorial</title>
</head>
```

**Explanation:**
- `charset`: Character encoding (always use UTF-8)
- `viewport`: Mobile responsive settings
- `description`: Page description (SEO important)
- `keywords`: Keywords (less important now)
- `author`: Author information
- Open Graph: Social media sharing metadata
- Twitter Card: Twitter sharing metadata
- `<title>`: Page title (shown in browser tab, important for SEO)

**Key Takeaways:**
- Always include `charset="UTF-8"`
- Include viewport meta for responsive design
- Write descriptive `<title>` (important for SEO)
- Add Open Graph tags for social sharing
- Meta description appears in search results

---

## Best Practices

### Accessibility

- **Alt Text**: Always include `alt` attribute for images
- **Semantic HTML**: Use semantic elements
- **Labels**: Always use `<label>` with form inputs
- **Heading Hierarchy**: Use headings in order (h1 → h2 → h3)
- **ARIA**: Use ARIA attributes when needed
- **Keyboard Navigation**: Ensure all interactive elements are keyboard accessible
- **Color Contrast**: Ensure sufficient contrast
- **Screen Readers**: Test with screen readers

### SEO

- **One H1**: Use one `<h1>` per page
- **Descriptive Titles**: Write descriptive `<title>` tags
- **Meta Description**: Include meta description
- **Semantic Markup**: Use semantic HTML5 elements
- **Image Alt Text**: Descriptive alt text for images
- **Valid HTML**: Create valid, clean HTML
- **Structured Data**: Use Schema.org structured data
- **Mobile Friendly**: Ensure mobile responsiveness

### Performance

- **Lazy Loading**: Use `loading="lazy"` for images
- **Image Optimization**: Optimize image sizes and formats
- **Minimize HTTP Requests**: Combine CSS/JS files
- **CDN**: Use CDN for static assets
- **Caching**: Enable browser caching
- **Compression**: Enable gzip/brotli compression

---

## Common Patterns

### Navigation Menu

```html
<nav aria-label="Main navigation">
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

### Form with Validation

```html
<form>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" 
           minlength="8" required>
    
    <button type="submit">Submit</button>
</form>
```

### Card Layout

```html
<article>
    <header>
        <h2>Article Title</h2>
        <time datetime="2024-12-30">December 30, 2024</time>
    </header>
    <p>Article content...</p>
    <footer>
        <p>Author: John Doe</p>
    </footer>
</article>
```

---

## Resources

### Official Documentation

- **MDN HTML Reference**: https://developer.mozilla.org/en-US/docs/Web/HTML
- **HTML Living Standard**: https://html.spec.whatwg.org/
- **W3C HTML**: https://www.w3.org/html/

### Learning Resources

- **MDN HTML Guide**: https://developer.mozilla.org/en-US/docs/Web/HTML
- **HTML5 Doctor**: http://html5doctor.com/
- **HTML Reference**: https://htmlreference.io/

### Community

- **Stack Overflow**: Tag: html
- **r/webdev**: Reddit community
- **web.dev**: Google's web development resources

### Tools

- **HTML Validator**: https://validator.w3.org/
- **CodePen**: Online HTML editor
- **VS Code**: Code editor with HTML support
- **Chrome DevTools**: Browser developer tools

---

