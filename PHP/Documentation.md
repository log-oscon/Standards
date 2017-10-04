# Documentation

Generally, follow the WordPress rules on [inline documentation](https://make.wordpress.org/core/handbook/best-practices/inline-documentation-standards/php/).

For ease of reference, the most important points of the previous standards are described here as well.

## Language
All documentation **must be written in english**.

## General
DocBlocks should directly precede the hook, action, function, method or class line. There should not be any opening/closing tags or other things between the DocBlock and the declarations.


## Description (short and long descriptions)
HTML markup should never be used outside of code examples, though Markdown can be used.

All descriptions should be **clear, simple and brief**. Avoid describing *why* an element exists, rather, focus on documenting *what* and *when* it does something.

All sentences should end with a full stop symbol.

Always conjugate verbs in the singular third-person.

```php
// Yes.
(it) Does something.

// No.
(it) Do something.
```


## Examples

```php
/**
 * Class description.
 *
 * @since x.y.z
 * @package ClientName
 * @author log.OSCON, Lda. <engenharia@log.pt>
 */

/**
 * Variable or Constant description.
 *
 * @since x.y.z
 * @var   (type)
 */

/**
 * Method description.
 *
 * @since  x.y.z
 * @param  (type)  $param_name  Parameter description.
 * @return (type)               Return value description.
*/
```

