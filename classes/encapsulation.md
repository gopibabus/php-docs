# Encapsulation

## What is Data Encapsulation?

**Data Encapsulation**: In the class you hide properties and make them access only through methods. 
Here we allow user to interact with **setter and getter** methods to access and update variables in the class.

```php
<?php

class Users
{

    private $age;

    private $name;

    /**
     * Get the value of age
     */
    public function getAge()
    {
        return $this->age;
    }

    /**
     * Set the value of age
     *
     * @return  self
     */
    public function setAge($age)
    {
        if (is_numeric($age)) {
            $this->age = $age;
        }
        return $this;
    }

    /**
     * Get the value of name
     */
    public function getName()
    {
        return $this->name;
    }

    /**
     * Set the value of name
     *
     * @return  self
     */
    public function setName($name)
    {
        if (is_string($name)) {
            $this->name = $name;
        }
        return $this;
    }
}
```

## What is Overriding?

**Overriding** is a concept where child class can override(rewrite) the parent's methods with same name.

```php
<?php

class Database
{
    public function getConnection() {
        echo "By default connected to MySql";
    }
}

class OracleDatabase extends Database
{
    public function getConnection() {
        echo "Connected to Oracle Database";
    }
}
```

## What is Overloading?

Defining same method 2 times in same class with different parameters.

🚫 Unforunately this feature is not implemented in PHP 😏

```php
<?php

class Database
{
    public function getConnection() {
        echo "By default connected to MySql";
    }

    public function getConnection($database) {
        echo "Connected to Oracle Database". $database;
    }
}
```
