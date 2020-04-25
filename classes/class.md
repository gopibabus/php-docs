# Classes in OOPs

## What is a Class ?

**Class** is a blueprint of a object.

Class is a logical grouping of code with properties and methods specific to a object.

The main purpose of class is to organize our code into individual components.

## How to organize Classes?

1. First identify classes in our program

2. Start defining the class.

3. Classes are specifications and not real.

4. Class name first letter should start with Capital Letter.

5. File name should match class name.

6. One file should contain only one class.

7. Class in opened and closed with **{ }** like functions.

## Template of a Class:

```php
Class Car {

    private $car_name;

    function helloClass(){

        echo "Hello from Car Class" . PHP_EOL;
    }
}
```

## How to use Other Class inside a Class?

```php
<?php

class Users
{
    function fetchUser($id): array
    {
        $result = false;

        /**
         * Place where we call Database Class
         */
        echo "Query Database". PHP_EOL;
        $result=true;
        echo "Display the records". PHP_EOL;
        $result = [];

        return $result;
    }

    function deleteUser($id): void{
        /**
         * Place where we call Database Class
         */
        echo "Delete records for USER ID: $id". PHP_EOL;
    }

}

$user1 = new Users();
$user1->fetchUser(101);
$user1->fetchUser(102);
$user1->deleteUser(101);
```

### Example: Employee Class

```php
<?php

class Users
{
    public $id;
    public $name;
    public $workingHrsPerDay;
    public $hourlyRate;
    public $totalLeaves;
    public $workingDays;

    function getSalary($totalDays): int
    {
        $this->workingDays = $totalDays - $this->totalLeaves;

        $salary = $this->workingDays * ($this->workingHrsPerDay * $this->hourlyRate);

        return "Salary of $this->name is $salary";
    }

}

$user1 = new Users();
$user1->id = 123456;
$user1->name = "John Marty";
$user1->workingHrsPerDay = 8;
$user1->hourlyRate = 50;
$user1->totalLeaves = 1;

echo $user1->getSalary(23);
```