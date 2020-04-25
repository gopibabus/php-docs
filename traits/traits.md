# Traits

## What are Traits?

**Limitation:** You cannot extend more than one class.

Multiple Inheritance is not possible in PHP. To address this issue PHP introduced concept called **Traits**, Where we can include multiple traits into a given class.

```php
<?php

trait DatabaseHelper {

    function getRecords(){
        echo "Here are your Database Credentials!!!";
    }
}

trait StringHelper {
    function removeSpaces($str) {
        return trim($str);
    }
}

class Student {
    use DatabaseHelper;
    use StringHelper;

    function connectDB() {
        $this->getRecords();
        echo $this->removeSpaces(" This is input ");
    }
}

$student1 = new Student();
$student1->connectDB();
```