# CSS


 ### CSS Reset 
 - Andy Bell's A (more) Modern CSS Reset 2025

 ```

/* Box sizing rules */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* Prevent font size inflation */
html {
  -moz-text-size-adjust: none;
  -webkit-text-size-adjust: none;
  text-size-adjust: none;
}

/* Remove default margin in favour of better control in authored CSS */
body, h1, h2, h3, h4, p,
figure, blockquote, dl, dd {
  margin-block-end: 0;
}

/* Remove list styles on ul, ol elements with a list role, which suggests default styling will be removed */
ul[role='list'],
ol[role='list'] {
  list-style: none;
}

/* Set core body defaults */
body {
  min-height: 100vh;
  line-height: 1.5;
}

/* Set shorter line heights on headings and interactive elements */
h1, h2, h3, h4,
button, input, label {
  line-height: 1.1;
}

/* Balance text wrapping on headings */
h1, h2,
h3, h4 {
  text-wrap: balance;
}

/* A elements that don't have a class get default styles */
a:not([class]) {
  text-decoration-skip-ink: auto;
  color: currentColor;
}

/* Make images easier to work with */
img,
picture {
  max-width: 100%;
  display: block;
}

/* Inherit fonts for inputs and buttons */
input, button,
textarea, select {
  font-family: inherit;
  font-size: inherit;
}

/* Make sure textareas without a rows attribute are not tiny */
textarea:not([rows]) {
  min-height: 10em;
}

/* Anything that has been anchored to should have extra scroll margin */
:target {
  scroll-margin-block: 5ex;
}
 ```

#### Chaining selectors and scaling elements with variables

```
h1, h2, h3, h4 {
    /* This applies to all four selectors */
}

div > h1 {
    /* This applies to h1 elements in div elements */
}
```

```
:root {
    --base-size: 1rem; /* rem scales */
    --scale: 1.2;
    --h1: calc(var(--h2) * var(--scale));
    --h2: calc(var(--h3) * var(--scale));
    --h3: calc(var(--h4) * var(--scale));
    --h4: var(--base-size);
}
```

<!-- The style variables below will change the format of this markdown README -->

<style>
    :root {
    --base-size: 1.1rem; /* rem scales */
    --scale: 2;
    --h1: calc(var(--h2) * var(--scale));
    --h2: calc(var(--h3) * var(--scale));
    --h3: calc(var(--h4) * var(--scale));
    --h4: var(--base-size);
    }

    h1 {
        font-size: var(--h1);
    }
    h2 {
        font-size: var(--h2);
    }
    h3 {
        font-size: var(--h3);
    }
    h4 {
        font-size: var(--h4);
    }
</style>

#### CSS Precedence

- !important > ID > Class > Element for CSS selectors
- Two instances of the same CSS selectors making different assignments in a stylesheet--the lower-most instance will be executed on the HTML
- importing your custom stylesheet vs bootstrap's, import yours lower in the document and it will have greater precedence

#### Tools

- [CSSTricks](https://css-tricks.com/)
- [CSS Grid Helper](https://cssgrid-generator.netlify.app/)
- [CanIUse](https://caniuse.com/)
- [Adobe Color](https://color.adobe.com/)
- [fontpair](https://www.fontpair.co/)
- [Google Fonts](https://fonts.google.com/)
Pseudo elements can punctuate or be the prefix of a component
- [ResponsiveBreakpoints](https://responsivebreakpoints.com/)

```
    /* This makes measuring on a webpage easier */

* {
    box-sizing: border-box;
}

    /* More verbose below */

html {
    box-sizing: border-box;
}
*,
*::before,
*::after {
    box-sizing: inherit;
}

```

- Flex grow can be assigned to flex children and used to grow elements in proportion to the flex children of a given parent flex element. Ex. A div with flex-grow of 20 vs a div with flex-grow of 1; the 20 will be 20 times bigger in the parent container.

#### Grid with basic fractional column example

<div style="display:grid; grid-template-columns: 1fr 1fr; text-align: center; margin-bottom: 2em;">
<div>element1</div>
<div>element2</div>
<div>element3</div>
<div>element4</div>
<div>element5</div>
<div>element6</div>
</div>

#### Combine grid template areas and fractional columns

<style>
    .page {
        color: black;
        display: grid;
        grid-template-columns: 5fr 5fr 1fr 5fr;
        grid-template-areas: 
        "nav-header nav-header nav-header nav-sidebar"
        "main-body main-body . nav-sidebar"
        "main-body main-body . nav-sidebar"
        "footer footer footer footer"
    }
    .header {
        background-color: red;
        height: 100px;
        grid-area: nav-header;
    }
    .body {
        background-color: green;
        height: 200px;
        grid-area: main-body;
    }
        .sidebar {
        background-color: pink;
        grid-area: nav-sidebar;
    }
        .footer {
        background-color: blue;
        height: 100px;
        grid-area: footer;
    }

</style>

<div class="page">
<header class="header">Header</header>
<div class="body">Body</div>
<div class="sidebar">Sidebar</div>
<footer class="footer">Footer</footer>
</div>

#### Variables

_it is useful to use variables for thematic aspects like:_

- font stacks
- colors
- font size
- padding

#### Line height

without a unit of measure, line height will be a multiple of the font on the line, rather than a fixed size.

```
p {
    line-height: 1.5
}
```

#### Overlap with CSS Grid

<style>
    .ol_page {
        color: black;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        margin-bottom: 2rem;
    }
    .ol_body {
        background-color: green;
        height: 300px;
        grid-column: 1/6;
        grid-row: 1/4;

    }
    .ol_overlap {
        background-color: pink;
        height: 100px;
        grid-column: 3/5;
        grid-row: 2/3;
        z-index: 1;

    }
</style>
<div class="ol_page">
<div class="ol_overlap">Overlap</div>
<div class="ol_body">Body</div>
</div>

<style>
    .gap_example {
        background-color: red;
        height: 200px;
        display: grid;
        grid-template-columns: repeat(3, 1fr);
    }

    .gap_ex_elem {
        display: inline;
        background-color: blue;
        margin: 1px 10px 20px 9px;; 
    }
</style>
<div class="gap_example">
<div class="gap_ex_elem elem1"></div>
<div class="gap_ex_elem elem2"></div>
<div class="gap_ex_elem elem3"></div>
</div>

#### Making grid responsive
 - auto-fit
 - auto-fill
 - minmax


 ### Flexbox
#### Used for
 - A series of boxes that are not the same size
 - A series of boxes that are not in an even-sized grid
 - When the same space between elements is important, not the same width of each element
 - Flexbox wasn't designed to be locked down for layouts

 ### Image Optimization
 - Image Optimization - Addy Osmani
 - the < picture> element can allow for responsively loading different source files based on media query
