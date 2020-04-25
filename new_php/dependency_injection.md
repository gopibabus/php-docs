# Dependency Injection

## What is Dependency Injection?

**Dependency Injection(DI)** is a design pattern that allows the creation of dependent objects outside of a class and provides those objects to a class through different ways.

Using **DI**, we move the creation and binding of the dependent objects outside of the class that depends on them.

<img src="./assets/images/di.png" alt="DI">

```php
<?php

class Course {
    public $cid;

    function __construct($cid)
    {
        $this->cid = $cid;
    }
}

class Lesson {
    public $lid;
    public $cid;

    function __construct($lid, Course $course)
    {
        $this->lid = $lid;
        $this->cid = $course->cid;
    }

    function showLessons() {
        echo "Here are lessons";
    }
}

class Quiz extends Course {
    public $qid;

    function __construct($qid, Course $course)
    {
        $this->qid = $qid;
        $this->cid = $course->cid;
    }
}

$course = new Course(1);
$lesson = new Lesson(100, $course);
$quiz = new Quiz(200, $course);
```

## What are benefits of using DI?

* Helps in Unit testing.
* Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
* Extending the application becomes easier.
* Helps to enable loose coupling, which is important in application programming.

**Library used in PHP to implement DI**

<a href="http://php-di.org/" target="_blank"><img src="./assets/images/php-di.png" alt="DI"></a>

## Real world example of DI:

```php
<?php

interface GeolocationService {
    public function getCoordinatesFromAddress($address);
}

class GoogleMaps implements GeolocationService { }

class OpenStreetMap implements GeolocationService { }

class StoreService {
    private $geolocationService;

    public function __construct(GeolocationService $geolocationService) {
        $this->geolocationService = $geolocationService;
    }

    public function getStoreCoordinates($store) {
        return $this->geolocationService->getCoordinatesFromAddress(
            $store->getAddress()
        );
    }
}
```