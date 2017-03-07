## Ternary formatting

When using ternaries, if they exceed the length of virtual limit for a line, they should be broken using the following pattern.

```php
// On a variable attribution.
$variable = ( <condition> )
    ? true
    : false;

// As a formal parameter to a function.
printf(
    '<p>%s</p>',
    ( <condition> )
    ? 'true'
    : 'false'
);
```
