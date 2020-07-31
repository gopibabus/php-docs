# 🔥Traits

### ❇What are Traits?

**Limitation:** You cannot extend more than one class.

!> **Multiple Inheritance** is not possible in PHP. To address this issue PHP introduced concept called **Traits**, Where we can include multiple traits into a given class.

?> A **Trait** enable a developer to reuse sets of methods freely in several independent classes living in different class hierarchies.

## ⚡Use Cases of Traits

>**AWS** uses them in their PHP SDK codebase.

### ❇Using single trait

?> Following trait __MyTrait__ provides a method called **hello()** which allows to print _hello world_. MyClass used the trait __MyTrait__ to use method hello() to print _hello world_ .

```php
trait MyTrait
{
    public function hello()
    {
        print "hello world" . PHP_EOL;
    }
}


class MyClass
{
    use MyTrait;
}

$myObj = new MyClass();
$myObj->hello();
```

### ❇Using multiple traits

```php
trait Trait1
{
    public function hello()
    {
        print "hello ";
    }
}

trait Trait2
{
    public function world()
    {
        print "world";
    }
}

class MyClass
{
    use Trait1;
    use Trait2;
}

$myObj = new MyClass();
$myObj->hello();
$myObj->world();
```

### ❇Traits Within Traits

```php
trait Trait1
{
    public function hello()
    {
        print "hello ";
    }
}

trait Trait2
{
    use Trait1;

    public function world()
    {
        print "world";
    }
}

class MyClass
{
    use Trait2;
}

$myObj = new MyClass();
$myObj->hello();
$myObj->world();
```

### ❇Inheritance With Traits

```php
trait MyTrait
{
    public function hello()
    {
        print "hello ";
        parent::hello();
    }
}

class ParentClass
{
    public function hello()
    {
        print "world";
    }
}

class MyClass extends ParentClass
{
    use MyTrait;
}

$myObj = new MyClass();
$myObj->hello();
```

### ❇Overriding And Order of Precedence

?> Traits are overridden if the method with the same name is defined in the class that uses the traits. The precedence order is that members from the current class override Trait methods, which in turn override inherited methods.

```php
trait MyTrait
{
    public function hello()
    {
        print "hello ";
        parent::hello();
    }
}

class ParentClass
{
    public function hello()
    {
        print "world";
    }
}

class MyClass extends ParentClass
{
    use MyTrait;

    public function hello()
    {
        print "hi there";
    }
}

$myObj = new MyClass();
$myObj->hello();
```

### ❇Remapping

?> If you want to work around a trait's method being overridden, or you need to resolve a conflict of the same method name being used in two traits of a class, you can "remap" a trait's methods by changing their names and even whether the methods are private, public, protected.

```php
trait MyTrait
{
    public function hello()
    {
        print "hello ";
        parent::hello();
    }
}

class ParentClass
{
    public function hello()
    {
        print "world";
    }
}


class MyClass extends ParentClass
{
    use MyTrait {
        hello as private hey;
    }

    public function hello()
    {
        print "Using hey method: ";
        $this->hey();
    }
}

$myObj = new MyClass();
$myObj->hello();
```

### ❇Abstract Methods

?> Traits can specify abstract methods, forcing the class that uses the trait to implement methods

```php
trait MyTrait
{
    public function runSomething()
    {
        return $this->something();
    }

    public abstract function something();
}

class MyClass
{
    use MyTrait;

    public function something()
    {
        // do something here.
    }
}

$myObj = new MyClass();
$myObj->runSomething();
```

### ❇Change visibility of a trait method

```php
trait traitone {
    public function log() {
        echo "I am a method of traitone!";
    }
}

class Test {
    use traitone {
       log as protected aliased_log;
    }
}

$test = new Test();
$test->log();//I am a method of traitone!
$test->aliased_log();//PHP Warning:  Uncaught Error: Call to protected method
```

### ❇Conflict Resolution and Aliasing

```php
<?php
trait Game
{
    function play() {
        echo "Playing a game";
    }
}

trait Music
{
    function play() {
        echo "Playing music";
    }
}

<?php
class Player
{
    use Game, Music {
        Game::play as gamePlay;
        Music::play insteadof Game;
    }
}

$player = new Player();
$player->play(); //Playing music
$player->gamePlay(); //Playing a game
```

### ❇Reflection

?> The **Reflection API** is one of the powerful features of PHP to analyze the internal structure of interfaces, classes, and methods and reverse engineer them. And since we’re talking about traits, you might be interested to know about the Reflection API’s support for traits. In PHP 5.4, four methods have been added to ReflectionClass to get information about traits in a class.

> **ReflectionClass::getTraits()** to get an array of all traits used in a class.

> **ReflectionClass::getTraitNames()** method will simply return an array of trait names in that class.

> **ReflectionClass::isTrait()** is helpful to check if something is a trait or not.

> **ReflectionClass::getTraitAliases()** will return an array of trait aliases mapped to its original name.

## ⚡References

> [🌐 Reference 1](https://blog.programster.org/php-using-traits)

> [🌐 Reference 2](https://www.sitepoint.com/using-traits-in-php-5-4/)

> [🌐 Reference 3](https://dev.to/mattsparks/how-to-use-php-traits-459m)

!> Sample 1

!> Sample 2