# Inheritance

## What are access modifiers?

Access Modifiers helps to restrict the access of properties and methods.

Access Modifiers are not applied to classes and Interfaces.

Access Modifiers are of 3 types - **public, private & protected**.

They help us in hiding properties and methods accessed from the Object.

By default properties and methods are **public**.

**public** access modifier means it can be accessed from inside and ouside of a class.

**private** access modifier means it can be accessed only inside class and cannot accessed from outside of the class.

**protected** access modifier helps us to restrict access of properties and methods to child and Parent classes.

protected properties and methods are cannot be accessed from outside using objects.

```php
<?php

Class Car {

    private $name;
    private $color;

    private function getName(): string {
        return $this->name;
    }

    public function setName($name): void {
        $this->name = $name;
    }

    private function getColor(): string {
        return $this->color;
    }

    public function setColor($color): void {
        $this->color = $color;
    }

    public function getCarInfo() {
        return [
            $this->getName(),
            $this->getColor()
        ];
    }
}

$car1 = new Car();
$car1->name = "Honda";#cannot access private property 
$car1->color = "Black";#cannot access private property 
$car1->setColor('Black');
$car1->setName('Honda');
$car1->getName();#cannot access private method 
$car1->getCarInfo();
```

## What is Inheritance?

If you want to reuse an existing Class properties & methods in our Class then we should **extend** that class from your class.

Parent Class properties and methods are available in Child class after extending parent class.

We can restrict access of properties and methods to child classes via **protected** access modifier.

**Multiple inheritance** is not possible in PHP. We can only extend only one class.

```php
<?php

Class University {
    protected  $univeristy_name = "DSU";

    protected function getUniversityName() {
        return $this->univeristy_name;
    }
}

Class Teacher extends University {

    private $teacher_name = 'Kiranmai';

    public function getTeacherName() {
        return $this->teacher_name;
    }

    public function getUniversityName() {
        return parent::getUniversityName();
    }
}

$teacher1 = new Teacher();
$teacher1->getUniversityName();
$teacher1->getTeacherName();
```

## What is Overriding of Methods?

Declaring same method from Parent class with same signature in child class.

```php
<?php

Class University {
    private  $univeristy_name = "DSU";

    public function getName() {
        return $this->univeristy_name;
    }
}

Class Teacher extends University {

    private $teacher_name = 'Kiranmai';

    public function getName() {
        return $this->teacher_name;
    }
}

$teacher1 = new Teacher();
$teacher1->getName();#Kiranmai
```

## How to implement Multiple Inheritance?

We can't extend multiple classes in PHP. But we can achieve multiple inheritance by extending class which is extending required class.

```php
<?php

Class University {
    private  $univeristy_name = "DSU";

    public function getName() {
        return $this->univeristy_name;
    }
}

Class Teacher extends University {

    private $teacher_name = 'Kiranmai';

    private $working_hrs = 40;

    public function getName() {
        return $this->teacher_name;
    }

    public function getSalary() {
        return $this->working_hrs * 20;
    }
}

Class PartTimeTeacher extends Teacher {
    private $working_hrs = 20;

    public function getSalary() {
        return $this->working_hrs * 20;
    }

}

$teacher1 = new Teacher();
$teacher1->getName();#Kiranmai
$teacher2 = new PartTimeTeacher();
$teacher2->getSalary();#400
```

## What is purpose of final keyword?

**final** keyword is used to restrict methods and class not to be shared with Child Class.

**Class as final** - Prevent Inheritance

**Method as final** - Prevent Method Overriding

```php
<?php

Class University {
    private  $univeristy_name = "DSU";

    final function getName() {
        return $this->univeristy_name;
    }
}

final Class Teacher extends University {

    private $working_hrs = 40;

    public function getSalary() {
        return $this->working_hrs * 20;
    }
}

Class PartTimeTeacher extends Teacher {

    private $working_hrs = 20;

    public function getSalary() {
        return $this->working_hrs * 20;
    }

}

$teacher1 = new Teacher();
$teacher1->getName();# Cannot inherit final method
$teacher2 = new PartTimeTeacher(); # Cannot extend final Class
```