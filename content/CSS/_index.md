---
title: "CSS"
date: 2023-05-29T18:31:10-04:00
draft: false
---

{{< panel title="Update Log" style="success" >}}

* 2023 06 02 - Initial Commit

{{< /panel >}}

{{< panel title="WIP" style="danger" >}}
This site is a work in progress, notes are being actively added, formatted and reorganized at the moment.
{{< /panel >}}

{{< lead >}}

### Overview

(Cascading Style Sheets) is a language used to define the presentation and styling of HTML elements in web pages. It provides a wide range of capabilities for controlling the layout, colors, fonts, and other visual aspects of a website. With CSS, designers can create visually appealing and responsive web designs, customize the appearance of text, images, and backgrounds, and apply animations and transitions. CSS uses selectors to target specific elements and apply styles to them. It plays a crucial role in separating the content and structure of a webpage from its visual representation, enhancing the user experience and enabling consistent design across multiple pages.

### History

Initially proposed by Håkon Wium Lie and Bert Bos, CSS went through various iterations, with CSS1 being released in 1996. Subsequent versions, CSS2 and CSS3, expanded its capabilities and introduced new features. CSS3 is modular and includes separate specifications for selectors, layout, animations, and more.

### Governance

CSS is governed by the CSS Working Group, which operates under the World Wide Web Consortium (W3C). This group consists of web experts and browser vendors who collaborate to develop and maintain CSS standards, ensuring cross-browser compatibility and continuous evolution of the language.

### W3 Consortium

(From their website) The World Wide Web Consortium (W3C) is an international community where Member organizations, a full-time staff, and the public work together to develop Web standards. Led by Web inventor and Director Tim Berners-Lee, Interim CEO Ralph Swick and a Board of Directors, W3C's mission is to lead the Web to its full potential. Contact W3C for more information.

[https://www.w3.org/](https://www.w3.org/)

{{< /lead >}}

---

# Cascading Style Sheets

---

## CSS Syntax

A style defines the appearance of an element on a page. It is a rule that tells the browser how to present something on a web page. A style consists of two main parts:

---

### 1. Selector 
- The selector points to the HTML element you want to style.

---

### 2. Declaration Block 
- The declaration block contains one or more declarations separated by semicolons.
- Declaration: Each declaration includes a CSS property name and a value, separated by a colon.
- Property: Specifies the CSS property to be styled.
- Value: Specifies the value of the CSS property.

---

<a href="#top" class="back-to-top">Back to Top</a>

## CSS Comments

- A CSS comment starts with `/*` and ends with `*/`. Comments can also span multiple lines.

---

    p {
    color: red;
    /* This is a single-line comment */
    text-align: center;
    }

---

## CSS Units

* CSS has several units for expressing length.
* Length is a number followed by a length unit, such as 10px, 2em, etc.
* There should be no whitespace between the number and the unit. However, if the value is 0, the unit can be omitted.
* There are two types of length units: relative and absolute.
* Relative length units specify a length relative to another length property.
    em: Relative to the font-size of the element (2em means 2 times the size of the current font).
    rem: Relative to the font-size of the root element.
    %: Percent
* Absolute length units are fixed and appear exactly as the specified size.
    px: pixels (1px = 1/96th of 1in)

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## CSS Selectors

CSS selectors are used to target specific HTML elements for styling. They allow you to select elements based on their tag name, class, ID, attributes, and more. Here are some common CSS selectors:

---

### Tag Selector

---

Selects all elements with a specific tag name.

Example:

    p {
    color: blue;
    }

This will select all <p> elements and set their text color to blue.

---

### Class Selector

Selects elements with a specific class attribute.

    .my-class {
    font-weight: bold;
    }

---

### ID Selector

Selects an element with a specific ID attribute.

---

    #my-element {
    color: red;
    font-size: 20px;
    }

---

<p id="my-element">This is a paragraph with the ID "my-element".</p>

---

Remember, IDs should be unique within the HTML document to ensure proper functionality and avoid conflicts. Use the CSS ID selector when you want to apply specific styles to a single, unique element.

Feel free to modify the example and apply it to your own HTML elements with unique IDs.


---

### Attribute Selector

Selects elements based on their attribute values.

---

    [type="submit"] {
    border: 1px solid green;
    }

---

### Descendant Selector

Selects elements that are descendants of another element.

---

    div p {
    text-decoration: underline;
    }

---

### Child Selector

Selects elements that are direct children of another element.

---

    ul > li {
    list-style-type: square;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## CSS Grouping Selectors

CSS grouping selectors allow you to apply styles to multiple elements at once by grouping them together. This helps in reducing code duplication and simplifying the styling process. Here are some examples of CSS grouping selectors:
Selector Grouping

---

    h1, h2, h3 {
    color: blue;
    font-weight: bold;
    }

---

### Grouping Descendant Selectors

You can also group descendant selectors to target specific elements within a common parent.

---

    div p, div span {
    color: red;
    }

---

This will apply the color red to all <p> and <span> elements that are descendants of a <div>.

---

### Grouping Class Selectors

Grouping selectors can be used with class selectors to apply styles to multiple elements sharing the same class.

---

    .button-primary, .button-secondary {
    background-color: blue;
    color: white;
    padding: 10px 20px;
    }

---

This will apply the specified styles to all elements with the classes .button-primary and .button-secondary.

Grouping selectors in CSS allows for efficient and concise styling of multiple elements with similar properties. By leveraging grouping selectors, you can streamline your CSS code and achieve consistent and cohesive designs throughout your web pages.

---

### CSS Universal Selectors

In CSS, a universal selector allows you to target all elements on a web page regardless of their type or position in the HTML structure. It is represented by an asterisk (*). The universal selector applies styles to every element on the page. This can be useful when you want to set global styles or apply a common style to all elements.

---

    {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    }

---

### CSS Descendant Selectors

In CSS, descendant selectors are used to target elements that are descendants of a specific parent element. This allows you to apply styles to elements based on their hierarchical relationship within the HTML structure. To select a descendant element, you specify both the parent element and the descendant element, separated by a space.

---

    .parent-element p {
    color: blue;
    font-size: 16px;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

### CSS Attribute Selectors

In CSS, attribute selectors allow you to target elements based on their attribute values. This provides a way to select elements that have specific attributes or attribute values, regardless of the element type.

Attribute selectors are enclosed in square brackets ([]) and can be used in various ways:

Select elements with a specific attribute:

---

    [attribute] {
    /* Styles applied to elements with the specified attribute */
    }

---

Select elements with a specific attribute and value:

---

    [attribute="value"] {
    /* Styles applied to elements with the specified attribute and value */
    }

---

Select elements with an attribute that begins with a specific value:

---

    [attribute^="value"] {
    /* Styles applied to elements with the specified attribute value at the beginning */
    }

---

Select elements with an attribute that ends with a specific value:

---

    [attribute$="value"] 

---

Select elements with an attribute that contains a specific value:

---

    [attribute*="value"]

---

Select all elements with the required attribute:

---

    input[required] {
    border: 1px solid red;
    }

---

Select all elements with the href attribute starting with "https://":

---

    a[href^="https://"] {
    color: blue;
    }

---

Select all elements with the alt attribute containing the word "logo":

---

    img[alt*="logo"] {
    width: 100px;
    }

---

**Benefits**

Attribute selectors provide flexibility in targeting elements based on their attributes, making it easier to apply styles to specific elements that meet certain criteria. This allows for more dynamic and precise styling without relying on specific class or ID values.

---

**Considerations**

While attribute selectors are powerful, it's important to use them judiciously to avoid overcomplicating your CSS and impacting performance. Keep in mind that attribute selectors are not supported in older versions of Internet Explorer (IE7 and below).

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Sibling Selectors

### Adjacent Sibling Selectors 

The adjacent sibling selector in CSS allows you to select an element that comes immediately after another specific element. It uses the `+` symbol to target the adjacent sibling.

---

    h1 + p {
    color: blue;
    }

---

### General Sibling Selectors

The general sibling selector in CSS allows you to select all sibling elements that come after a specific element, regardless of their position in the HTML structure. It uses the `~` symbol to target the general siblings.

---

    h1 ~ p {
    font-weight: bold;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Pseudo-classes

Pseudo-classes in CSS allow you to select and style elements based on their state or position within the document. They are denoted by a colon (`:`) followed by the pseudo-class name.

---

    a:hover {
    color: red;
    text-decoration: underline;
    }

---

## Pseudo-elements

Pseudo-elements in CSS allow you to style and add content to specific parts of an element. They are denoted by double colons (`::`) followed by the pseudo-element name.

---

    blockquote::before {
    content: open-quote;
    }

---

## Style Inheritance

Style inheritance in CSS allows certain properties of an element to be inherited by its children. Inherited properties are automatically applied to child elements unless explicitly overridden.

---

    body {
    font-family: Arial, sans-serif;
    color: #333;
    }

    h1 {
    font-size: 24px;
    font-weight: bold;
    }

    p {
    font-size: 16px;
    }

    span {
    color: red;
    }

    p {
    font-size: 16px;
    }

    span {
    color: red;
    }

---

In this example, the body element sets the font family to Arial and the color to #333. The h1 and p elements inherit these styles from their parent body element. However, the span element explicitly overrides the inherited font color and sets it to red.

Style inheritance is helpful for establishing a consistent visual hierarchy throughout a website or application, as it allows styles to be applied to parent elements and automatically inherited by their children.

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Cascading Style Inheritance

Cascading Style Sheets (CSS) utilizes a cascade mechanism that determines how styles are applied to elements. The cascade style inheritance in CSS refers to the order and specificity of styles that affect an element.

---

    p {
    color: blue;
    font-size: 14px;
    }

    p.special {
    color: red;
    font-weight: bold;
    }

    #unique {
    font-size: 18px;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Setting Height and Width

In CSS, you can specify the height and width of elements using various units of measurement. The height and width properties allow you to control the size of an element on the web page.

--- 

    div {
    height: 200px;
    width: 300px;
    }

---

    img {
    height: 150px;
    width: auto;
    }

---

    button {
    height: 40px;
    width: 120px;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Display Property with block and inline Values in CSS

The `display` property in CSS allows you to control how an element is rendered on the web page. Two common values for the `display` property are `block` and `inline`.

---

    div.block {
    display: block;
    width: 200px;
    height: 100px;
    background-color: red;
    margin-bottom: 10px;
    }

---

    span.inline {
    display: inline;
    color: blue;
    font-weight: bold;
    }

---

In this example, a div element with the class block is set to display as a block-level element. It has a specified width, height, background color, and a margin-bottom of 10 pixels. Block-level elements occupy the entire width of their parent container and stack vertically.

On the other hand, a span element with the class inline is set to display as an inline element. It has a blue color and bold font weight. Inline elements only occupy the space necessary for their content and do not create line breaks.

---

## The Box Model (Concept)

In CSS, every element is treated as a rectangular box. The box model is a fundamental concept that describes the structure and layout of these boxes. It consists of four main components: content, padding, border, and margin.

---

### Content

The content area is where the actual content of the element, such as text or images, is displayed. It has width and height properties.

---

### Padding

Padding is the space between the content and the border. It can be set using the `padding` property and affects the size of the element's total width and height.

---

### Border

The border is a line that surrounds the padding and content. It can be styled using properties like `border-width`, `border-color`, and `border-style`.

---

### Margin

Margin is the space outside the border. It creates a gap between the element and other elements in the layout. Margins can be set using the `margin` property.

---

    .box {
    width: 200px;
    height: 100px;
    padding: 20px;
    border: 2px solid black;
    margin: 10px;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## CSS Layouts

CSS layouts refer to the arrangement and positioning of elements on a web page. There are various techniques and approaches to create different types of layouts. Here are some commonly used layout methods:

---

### 1. Float Layout

Float layout is a traditional method where elements are floated left or right within a container. It allows elements to wrap around each other and create multi-column layouts. Float layout can be achieved using the `float` property.

---

    /* HTML */
    <div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
    </div>

---

    /* CSS */
    .container {
    width: 500px;
    }

    .box {
    float: left;
    width: 150px;
    height: 150px;
    margin: 10px;
    background-color: #eaeaea;
    }

---

### 2. Flexbox Layout

Flexbox is a powerful CSS layout model that provides a flexible way to arrange elements within a container. It enables alignment, distribution, and reordering of elements along the main axis and cross axis. Flexbox layout can be implemented using the `display: flex` property on the container and various other flex-related properties.

---

    /* HTML */
    <div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
    </div>

---

    /* CSS */
    .container {
    display: flex;
    }

    .box {
    flex: 1;
    height: 150px;
    margin: 10px;
    background-color: #eaeaea;
    }

---

### 3. Grid Layout

Grid layout allows for creating complex two-dimensional layouts. It divides the page into a grid of rows and columns, where elements can be placed in specific cells or spans. Grid layout provides fine control over the positioning and alignment of elements. It can be implemented using the `display: grid` property on the container and defining grid rows and columns.

---

    /* HTML */
    <div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
    </div>

---

    /* CSS */
    .container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 10px;
    }

    .box {
    height: 150px;
    background-color: #eaeaea;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---

### 4. CSS Frameworks

CSS frameworks like Bootstrap and Foundation provide pre-built layout systems that offer responsive designs and a grid system for organizing elements. These frameworks often come with predefined classes and components that simplify the process of creating complex layouts.

---

#### Popular CSS Frameworks

1. Bootstrap
   - Website: [Bootstrap](https://getbootstrap.com/)
   - Description: A widely-used framework that provides a responsive grid system, pre-styled components, and extensive CSS utilities. It also includes JavaScript plugins for enhanced interactivity.

---

2. Foundation
   - Website: [Foundation](https://foundation.zurb.com/)
   - Description: A powerful responsive front-end framework that offers a grid system, a collection of UI components, and built-in responsive design features. It focuses on customization and scalability.

---

3. Bulma
   - Website: [Bulma](https://bulma.io/)
   - Description: A lightweight and modern CSS framework that emphasizes simplicity and flexibility. It provides a responsive grid, numerous UI components, and utilities for rapid website development.

---

4. Tailwind CSS
   - Website: [Tailwind CSS](https://tailwindcss.com/)
   - Description: A highly customizable CSS framework that provides a utility-first approach. It offers a wide range of pre-built utility classes that allow developers to rapidly build unique designs.

---

5. Material-UI
   - Website: [Material-UI](https://material-ui.com/)
   - Description: A popular framework that implements the Material Design guidelines from Google. It provides a comprehensive set of pre-styled React components with a modern and sleek appearance.

---

6. Semantic UI
   - Website: [Semantic UI](https://semantic-ui.com/)
   - Description: A user-friendly framework that focuses on natural language principles for intuitive and readable syntax. It offers a wide range of UI components and a responsive grid system.

---

7. UIKit
   - Website: [UIKit](https://getuikit.com/)
   - Description: A lightweight and modular framework that provides a collection of reusable components and a flexible grid system. It is known for its modern and stylish design.

---

### 5. CSS Grid Frameworks

CSS grid frameworks like 960 Grid System and Susy provide grid systems based on the CSS grid layout. These frameworks offer a set of classes and mixins that help create grid-based layouts quickly.

---

#### Popular CSS Grid Frameworks

---

1. 960 Grid System
   - Website: [960 Grid System](https://960.gs/)
   - Description: A grid-based framework that provides a solid foundation for creating grid layouts. It offers a 12-column grid system with various layout options and is widely used for its simplicity and versatility.

---

2. Susy
   - Website: [Susy](https://www.oddbird.net/susy/)
   - Description: A powerful grid framework built with Sass that allows for flexible and customizable grid layouts. Susy provides a range of features like nested grids, math-based calculations, and responsive grid design.

---

3. Foundation Grid
   - Website: [Foundation](https://foundation.zurb.com/)
   - Description: Foundation, a comprehensive front-end framework, includes a robust grid system as one of its core features. The Foundation Grid offers responsive, mobile-first grid layouts with various options for customization.

---

4. Bootstrap Grid
   - Website: [Bootstrap](https://getbootstrap.com/)
   - Description: Bootstrap, a widely-used CSS framework, includes a responsive grid system as one of its key components. The Bootstrap Grid allows for building flexible and responsive layouts using a mobile-first approach.

---

5. Materialize Grid
   - Website: [Materialize](https://materializecss.com/)
   - Description: Materialize is a modern CSS framework that implements Material Design principles. Alongside its other components, it offers a responsive grid system for creating visually appealing and responsive layouts.

---

6. YAML
   - Website: [YAML](https://www.yaml.de/)
   - Description: YAML (Yet Another Multicolumn Layout) is a modular and flexible grid framework. It provides options for various grid configurations, including fluid and fixed layouts, making it suitable for different design needs.

---

7. Pure Grids
   - Website: [Pure](https://purecss.io/)
   - Description: Pure is a lightweight CSS framework created by Yahoo. It includes a responsive grid system that allows for the creation of grid-based layouts that adapt to different screen sizes.

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Responsive Web Design

Responsive web design is an approach to designing and developing websites that aim to provide an optimal viewing experience across a range of devices and screen sizes. It involves creating flexible layouts, fluid images, and adaptive functionality to ensure that a website looks and functions well on desktops, tablets, smartphones, and other devices.

---

### Fluid Grids and Flexible Layouts

A fundamental principle of responsive web design is the use of fluid grids and flexible layouts. Instead of fixed pixel-based layouts, elements are sized using relative units such as percentages or "em" values. This allows the layout to adapt and scale proportionally based on the screen size.

---

    .container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 20px;
    }

In this example, the CSS grid layout is used to create a responsive grid. The repeat() function with auto-fit ensures that the columns will automatically adjust to fit the available space. The minmax() function sets the minimum and maximum width of each column, providing flexibility. The grid-gap property adds spacing between the grid items.

---

### Media Queries
<a name="responsive-web-design"></a>
Responsive Web Design

Media queries are a key component of responsive web design. They allow you to apply different CSS styles based on the characteristics of the device or viewport. Media queries typically target specific screen widths or device capabilities.

---

    @media (max-width: 768px) {
    .container {
        grid-template-columns: 1fr;
      }
    }

---

### Responsive Images

Images play a crucial role in web design, and responsive websites need to handle images effectively. Responsive images should adapt and scale based on the screen size to prevent distortion or oversized images on smaller devices. The max-width property can be used to constrain the image width.

---

    img {
    max-width: 100%;
    height: auto;
    }

---

### More Modern Techniques

Beyond fluid grids, media queries, and responsive images, modern techniques have emerged to enhance responsive web design. These include:

---

- Flexbox: A flexible box layout model that simplifies the alignment and positioning of elements within a container. It offers powerful control over element arrangement and responsiveness.

---

- CSS Grid: A two-dimensional grid system that allows for sophisticated and responsive layouts. It provides fine-grained control over rows, columns, and the placement of elements.

---

- CSS Variables: Also known as custom properties, CSS variables allow you to define reusable values that can be used throughout your stylesheets. They can be updated dynamically, enabling responsive changes based on different conditions.

---

- Mobile-First Design: A design approach where the mobile version of a website is developed first, and then additional styles and layouts are added for larger screens. This ensures a solid foundation for smaller devices and enhances performance.

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Forms

---

### Styling Focused Inputs

When a user interacts with an input field on a web form, it's often useful to provide visual feedback to indicate that the input is in focus. CSS allows you to style focused inputs using pseudo-classes, which target elements based on their state.

---

    <a name="focused-inputs"></a>

    input:focus {
    outline: 2px solid blue;
    background-color: lightblue;
    }

---

### Additional Styling Options

    input:focus {
    outline: 2px solid blue;
    background-color: lightblue;
    }


---

<a href="#top" class="back-to-top">Back to Top</a>

---

## Transitions

CSS transitions allow you to animate property changes smoothly over a specified duration. They provide a way to add subtle or eye-catching effects to elements on your web page.

---

    selector {
    transition: property duration timing-function delay;
    }

---

* selector refers to the element(s) you want to apply the transition to.
* property specifies the CSS property you want to animate.
* duration determines how long the transition takes to complete (in seconds or milliseconds).
* timing-function defines the acceleration and deceleration of the transition, such as ease, linear, or cubic-bezier.
* delay specifies the time before the transition starts (in seconds or milliseconds).

---

#### Example 1: Color Transition

    button {
    background-color: blue;
    transition: background-color 0.5s ease-in-out;
    }

    button:hover {
    background-color: red;
    }

---

#### Example 2: Opacity Transition

    .box {
    opacity: 0.5;
    transition: opacity 0.3s linear;
    }

    .box:hover {
    opacity: 1;
    }

---

#### Example 3: Transform Transition

    .image {
    transition: transform 0.4s ease-out;
    }

    .image:hover {
    transform: scale(1.2);
    }

---

## Animation

---

<a href="#top" class="back-to-top">Back to Top</a>

---

## CSS Animations

CSS animations allow you to create dynamic and engaging effects by animating CSS properties over a specified duration. They bring elements to life, adding movement and visual interest to your web pages.

---

### Syntax

    @keyframes animationName {
    0% { /* CSS styles at the start of the animation */ }
    100% { /* CSS styles at the end of the animation */ }
    }

    selector {
    animation: animationName duration timing-function delay iteration-count direction;
    }

---

* animationName is a custom name given to the animation.
* Keyframes (0% and 100%) define the CSS styles at the start and end of the animation.
* duration determines how long the animation takes to complete (in seconds or milliseconds).
* timing-function specifies the acceleration and deceleration of the animation, such as ease, linear, or cubic-bezier.
* delay specifies the time before the animation starts (in seconds or milliseconds).
* iteration-count sets the number of times the animation should repeat.
* direction defines whether the animation should play forward, backward, or alternate between forwards and backwards.

---

#### Example 1: Bounce Animation

    @keyframes bounce {
    0% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
    100% { transform: translateY(0); }
    }

    .box {
    animation: bounce 1s ease-in-out infinite;
    }

    /* Example 2: Fade In Animation */
    @keyframes fadeIn {
    0% { opacity: 0; }
    100% { opacity: 1; }
    }

    .element {
    animation: fadeIn 0.5s ease-out forwards;
    }

---

#### Example 3: Spin Animation

    @keyframes spin {
    0% { transform: rotate(0); }
    100% { transform: rotate(360deg); }
    }

    .spinner {
    animation: spin 1s linear infinite;
    }

---

<a href="#top" class="back-to-top">Back to Top</a>

---
