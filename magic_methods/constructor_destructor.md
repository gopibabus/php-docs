# Constrctor & Destructor

## What is Constructor?

Constructors are magic methods that gets loaded automatically, when instance of a class in created.

Purpose of a constructor is to initialize the properties of a Class.

**__construct( )** is called automatically when new instance is created and doesnot return any value. Argumants are optional.

You can choose to define constructor method or ignore it as it is optional to define.

```php
<?php

Class Car {

    public $wheels;

    public __constructor() {
        $this->wheels = 4;
    }

    public function wheelCount() {
        return $this->wheels;
    }
}

$car1 = new Car();
$car1->wheelCount();
```

## What are Realtime use cases of a Constructor?

1. Initialize the properties of a class.

2. Initialize the Database Connection.

3. Check if file exists.

4. Open a file before using it with the methods.

5. Check API is reachable before the connection.

6. Load a instance of a class.

## How to initialize properties with a constructor?

```php
<?php

Class Car {

    public $wheels;
    public $name;
    $public $color;

    public __constructor($name, $color) {
        $this->wheels = 4;
        $this->name = $name;
        $this->color = $color;
    }

    public function wheelCount() {
        return $this->wheels;
    }

    public function getName() {
        return $this->name;
    }

    public function getColor() {
        return $this->color;
    }
}

$car1 = new Car('honda', 'pearl');
$car1->getName();
$car1->getColor();
```

### Constructor property promotion

?> Added in v8.0

```php

// from this
class User {
  public string $name;
  public Address $address;
  public function __construct(string $name, Address $address) {
    $this->name = $name;
    $this->address = $address;
 }
}
// to this
class User {
  public function __construct(protected string $name, protected Address $address) {
  // nothing else needed
  }
}

```

## What is a Destructor?

Destructors are magic methods that gets loaded automatically just before instance of class is destroyed. And doesnot return any values.

Purpose of destructor is to do clean up activities.

**Example**: Closing database connection (or) saving a file.

You can choose to define destructor method or ignore it as it is optional to define.

```php
<?php

Class Car {
    public $dbConnection;

    public __destruct() {
        mysqli_close($dbConnection);
    }
}
```

## What are Realtime use cases of a Destructor?

1. Perform cleanup activities.

2. Close Database Connection.

3. Close file Connections.

4. Save log file.

5. Write Activity logs - End time.

6. Free up Resources.

7. Save properties into a file.

8. Save the Cache

9. Serialize the Objects.