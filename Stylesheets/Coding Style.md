# Coding Style

We mainly use Sass (written as SCSS) as a pre-processor to generate the final CSS styles for each project. As a result, our CSS coding style mixes with the Sass and on the following document we try to give this distinction by pointing to what only applies to Sass (in general because it is invalid CSS).

## General principles

If you follow nothing else at least don't forget these next few lines.

> "Part of being a good steward to a successful project is realizing that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec." - Idan Gazit

* **All code should look like a single person wrote it, even when many actually did.** This ensures that anyone coming in to the project later on for whatever reason (correct a bug, extend functionality, help with development, etc.) will be able to understand and contribute in a single voice.
* Code readability should come first and optimization second.
* When in doubt about a style raise the question for debate and proceed with existing common patterns (share these patterns with your question).
* Enforce the agreed-upon style, always. Code review is a particular example where this should always be done.

## CSS

### Naming Conventions

* Use lowercase and separate words with hyphens, don't use camelCase or snake_case. An exception to this is to override some out

### Location-based Styling

Never use it. We code in WordPress, and there are many temptations to override or extend a given class based on a specific class that WordPress attaches to a page (post-type, single, front-page, home-page, to name a few), but try not to. Add a modifier class to your block based on its location and apply your overrides/extensions to that class.
(Outside the WordPress environment the advice is the same!)

### Format

* Include one space before the opening braces

Bad:
```css
.selector-1,
.selector-2{
  /* Declarations */
}
```

Good:
```css
.selector-1,
.selector-2 {
  /* Declarations */
}
```

* Opening braces on the same line as the last selector in the list

Bad:
```css
.selector-1,
.selector-2
{
  /* Declarations */
}
```

Good:
```css
.selector-1,
.selector-2 {
  /* Declarations */
}
```

* Closing braces on a different line

Bad:
```css
.selector-1,
.selector-2 {
  /* Declarations */ }
```

Good:
```css
.selector-1,
.selector-2 {
  /* Declarations */
}
```

* Place the closing brace of a ruleset in the same column as the first character of the ruleset

Bad:
```css
.selector {
  /* Declarations */
  }
```

Good:
```css
.selector {
  /* Declarations */
}
```

* Separate each rule set with a single blank line

Bad:
```css
.selector-1 {
  /* Declarations */
}
.selector-2 {
  /* Declarations */
}
```

Good:
```css
.selector-1 {
  /* Declarations */
}

.selector-2 {
  /* Declarations */
}
```

* Include one space on comma-separated values, after each comma

Bad:
```css
.selector-1 {
  background-image: url("images/my-lovely-face.png"),url("images/my-pink-background.png");
}

.selector-2 {
  background-image: linear-gradient(to top,yellow,pink);
  color: rgb(32,32,33);
}
```

Good:
```css
.selector-1 {
  background-image: url("images/my-lovely-face.png"), url("images/my-pink-background.png");
}

.selector-2 {
  background-image: linear-gradient(to top, yellow, pink);
  color: rgb(31, 32, 33);
}
```

* Use double quotes instead of single quotes

Bad:
```css
.selector {
  background-image: url('images/half-quote.jpg');
  content: '';
}
```

Good:
```css
.selector {
  background-image: url("images/half-quote.jpg");
  content: "";
}
```

### Selectors

* Write one selector per line

Bad:
```css
.selector-1, .selector-2, .selector-3 {
  /* Declarations */
}
```

Good:
```css
.selector-1,
.selector-2,
.selector-3 {
  /* Declarations */
}
```

* Quote attribute values in selectors

Bad:
```css
input[type=checkbox] {
  /* Declarations */
}
```

Good:
```css
input[type="checkbox"] {
  /* Declarations */
}
```

* Never use IDs, they aren't re-usable

Bad:
```css
#content {
  /* Declarations */
}
```

Good:
```css
.content {
  /* Declarations */
}
```

### Declarations

* Write one declaration per line

Bad:
```css
.selector {
  color: #fff; text-align: center; width: 20px;
}
```

Good:
```css
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* Include one space before each declaration value

Bad:
```css
.selector {
  color:#fff;
  text-align:center;
  width:20px;
}
```

Good:
```css
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* All declarations must end with a semi-colon, even the last one, to avoid error

Bad:
```css
.selector {
  color: #fff;
  text-align: center;
  width: 20px
}
```

Good:
```css
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* Use one level of indentation for each declaration

Bad:
```css
.selector {
  color: #fff;
    text-align: center;
    width: 20px;
}
```

Bad:
```css
.selector {
color: #fff;
text-align: center;
width: 20px;
}
```

Good:
```css
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* Don't use shorthand notations to set only one value

Bad:
```css
.selector {
  background: blue;
}
```

Good:
```css
.selector {
  background-color: blue;
}
```

* Zero values don't need units

Bad:
```css
.selector {
  margin: 0rem;
}
```

Good:
```css
.selector {
  margin: 0;
}
```

* Line height should also be unit-less, unless it is required to be a specific value for layout purposes. (The fact that line height can accept unit-less values and that this should be preferable is kind of old, [2006 old](http://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/))

Acceptable:
```css
.header {
  font-size: 1.2rem;
  line-height: 60px;
}
```

Default:
```css
.selector {
  font-size: .9rem;
  line-height: 1.2;
}
```

* Write lowercase values, except for font names
    * Use shorthand hex values

Bad:
```css
.selector {
  background-color: #FFFFFF;
  font-family: "Helvetica Neue", sans-serif;
}
```

Good:
```css
.selector {
  background-color: #fff;
  font-family: "Helvetica Neue", sans-serif;
}
```

* Long, comma-separated property values (eg. gradients or shadows) can be arranged across multiple lines in an effort to improve readability and produce more useful diffs. In this case:
    * All values should be in a new line
    * Indentation of each value must be one level deeper than the declaration
    * Commas should be at the end of each property
    * The last property must end with the declaration's semi-colon

Acceptable:
```css
.selector {
  box-shadow: 0 2px 2px #ccc, 0 -2px 2px #ccc;
}
```

Bad:
```css
.selector {
  box-shadow: 0 2px 2px #ccc,
  0 -2px 2px #ccc;
}
```

Good:
```css
.selector {
  box-shadow:
    0 2px 2px #ccc,
    0 -2px 2px #ccc;
}
```

* Declarations should be ordered alphabetically.

Example:
```css
.selector {
  background-color: #000;
  background-image: url("images/bg.jpg");
  background-position: center;
  background-repeat: no-repeat;
  border: 10px solid #333;
  box-sizing: border-box;
  display: inline-block;
  font-family: sans-serif;
  font-size: 16px;
  height: 100px;
  margin: 10px;
  overflow: hidden;
  padding: 10px;
  width: 100px;
}
```

### Vendor Prefixes
Don't add any declarations with them, use something like [PostCSS' Autoprefixer](https://github.com/postcss/autoprefixer). This way you only have to worry about the support of a given property.

### Media Queries
All the `@media` rulesets should be placed after each rule with the declarations that override/extend that rule.

Example:
```css
.select-1 {
    color: #000;
    text-align: center;
}

@media (min-width: 800px) {
    .select-1 {
        text-align: left;
    }
}

.selector-2 {
    display: block;
    width: 100%;
}

@media (min-width: 800px) {
    .selector-2 {
        display: inline-block;
        width: 30%;
    }
}
```

Default styles should be mobile-first, with variations/corrections added with media queries conditioned with `min-width`. However, the use of `max-width` is encouraged if it results in easier code to read and maintain.

## Sass

In writing SCSS the above, plus all that follows, should be taken into account.

### Declaration ordering

1. `$variable` overrides **always** on top
2. `@extend`
3. `@include`
4. Regular declarations (allows for overriding)
    5. Mixins with content blocks (`@media` declarations included here)
6. Selectors that target itself:
    1. pseudo-classes
    2. pseudo-elements
    3. component states
5. Nested declarations

Each of these items should be separated from the next by an blank line.

### Nesting

While nesting is great, too much of it can make the code harder to read than plain boring ol' CSS. Also, it creates excessive over specificity which results in greater specificity when overriding styles. As a rule, nesting should be avoided as much as possible.

**Nesting required:** when it always makes the code easier to read
* pseudo-classes
* pseudo-elements
* component states
* media queries

**Nesting can be used:** on some coding styles like [RSCSS](https://github.com/rstacruz/rscss)

### File structure

* Each logical module of code should live in its own file. Avoiding multiple objects in the same file allows for the use of the filesystem as a means to navigate the styles rather than relying on comments.
* The following should always have a file of their own:
    * Variables
    * Functions
    * Mixins
    * Placeholders
* Files should be named for easy grasp of their contents
* All files should be partials, their name should start with an underscore `_`, except if the file is processed to a CSS file
* If possible the files that generate the compiled CSS should never have anything other than `@import` statements and comments

#### Folder structure

In most projects multiple Functions and Mixins will for sure exist. Considering this, the following structure should be the backbone for any project:

```
/styles
|-/functions
| |- _calc-awesome.scss
|  - _catch-fire.scss
|-/mixins
| |- _button.scss
| |- _media-queries.scss
|  - _positioning
|- _variables.scss
 - main.scss
```

### Functions

### Mixins

### Definitions

## Resources

Most of what is here is not original – probably everything. We built this from analyzing and learning with others, below you will find our sources resources and other may appear along the document for a particular guideline. This document is our brand of [guidelines/rules of thumb/experience/magic dust] mixture and we'll evolve it along with our needs.

* [WordPress CSS Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/css/)
* [Principles of writing consistent, idiomatic CSS](https://github.com/necolas/idiomatic-css)
* [Principles for writing consistent, clean, friendly Sass](https://github.com/anthonyshort/idiomatic-sass)
