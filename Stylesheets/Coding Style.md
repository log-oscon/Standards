# Coding Style

We mainly use SASS (mainly written as SCSS) as a pre-processor to generate the final CSS styles for each project. As a result, our CSS coding style mixes with the SASS and on the following document we try to give this distinction by pointing to what only applies to SASS (in general because it is invalid CSS).

## General principles

If you follow nothing else at least don't forget these next few lines.

> "Part of being a good steward to a successful project is realizing that writing code for yourself is a Bad Idea™. If thousands of people are using your code, then write your code for maximum clarity, not your personal preference of how to get clever within the spec." - Idan Gazit

* **All code should look like a single person wrote it, even when many actually did.** This ensures that anyone coming in to the project later on for whatever reason (correct a bug, extend functionality, help with development, etc.) will be able to understand and contribute in a single voice.
* Code readability should come first and optimization second.
* When in doubt about a style raise the question for debate and proceed with existing common patterns (share these patterns when with your question).
* Enforce the agreed-upon style, always. Code review is a particular example where this is almost mandatory.

## Syntax an Formatting
This probably the main reason why code feels like it was written by different people. By keeping the syntax and formatting the code in a clean way maintaining and debugging the code become easier tasks.

### Syntax
* Write one selector per line
* Write one declaration per line
* Opening braces on the same line as the last selector in the list
* Closing braces on a different line

Bad:
```
.selector-1, .selector-2, .selector-3 {
    background-color: blue; color: yellow;
    height: 150px;
    width: 100px; }
```

Good:
```
.selector-1,
.selector-2,
.selector-3 {
    background-color: blue;
    color: yellow;
    height: 150px;
    width: 100px;
}
```

* Include one space before the opening braces
* Include one space before each declaration value
* Include one space after each comma on comma-separated values

Bad:
```
.selector-1,.selector-2,.selector-3{
    color: blue;
    box-shadow:0 1px 2px #000,2px 1px 2px #999;
}
```

Good:
```
.selector-1,
.selector-2,
.selector-3 {
    color: blue;
    box-shadow: 0 1px 2px #000, 2px 1px 2px #999;
}
```

* Use lowercase for all values, except font names
* Zero values don't need units
* All declarations must end with a semi-colon, even the last one, to avoid error
* Use single quotes instead of double quotes
* Don't use shorthand notations to set only one value

### Format
* Indentation should be in spaces, two for each level (Editor Config's dotfile should be used, if possible)
* SASS: nested declarations must have an empty line before the selector list if:
    * The parent as @extend, @include or regular declarations
    * There are other nested declarations before

#### Declaration ordering
Declarations should be ordered alphabetically or by type (Positioning, Box model, Typography, Visual). Whichever is chosen, it must be consistent across all files in the project.

SASS:
1. @extend
2. @include
3. Regular declarations (allows for overriding)
4. Nested declarations

#### SASS: Nesting
While nesting is great, too much of it can make the code harder to read than plain boring ol' CSS. Also, it creates excessive over specificity which results in greater specificity when overriding styles. As a rule, nesting should be avoided as much as possible.

**Nesting required:** when it always makes the code easier to read:
* pseudo-classes
* pseudo-elements
* component states
* media queries

**Nesting can be used:** on some coding styles like [RSCSS](https://github.com/rstacruz/rscss)
