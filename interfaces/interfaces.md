# Interfaces & Abstract Classes

## What is an Interface?

**interface** is like a guideline (or) contract that every class must implement all methods defined in an Interface.

You cannot define methods in an interface.

All methods in an interface are just definitions.

**interface** keyword is used to define interface.

**implements** keyword is used to implement from Interface.

Any class can implement one or more interfaces.

```php
<?php

interface Car {
    public function applyBreak();

    public function increaseSpeed();

    public function decreaseSpeed();
}

class SportsCar implements Car {
    /**
     * Must implement all functions defined in Car interface
     */
}
```

## How to use Interfaces in real world?

Instead of using class in our logic, we can use Interface of that class.

In this way we can hide implementation logic from end user.

```php
<?php

interface Car {
    public function applyBreak();

    public function increaseSpeed();

    public function decreaseSpeed();
}

class SportsCar implements Car {
    public function applyBreak() {
        return "Applied Break";
    }

    public function increaseSpeed() {
        return "Increased Speed";
    }

    public function decreaseSpeed() {
        return "decreased Speed";
    }
}

class EconomyCar implements Car {
    public function applyBreak() {
        return "Applied Break";
    }

    public function increaseSpeed() {
        return "Increased Speed";
    }

    public function decreaseSpeed() {
        return "decreased Speed";
    }
}

class ConstructCar {
    public function buildSportsCar(Car $sportsCar) {
        return $sportsCar->applyBreak();
    }

    public function buildEconomyCar(Car $economyCar) {
        return $economyCar->applyBreak();
    }
}
```

## What are Abstract classes and Methods?

Class that we do not want to create object are defined as **Abstract Class**.

A class is called **Abstract**, when it has atleast one Abstract methods inside it.

Methods that are declared as **Abstract** must be implemented in the child Class.

**Abstract Classes** are like **Interface** but Abstract Classes can have normal methods implementation.

```php
<?php

abstract class Car {
    abstract public function applyBreak();

    public function increaseSpeed() {
        echo "Increase Speed";
    }

    public function decreaseSpeed() {
        echo "Decrease Speed";
    }
}

class SportsCar extends Car {
    /**
     * Must implement all abstract methods from Car Class
     */
}
```

## What are use cases of Abstract classes and methods?

If we don't want to create instance of a class but use it's methods in child classes.

If we want to enforce child to implement some methods before using class methods.

**Abstract Class** is a library class that you want to extend and use it's library methods.

```php
<?php

abstract class Database {

    public $connection;
    private $connectionActive = false;

    abstract public function setConnection($dbName);
    abstract public function getConnection();

    public function checkConnectionActive() {
        return $this->connectionActive;
    }
}

class DBConnection extends Database {

    public function setConnection($dbName) {
        $this->connectionActive = true;
        $this->connection = "Connection Handler";
    }
    public function getConnection() {
        if($this->checkConnectionActive()){
            return $this->connection;
        }
    }
}
```
