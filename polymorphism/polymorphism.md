# Polymorphism

## What is Polymorphism?

**POLY** means many and **MORPHIC** means form. Polymorphism means many forms os same method.

**Polymorphism** is achieved by using the same method names in different classes which are derived from same parent Interface.

```php
<?php
interface Database {
    public function openConnection();
}

class OracleDatabase implements Database {

    public function openConnection() {
        echo "Using Oracle driver to establish connection";
    }
}

class MySqlDatabase implements Database {

    public function openConnection() {
        echo "Using Mysql driver to establish connection";
    }
}
```