# Coding Style

Unless otherwise mentioned, we follow the [WordPress PHP Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/php/) and [PSRs](http://www.php-fig.org/psr/).

We also have our own standards for things that aren’t covered by the standards mentioned above, such as namespacing and general project structure.

For ease of reference, the most important points of the previous standards are described here as well.


## File Layout

PHP files should **either** declare symbols (classes, functions, etc) **or** run code (function calls, etc), but not both.

Each class should be in its own file, which should not declare any other functions (outside the class scope) or classes.

Generally, the file should follow the following order:

- `namespace` declaration
- `use` declarations
- `const` declarations
- `require` when allowed
- Declarations or run code


## File Naming

Namespaces are mapped to filesystem directories after lowercasing. Part of the namespace may be excluded from the directory structure, ala PSR-4. For example, a class with the namespace `logoscon\WP\Plugin\Example` could live in the `lib/` directory without the `logoscon\WP\Plugin` part.

Contrary to the WordPress coding standards we do not name our classes like `class-<classname>.php`. 

The main file for plugins should live in `<plugin-slug>.php` (typically, the folder name) in the plugin’s directory, while the main file for themes is `functions.php` in the theme directory. This file should be the only one to contain run code. This file should also register necessary autoloaders.

Underneath the top-level directory (either the plugin directory or the theme directory) should be a `lib` directory which represents the top-level namespace for the plugin/theme.

As an example, for a plugin called “logoscon-foobar” with a namespace of `logoscon\WP\Plugin\FooBar`, the directory structure should look like this:

- `logoscon-foobar.php` 
- `lib/` - Contains PHP code for `logoscon\WP\Plugin\FooBar` namespace
  - `Plugin.php` - Defines the core plugin class
  - `I18n.php` - Define the internationalization functionality


## Namespace and Class Naming

Namespaces should be logical groupings of related functionality. Typically, this means along feature lines, not along technology lines. 

Namespaces and classes should be named with [CamelCase][1]. Avoid lowercase and the use of underscores.

Reusable code should be prefixed with `logoscon\`. Project names starting with “logoscon-“ should be sub-namespaces of `logoscon\`: if the project is called “logoscon-foobar”, the namespace should be `logoscon\FooBar`.

Client projects or products should generally use their own namespace (e.g. `AwesomeClient\`) rather than under the `logoscon` namespace.

Classes used in a namespaced file should have a `use` statement at the top of the file to allow a quick overview of what is used, and to avoid long absolute references to the classes throughout the file. If you have a lot of functionality from given namespace, you can `use` the entire namespace to avoid excessive `use` statements.

`use` statements should never start with a `\`; these are not required, as the namespaces here are already absolute.

```php
// No:
$x = \AwesomeClient\WP\Something::method();

// No:
use \AwesomeClient\WP\Something;
$x = Thing::method();

// Yes:
use AwesomeClient\WP\Something;
$x = Something::method();

// Allowed:
use AwesomeClient\WP;

$x = Something::method();
$y = WP\Other::thing();
```


## Yoda Conditions
> Yoda conditions are dumb and solve the wrong problem. You have my permission to **not** use Yoda conditions.
> 
> by Ryan McCue


## Single and Double Quotes
Usage of quotation marks (double quotes) ir restricted to HTML attributes or when evaluating anything inside the string. Otherwise you should always use single quotes.

```php
// No:
echo "<a href='/static/link' title='Yeah yeah!'>Link name</a>";

// Yes:
echo '<a href="/static/link" title="Yeah yeah!">Link name</a>';

// No:
$option_block = \get_option( 'options_block' . $this->language );

// Yes:
$option_block = \get_option( "options_block{$this->language}" );
```


## Indentation
Your indentation should always reflect logical structure. Use **real tabs** and not spaces.

Exception: if you have a block of code that would be more readable if things are aligned, use spaces:
```php
$foo   = 'somevalue';
$foo2  = 'somevalue2';
$foo34 = 'somevalue3';
$foo5  = 'somevalue4';
```

## References
- [Human Made - PHP Style Guide](http://engineering.hmn.md/how-we-work/style/php/)
- [10up Engineering Best Practices - PHP](https://10up.github.io/Engineering-Best-Practices/php/)

[1]: https://en.wikipedia.org/wiki/Camel_case
