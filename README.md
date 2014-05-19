# apdev frontend coding guidelines

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
var obj = {
  good: "code",
  "is generally": "pretty"
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
- all lowercase tags
- use double quotes `"` for attributes
- separation of concerns  
  Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.  
  **=> meaning: no inline-styling etc.**

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
- **never use `!important`**
- avoid qualifying ID and class names with type selectors (for [performance reasons](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/))
- only one selector per line

```css
.item-1,
.item-2,
.item-3 {
  /* … */
}
```

- put comments on the line above what you want to comment on

#### CSS Pre-processors
- use pre-processors like (SASS or LESS) where possible
- as a rule of thumb, don't nest further than 3 levels deep. If you find yourself going further, think about reorganizing your rules (either the specificity needed, or the layout of the nesting).
- use separate files (concatenated by a build step) to help break up code for distinct components
- 
