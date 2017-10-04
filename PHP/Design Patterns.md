## Levels of Visibility
The three levels define whether a property or method can be accessed outside of the class, and in classes that extend the class.

#### Public
This level permits a property or method to be called in any scope.
#### Protected
Protected properties or methods can be accessed form inside the class they are declared, or in any class that extends them. They can't be accessed from outside the class or subclass.
#### Private
The more restrictive visibility mode. Private properties or methods can't be accessed by a subclass of the class it is defined in.

## Rules of Visibility
Properties should be *protected* or *private*. It depends if the class will be extended or not.

Methods may have the three levels of visibility.

```php 
// Yes.
private $name;

// Yes.
protected $name;

// No.
public $name;
```
You must access properties through *getter* and *setter* methods.
```php
public function get_name() {
    return $this->name;
}

public function set_name( $value ) {
    $this->name = $value;
}
```

## Abstract Classes
Avoid code redundancy with this principle. This also enforces a particular pattern in the code. 

**But beware that inheritance must comply to the context of the abstract class.**



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
