# CSS

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

