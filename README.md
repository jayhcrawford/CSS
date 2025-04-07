# CSS

### CSS Precedence
 - !important > ID > Class > Element for CSS selectors
 - Two instances of the same CSS selectors making different assignments in a stylesheet--the lower-most instance will be executed on the HTML
 - importing your custom stylesheet vs bootstrap's, import yours lower in the document and it will have greater precedence


### Tools
- [CSSTricks](https://css-tricks.com/)
- [CSS Grid Helper](https://cssgrid-generator.netlify.app/)
- [CanIUse](https://caniuse.com/)


Pseudo elements can punctuate or be the prefix of a component

```
* {
    /* This makes measuring on a webpage easier */
    box-sizing: border-box;
}
```

- Flex grow can be assigned to flex children and used to grow elements in proportion to the flex children of a given parent flex element. Ex. A div with flex-grow of 20 vs a div with flex-grow of 1; the 20 will be 20 times bigger in the parent container.

### Grid with basic fractional column example

<div style="display:grid; grid-template-columns: 1fr 1fr; text-align: center; margin-bottom: 2em;">
<div>element1</div>
<div>element2</div>
<div>element3</div>
<div>element4</div>
<div>element5</div>
<div>element6</div>
</div>

### Combine grid template areas and fractional columns

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
        background-color: purple;
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