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

?> From PHP 7.4, class properties can be typed.

```php
<?php

class BankAccount {
    private int $id;
    private Money $balance;
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

?> Added in v7.0

```php

function getPost(int $postId): Post {
 //
}

```

**Union Types**

?> Added in v8.0

```php

function updateTotal(int|float $cost) {
 //
}

```


**Null and Void return types**

?> Added in v7.1

```php

// Notice the `?` before the type
function getPost(int $postId): ?Post {
 // can return null
}
function setPostTitle(int $postId, string $title): void {
  persistInDB($postId, $postTitle);
 // won't return anything, or optionally can do:
 // `return;`
}

```

**Never return type**

?> Added in v8.1

```php

function notImplemented(): never {
  throw new Exception('Not implemented');
}

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
