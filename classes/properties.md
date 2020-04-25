# Properties & Methods

## What are Properties & Methods?

**Variables** inside Class are called as **Properties**.

Variables helps to define elements of a class.

```php
Class Car {

    private $car_name;

    private $car_model;

    private $car_type;
}
```

**Functions** inside Class are called as **Methods**.

Methods helps to perform some action in the Class.

```php
Class Car {

    function getModel(){

        echo "Model of the car is Accord" . PHP_EOL;
    }

    function getName(){

        echo "Name of the car is Honda" . PHP_EOL;
    }

    function getType(){

        echo "Type of the car is Sedan" . PHP_EOL;
    }
}
```

## How to define Methods with parameters and return values?

```php
<?php

class Files
{
    function displayContent($file): bool
    {
        $result = true;

        try {
            echo "Read contents from the file: $file" . PHP_EOL;

            $content = file_get_contents($file);

            echo "Displaying contents of the file:" . PHP_EOL;

            echo $content. "<hr>";
        } catch (Exception $e) {
            $result = false;
        }

        return $result;
    }
}

$file1 = new Files;

$file1->displayContent('test.txt');

$file2 = new Files;

$file1->displayContent('test2.txt');
```

## What is \$this keyword?

**\$this** keyword allows us to access properties & methods of same class.

**\$this** indicates instance of this class.

You don't have to declare **\$this** keyword.

## How to chain methods and properties?

```php
<?php

Class ChainMethods() {

    public $name;

    function method1() {
        echo "This is from method 1". PHP_EOL;
        $this->name = "Chain Methods";
        return $this;
    }

    function method2() {
        echo "This is from method 2 ($this->name)". PHP_EOL;
        return $this;
    }
}

$cm = new ChainMethods();
/**
 * This is chain and should call in sequence
 */
$cm->method1()->method1()->name;
```