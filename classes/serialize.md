# Serialization

```php

<?php
require __DIR__ . '/vendor/autoload.php';

/*
|--------------------------------------------------------------------------
| Serialization handled manually by developer
|--------------------------------------------------------------------------
|
| We decide what is needed to be serialized in a Class
|
*/
class Manager
{
  public $name;
  public function __construct($name)
  {
    $this->name = $name;
  }
}

class Department implements Serializable
{
  public $name;
  public Manager $manager;
  public function __construct($name)
  {
    $this->name = $name;
  }

  public function serialize()
  {
    return json_encode([
      'name' => $this->name,
      'manager' => $this->manager,
      'manager_class' =>  get_class($this->manager)
    ]);
  }

  public function unserialize($data)
  {
    $jsonDepartment = json_decode($data);
    $this->name = $jsonDepartment->name;
    $this->manager = new $jsonDepartment->manager_class($jsonDepartment->manager->name);
  }
}

$department1 = new Department('IT');
$department1->manager = new Manager('Bill Gates');
$departmentString = serialize($department1);

$department2 = unserialize($departmentString);
$department2->manager->name = "Gopibabu";

```