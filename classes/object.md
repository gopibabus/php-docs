# Objects

## What are Objects?

**Objects** are used to access Properties and Methods of a Class.

Objects are called as **Instance of a Class**.

We can create unlimited Objects for a Class.

We should create an Object of a Class to access Properties and call Methods of a Class.

Each Object properties are unique to that specific instance of a Class.

```php
Class Car {

    public $car_name;

    function getName(){

        echo "Name of a Car is Honda" . PHP_EOL;
    }
}

$hondaCar = new Car();
$hondaCar->car_name = 'Honda';
$hondaCar->getName();
```

## How to define Objects and call methods and properties?

We create object using keyword **new**

We call methods and properties of class using object operator called **->**

```php
<?php

Class Car {

    public $name;
    public $color;

    function getCarInfo(){
        return $this->name.' '.$this->color;
    }
}

$car1 = new Car();
$car1->name = "Honda";
$car1->color = "Black";
echo $car1->getCarInfo();

$car2 = new Car();
$car2->name = "Accura";
$car2->color = "White";
echo $car2->getCarInfo();
```

## How to clone a Object?

```php
<?php

class Posts {
    public $post;

    function __construct($post)
    {
        $this->post = $post;
    }
}
$post1 = new Post("First Post");

$post2 = $post1; #Copy by Reference
$post1->post= 'Second Post';
echo $post1->post; #Second Post
echo $post2->post; #Second Post

$post2 = clone $post1; #Copy by value(Cloning)
$post1->post= 'Third Post';
echo $post1->post; #Third Post
echo $post2->post; #Second Post
```

## How to serialize and unserialize a Object?

```php
<?php

class Posts {
    public $post;

    function __construct($post)
    {
        $this->post = $post;
    }
}

$post1 = new Post("First Post");
$serializedPost1 = serialize($post1); #Snapshot of a Object with values
echo $serializedPost1;
file_put_contents("post1.txt", $serializedPost1);

$unserializedPost1 = file_get_contents('post1.txt');
$post11 = unserialize($unserializedPost1);
echo $post11->post; #First Post
```

## How to cache a Object?

```php
<?php

class PhpCache {
    protected $path = null;
    protected $duration = null;

    function __construct ( $path, $duration = 60) {
        $this->path = $path;
        $this->duration = $duration;
    }

    function get( $id ) {
        $file = $this->path . $id . '.cache';
        if (file_exists($file) && time() - filemtime($file) < $this->duration) {
            return unserialize( file_get_contents($file) );
        } else {
            return null;
        }
    }

    function set( $id, $obj) {
        $file = $this->path . $id . '.cache';
        file_put_contents($file, serialize($obj));
    }
}


$cache = new PhpCache(dirname(__FILE__).'\\cache\\', 600);
$key = 'mykey';
$value = $cache->get($key);
if ($value == null) {
    $value = 'new value';
    $cache->set($key, $value);
    echo 'created ' . $value;
} else {
    echo 'got ' . $value;
}
```

## How to compare Objects?

```php
<?php

    /**
     * Identity Operator (===)
     */
    function compare1(&$obj1, &$obj2) {
        if($obj1 === $obj1) {
            return true;
        } else {
            return false;
        }
    }

    /**
     * Comparison Operator (==)
     */
    function compare2(&$obj1, &$obj2) {
        if($obj1 == $obj1) {
            return true;
        } else {
            return false;
        }
    }

class Posts {
    public $post;

    function __construct($post)
    {
        $this->post = $post;
    }
}

$post1 = new Posts('First Post');
$post2 = new Posts('First Post');

echo compare1($post1, $post2) ? 'Same' : 'Different'; # Different
echo compare2($post1, $post2) ? 'Same' : 'Different'; # Same
```

## How to iterate Objects?

```php
<?php

class Posts {
    public $post;
    public $hasPosts = true;

    function __construct($post)
    {
        $this->post = $post;
    }

    function hello() {
        echo "Hello!!!";
    }
}

$post1 = new Posts('First Post');

/**
 * Method 1
 * Print all properties with values
 */
foreach ($post1 as $key => $value) {
    echo $key. '=>' . $value;
}

/**
 * Method 2
 * Print all properties with values
 */
var_dump($post1);
```