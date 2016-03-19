# Documentation

Great code always has comments and documentation. No matter how well crafted your rules and naming conventions are, comments can give more insight than any of them. However, excessive documentation can also burry your team in a hey stack, and for this not to happen we follow certain guidelines to make comments and documentation (which are also comment text, but have a more formatted structure) as lean and information packed as possible.

## Comments

* When using comments the rules are the same for both CSS and SCSS, except for how they are written. CSS comments are surrounded by `/* */` and SCSS simply start after `//`.

```scss
/* CSS comment here. */

// SCSS comment here.
```

* No SCSS comment should ever be written like a CSS comment. If the project has a pre-processor we don't need the comments to be in the compiled CSS files. (**An exception** is the WordPress required `styles.css` header, so that comment must be in *CSS mode*.)

```scss
/* Bad comment */
.selector {
    color: black;
    font-size: 1.2rem;

    // Good comment
    .child {
        color: red;
        font-size: .9em;
        text-align: right;
    }
}
```

* Ideally all files have a name that defines its content, so using a "heading" comment to separate rules should be useless. However, if there is a need for such a divider it should preferably have more than just the title, advancing a simple description and relevant notes.

```scss
/*
Heading Comment in CSS

With a simple, but totally informative description of the content below.
It may also contain notes and other types of relevant information.
*/

.selector {
    /* Declarations */
}

//
// Heading Comment in SCSS
//
// With a simple, but totally informative description of the content below.
// It may also contain notes and other types of relevant information.

.selector {
    // Declarations
}
```

## Documentation

In order to have both CSS and SCSS documentation using the same system, we use [KSS (Knyle Style Sheets)](https://github.com/kneath/kss/blob/master/SPEC.md), which also generate styleguides from the resulting documentation blocks. These blocks are both easy for humans to read and structured enough for a "machined" extraction of information.

* When writing on CSS the block comment's content should be in between the CSS comment tags.

```css
/*
Documentation block goes here.
*/
```

* SCSS uses the `//` before each of the lines of the documentation block.

```scss
// Documentation line 1
// Documentation line 2
// ...
```

* There are essentially two types of blocks:
    * Those that document style and end up generating the contents of the style guide (both exist in CSS and SCSS).
    * Those that document a SCSS mixin of function (naturally these only exist in SCSS).

```scss
//
// Examples
//

/*
A button suitable for giving stars to someone.

:hover             - Subtle hover highlight.
.stars-given       - A highlight indicating you've already given a star.
.stars-given:hover - Subtle hover highlight on top of stars-given styling.
.disabled          - Dims the button to indicate it cannot be used.

Styleguide 2.1.3.
*/
a.button.star{
  ...
}
a.button.star.stars-given{
  ...
}
a.button.star.disabled{
  ...
}

// Creates a linear gradient background, from top to bottom.
//
// $start - The color hex at the top.
// $end   - The color hex at the bottom.
//
// Compatible in IE6+, Firefox 2+, Safari 4+.
@mixin gradient($start, $end){
  ...
}
```
