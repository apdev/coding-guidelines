# Frontend Coding Guidelines

## JavaScript

- stick to [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
    - exceptions
        - use double quotes `"` instead of single ones `'`
        - use 2 spaces indentation
- lines not longer than 80 characters (see [here](https://github.com/felixge/node-style-guide#80-characters-per-line))
- always `"use strict"` mode (see [here](http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/))
- single `var` statement at the beginning of scope  
  (first assignments, then declarations)
- comma at end of the line
- every assignment on a seperate line
- always use semicolons
- variable naming
    - `lowerCamelCase` for variables
    - `UpperCamelCase` for classnames and
    - `SNAKE_CASE` for "constants"

```javascript
var MAX_ITEMS = 4,
  nameOfThing = "thing's name",
  // comments always on a seperate line
  numberOfItems = 234,
  firstDeclaration, secondDeclaration;
  // semicolons should always be followed by an endline
    
  // …
```

- curly braces  
  (space after `if` but not inside condition)

```javascript
if (something) {
  // …
} else {
  // …
}
```

- array creation

```javascript
var arr = ["hello", "world"];
```

- object creation
    
```javascript
// if it fits into 80 characters, you can do a one-liner
var obj = {good: "code", bad: "code"};

// otherwise split it up on multiple lines like this
var obj = {
  good: "code",
  "is generally": "pretty",
  most: "of the time, at least" 
};
```
    
- always use `===` and/or `!==` to compare two values
- do not extend built-in prototypes
- use descriptive conditions

```javascript
var isValidPassword = password.length >= 4 && /^(?=.*\d).{4,}$/.test(password);

if (isValidPassword) {
  console.log("winning");
}
```

- use slashes (`//`) for both single line and multi line comments. Try to write comments that explain higher level mechanisms or clarify difficult segments of your code. Don't use comments to restate trivial things.


## HTML & CSS

- roughly based on [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)

### HTML
- use `HTML5` doctype: `<!doctype html>`
- use 2 spaces indentation
- nested elements should be indented once
- all lowercase tags
- use double quotes `"` for attributes
- do not include a trailing slash in self-closing elements
- separation of concerns  
  Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.  
  **=> meaning: no inline-styling etc.**
- omit a `type` when including CSS and JavaScript files as `text/css` and `text/javascript` are their respective defaults
- HTML attributes should come in this particular order for easier reading of code:
    - `class`
    - `id`, `name`
    - `data-*`
    - `src`, `for`, `type`, `href`
    - `title`, `alt`
    - `aria-*`, `role`

*Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.*

```html
<a class="..." id="..." data-modal="toggle" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### CSS
- use 2 spaces indentation
- all lowercase classnames/IDs (no camelCase, use hyphens instead)

```css
#login {}
.gallery {}
```

- use class names/IDs that are as short as possible but as long as necessary
- do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.

```css
.gallery {}
.gallery-item {}
```

- that said, usually don't use IDs in CSS
- put one space after `:` in property declarations
- put one space before `{` in rule declarations
- use hex color codes `#000` unless using `rgba()`
- each declaration should appear on its own line for more accurate error reporting  
  *In instances where a rule set includes only one declaration, consider removing line breaks for readability and faster editing.*
- end all declarations with a semi-colon
- comma-separated property values should include a space after each comma
- do not include spaces after commas within `rgb()`, `rgba()`, `hsl()`, `hsla()` or `rect()` values  
  *This helps differentiate multiple color values (comma, no space) from multiple property values (comma with space)*
- lowercase all hex values, e.g., `#fff`
- use shorthand hex values where available, e.g., `#fff` instead of `#ffffff`

```css
.gallery-item {
  border: 1px solid #0f0;
  color: #000;
  background: rgba(0,0,0,0.5);
}
```

- related property declarations should be grouped together following the order:
    1. **Positioning**  
    *Positioning comes first because it can remove an element from the normal flow of the document and override box model related styles*
    2. **Box model**  
    *The box model comes next as it dictates a component's dimensions and placement.  
Everything else takes place inside the component or without impacting the previous two sections, and thus they come last.*
    3. **Typographic**
    4. **Visual**

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

- **never use `!important`**
- avoid qualifying ID and class names with type selectors (for [performance reasons](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/))

```css
/* wrong */
li.gallery-item {}
/* right */
.gallery-item {}

```

- when grouping selectors, keep individual selectors to a single line

```css
.item-1,
.item-2,
.item-3 {
  /* … */
}
```

- place closing braces of declaration blocks on a new line
- put comments on the line above what you want to comment on
- do not use `@import` - compared to `<link>`s, `@import` is slower, adds extra page requests, and can cause other unforeseen problems. Avoid them and instead opt for an alternate approach:  
    - Use multiple <link> elements
    - Compile your CSS with a preprocessor like Sass or Less into a single file
    - Concatenate your CSS files with features provided in Rails, Jekyll, and other environments

#### CSS Pre-processors
- use pre-processors like (SASS or LESS) where possible
- as a rule of thumb, don't nest further than 3 levels deep. If you find yourself going further, think about reorganizing your rules (either the specificity needed, or the layout of the nesting).
- use separate files (concatenated by a build step) to help break up code for distinct components

## Sources
- [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
- [Felix's Node.js Style Guide](https://github.com/felixge/node-style-guide)
- [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
- [Github Styleguide](https://github.com/styleguide/css)
- [Code Guide by @mdo](http://codeguide.co/)
