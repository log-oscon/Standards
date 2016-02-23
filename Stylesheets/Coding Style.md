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

### Format

* Use soft-tabs with a two space indent. Spaces are the only way to guarantee code renders the same in any person’s environment.
* Include one space before the opening braces.

```css
/* Bad */
.selector-1,
.selector-2{
  /* Declarations */
}

/* Good */
.selector-1,
.selector-2 {
  /* Declarations */
}
```

* Opening braces on the same line as the last selector in the list.

```css
/* Bad */
.selector-1,
.selector-2
{
  /* Declarations */
}

/* Good */
.selector-1,
.selector-2 {
  /* Declarations */
}
```

* Closing braces on a different line.

```css
/* Bad */
.selector-1,
.selector-2 {
  /* Declarations */ }

/* Good */
.selector-1,
.selector-2 {
  /* Declarations */
}
```

* Place the closing brace of a ruleset in the same column as the first character of the ruleset.

```css
/* Bad */
.selector {
  /* Declarations */
  }

/* Good */
.selector {
  /* Declarations */
}
```

* Separate each rule set with a single blank line.

```css
/* Bad */
.selector-1 {
  /* Declarations */
}
.selector-2 {
  /* Declarations */
}

/* Good */
.selector-1 {
  /* Declarations */
}

.selector-2 {
  /* Declarations */
}
```

* Use double quotes instead of single quotes.

```css
/* Bad */
.selector {
  background-image: url('images/half-quote.jpg');
  content: '';
}

/* Good */
.selector {
  background-image: url("images/half-quote.jpg");
  content: "";
}
```

* Include one space on comma-separated values, after each comma.

```css
/* Bad */
.selector-1 {
  background-image: url("images/my-lovely-face.png"),url("images/my-pink-background.png");
}

.selector-2 {
  background-image: linear-gradient(to top,yellow,pink);
  color: rgba(32,32,33,.5);
}

/* Good */
.selector-1 {
  background-image: url("images/my-lovely-face.png"), url("images/my-pink-background.png");
}

.selector-2 {
  background-image: linear-gradient(to top, yellow, pink);
  color: rgba(31, 32, 33, .5);
}
```

* Use hex color codes `#000` unless using `rgba()` in raw CSS. Although it's not much, it allows for a given color to be specified with less characters, reducing the final file size without any loss of specificity as both method map the same color space. (*Note:* SCSS’ `rgba()` function is overloaded to accept hex colors as a parameter.)

```scss
/* Bad */
.selector {
    background-color: rgba(255, 221, 102, .8);
    color: rgb(0, 136, 255);
}

/* Good */
.selector {
    background-color: rgba(255, 221, 102, .8);
    color: #08f;
}

// SCSS
.selector {
    background-color: rgba(#fd6, .8);
}
```

### Selectors

* Write one selector per line.

```css
/* Bad */
.selector-1, .selector-2, .selector-3 {
  /* Declarations */
}

/* Good */
.selector-1,
.selector-2,
.selector-3 {
  /* Declarations */
}
```

* Quote attribute values in selectors.

```css
/* Bad */
input[type=checkbox] {
  /* Declarations */
}

/* Good */
input[type="checkbox"] {
  /* Declarations */
}
```

* Never use IDs, they aren't re-usable.

```css
/* Bad */
#content {
  /* Declarations */
}

/* Good */
.content {
  /* Declarations */
}
```

### Declarations

* Write one declaration per line.

```css
/* Bad */
.selector {
  color: #fff; text-align: center; width: 20px;
}

/* Good */
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* Include one space before each declaration value.

```css
/* Bad */
.selector {
  color:#fff;
  text-align:center;
  width:20px;
}

/* Good */
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* All declarations must end with a semi-colon, even the last one, to avoid error.

```css
/* Bad */
.selector {
  color: #fff;
  text-align: center;
  width: 20px
}

/* Good */
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* Use one level of indentation for each declaration.

```css
/* Bad */
.selector {
  color: #fff;
    text-align: center;
    width: 20px;
}

/* Bad */
.selector {
color: #fff;
text-align: center;
width: 20px;
}

/* Good */
.selector {
  color: #fff;
  text-align: center;
  width: 20px;
}
```

* Don't use shorthand notations to set only one value.

```css
/* Bad */
.selector {
  background: blue;
}

/* Good */
.selector {
  background-color: blue;
}
```

* Zero values don't need units.

```css
/* Bad */
.selector {
  margin: 0rem;
}

/* Good */
.selector {
  margin: 0;
}
```

* Line height should also be unit-less, unless it is required to be a specific value for layout purposes. (The fact that line height can accept unit-less values and that this should be preferable is kind of old, [2006 old](http://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/).)

```css
/* Acceptable */
.header {
  font-size: 1.2rem;
  line-height: 60px;
}

/* Default */
.selector {
  font-size: .9rem;
  line-height: 1.2;
}
```

* Write lowercase values, except for font names.
    * Use shorthand hex values.

```css
/* Bad */
.selector {
  background-color: #FFFFFF;
  font-family: "Helvetica Neue", sans-serif;
}

/* Good */
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

```css
/* Acceptable */
.selector {
  box-shadow: 0 2px 2px #ccc, 0 -2px 2px #ccc;
}

/* Bad */
.selector {
  box-shadow: 0 2px 2px #ccc,
  0 -2px 2px #ccc;
}

/* Good */
.selector {
  box-shadow:
    0 2px 2px #ccc,
    0 -2px 2px #ccc;
}
```

* Declarations should be ordered alphabetically.

```css
/* Example */
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

```css
/* Example */
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

```css
/* Example */
@media (max-width: 480px) {
    .mobile-prevent-scroll {
        /* Declarations */
    }
}
```

### Don't use `@import`

Compared to `<link>`, `@import` is slower, adds extra page requests, and can cause other unforeseen problems. Since we use Sass we don't really require any action, because the `@import` statement will include the contents on the compiled CSS file. However, if Sass or any other pre-processor are not an option you should opt for an alternate approach:

* Use multiple <link> elements.
* Concatenate your CSS files with features provided in Rails, Jekyll, and other environments.

For more information, [read this article by Steve Souders](http://www.stevesouders.com/blog/2009/04/09/dont-use-import/).


### Naming Classes

We follow the general principles of [Block Element Modifier (BEM)](https://en.bem.info/) with our twist to make things fit our development needs. The selector types that we have are very similar to BEM, and we support both boolean modifiers and key-value modifiers.
The main differences lay in the fact that we separate modifier names with a double hyphen (`--`) and modifier values with a single hyphen (`-`). Also, we don't use multiple word modifiers, either for their names or their values (in the key-value scenario).

To define our BEM entities we use the following string format:
```
block[--blockModName[-modVal]][__element[--elementModName[-modVal]]]
```
*Note:* camelCase is used to avoid confusion in the representation of the string parts. Its use is not endorsed by this style guide.

Rules for each part of the string:
* `block` and `__element` - The name of the block and element, respectively. Can be a multiple word name with hyphens between words.
* `--blockModName` and `--elementModName` - Block and element boolean modifier name or modifier key, respectively. Must be a single word, no hyphens or underscores.
* `-modVal` - Modifier's value in key-value format. Must be a single word, no hyphens or underscores.

Available selector variations:
* `block` - The block.
* `block--blockModName` - The block with a boolean modifier.
* `block--blockModName-modVal` - The block with a key-value modifier.
* `block__element` - The element inside the block.
* `block--blockModName__element` The element inside the block with a boolean modifier.
* `block--blockModName-modVal__element` - The element inside the block with a key-value modifier.
* `block__element--elementMod` - The element with a boolean modifier inside the block.
* `block--blockModName__element--elementMod` - The element inside the block, both with a boolean modifier.
* `block--blockModName-modVal__element--elementMod` - The element with a boolean modifier inside the block with a key-value modifier.
* `block__element--elementMod-modVal` - The element with a key-value modifier inside the block.
* `block--blockModName__element--elementMod-modVal` - The element with a key-value modifier inside a block with a boolean modifier.
* `block--blockModName-modVal__element--elementMod-modVal` - The element inside the block, both with a key-value modifier.

#### State classes

A state is something that augments the current module e a very specific way, not necessarily in the properties it defines, but in the resulting output. Forms are a particular example where there will be state classes for sure. When a form field has errors or the field was filled successfully classes like `.is-success` or `.is-error` will bring styles to the element highlighting this state.

These classes, given that their job is to force a given style over everything else, may use `!important`, but only if there is no other way to be sure their styles will always override the ones from the element. When, using `!important`, there must be a comment stating the reason.

* Never create a ruleset with a selector composed of just the State Class, this makes it so there are no "default" properties for that class and avoids problems if (god forbid) the need to use `!important` arises.
* Avoid, with all your might, the use of `!important` in the declarations.
* Always comment the declarations where you failed to not use `!important`.

```css
/* Bad */
.is-error {
    border-color: red;
    color: red !important;
}

/* Good */
.selector.is-error {
    border-color: red;
    color: red !important; /* Very important reason. */
}
```

#### Interaction Classes

Class names starting with `js-` (e.g. `.js-search-toggle`). **These classes must never be styles**, they serve as bindings for JavaScript events and allow styles to be completely changed, including class names, without without any loss of functionality.

```css
/* NEVER DO THIS */
.js-search-toggle {
    background-color: pink;
    border-radius: 3px;
    color: white;
    font-weight: bold;
    padding: 10px;
}
```

#### Helper Classes

These classes should be added according to the projects needs. **Strive to have zero helper classes**, they should be like a transient state of the code, something like a new modifier or state class.

* The first character should always be a hyphen `-`.
* When naming, the property and its value should be explicit in the name.
* The names should consist of a single word. Two words are accepted for variations of the same helper or to give more information (e.g. `.-text-blue`).
* They should not declare more than a property.
* They can be used interactively (added through JavaScript), although State Classes are preferable, or to extend/override an element's property in a situation where using a modifier seems excessive.
* They should never be used where State Classes apply.
* Given their "short nature" (only one declaration per helper class) these rules should be written inline.
* *SCSS:* They should never be `@extend`ed on any other selector.

```css
/* Examples */
.-text-blue { color: blue; }

.-text-green { color: green; }

.-inline { display: inline; }

.-hidden { display: none; }

.-visible { display: block; }
```

### Location-based Styling

Never use it. We code in WordPress, and there are many temptations to override or extend a given class based on a specific class that WordPress attaches to a page (post-type, single, front-page, home-page, to name a few), but try not to. Add a modifier class to your block based on its location and apply your overrides/extensions to that class.
(Outside the WordPress environment the advice is the same!)

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

### Operators

For improved readability, wrap all math operations in parentheses with a single space between values, variables, and operators.

```scss
// Bad example
.element {
  margin: 10px 0 @variable*2 10px;
}

// Good example
.element {
  margin: 10px 0 (@variable * 2) 10px;
}
```

### Nesting

While nesting is great, too much of it can make the code harder to read than plain boring ol' CSS. Also, it creates excessive over specificity which results in greater specificity when overriding styles. As a rule, nesting should be avoided as much as possible.

* Nesting should not be **deeper than 3 levels**. If it can't be helped, step back and rethink the overall strategy.

* **Nesting required** when it always makes the code easier to read
    * pseudo-classes
    * pseudo-elements
    * component states
    * media queries

* **Nesting can be used** on some coding styles like [RSCSS](https://github.com/rstacruz/rscss)

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
|--/vendor
|--/functions
|  |-- _calc-awesome.scss
|   -- _catch-fire.scss
|--/mixins
|  |-- _button.scss
|  |-- _media-queries.scss
|   -- _positioning
|-- _variables.scss
 -- main.scss
```

* `vendor/`: contains all of the CSS from outside your codebase, usually relating to JavaScript dependencies.
* `functions/`: contains all of your Sass functions.
* `mixins/`: contains all of your Sass mixins.
* `_variables.scss`: contains all of your global variables.
* `main.scss`: used to import everything needed to generate the output CSS file.

### Functions

### Mixins

### Definitions

## Resources

Most of what is here is not original – probably everything. We built this from analyzing and learning with others, below you will find our sources resources and other may appear along the document for a particular guideline. This document is our brand of [guidelines/rules of thumb/experience/magic dust] mixture and we'll evolve it along with our needs.

* [WordPress CSS Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/css/)
* [Principles of writing consistent, idiomatic CSS](https://github.com/necolas/idiomatic-css)
* [Principles for writing consistent, clean, friendly Sass](https://github.com/anthonyshort/idiomatic-sass)
* [How we do CSS at Ghost](https://dev.ghost.org/css-at-ghost/)
* [Code Guide by @mdo](http://mdo.github.io/code-guide/#css)
* [BEM. Block Element Modifier](https://en.bem.info/)
