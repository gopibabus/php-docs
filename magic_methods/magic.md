# Magic Methods

## What are magic methods?

**Magic Methods** are default methods available for any class and invoked automatically depending on the triggers.

<img src="./assets/images/magic_methods.png" alt="magic methods">

```php
<?php

class Database
{
    private $dbName;

    private $username;

    private $password;

    public function getInfo()
    {
        return [
            $this->dbName,
            $this->username,
            $this->password
        ];
    }

    public function __set($propertyName, $propertyValue)
    {
        echo "attempted to write to non-existing property: $propertyName";
    }

    public function __get($propertyName)
    {
        echo "attempted to read non-existing property: $propertyName";
    }

    public function __call($method, $args)
    {
        if (in_array($method, $this->APIs)) {
            array_unshift($args, $this->str);
            return call_user_func_array($method, $args);
        } else {
            die('Error: call to unsupported method: ' . $method);
        }
    }

    public function __toString()
    {
    }

    public function __debugInfo()
    {
    }
}

$db = new Database();
echo $db; #__toString() method is called
var_dump($db); #__debugInfo() method is called
$db->lastName = 'John'; #__set() method is called
$db->lastName; #__get() method is called
$db->getName();#__call() method is called
```
