# Static Methods & Properties

## What are static methods and properties?

If we can access class methods or properties without creating an instance of a class then they are called as **static methods or static properties**.

Methods and properties which are marked as static can be accessed with class names directly with help of **Scope resolution operator (::)**.

**Example:** Car::applyBreak( );

```php
<?php

class Car {
    static public $name = "Accord";
    static public function getModel() {
        echo "Honda Accord";
    }
}

echo Car::$name;
Car::getModel();
```

## Why we can't use $this over static methods & static properties?

**$this** is nothing but object of a given class and static methods and static properties are not accessible with instance of a object.

PHP introduced keyword called **self** to access **static properties and static methods** inside a given class.

```php
<?php

class Calculator {
    static public $result;

    static function add($a, $b) : int {
        self::$result = $a + $b;
        return self::$result;
    }
}

echo Calculator::add(12, 23);
```

## Example: Static properties & Static Methods

```php
<?php

class FilesHelper {

    static function hasData($filename) : bool {

        if(!file_exists($filename)) {
            echo "$filename does not exists";
            return false;
        }

        $content = file_get_contents($filename);

        if(empty($content)) {
            return false;
        } else {
            return true;
        }
    }
}

if(FilesHelper::hasData("Test.txt")) {
    echo "Data found";
}
```