# 🔥User Defined Functions

?> In PHP, **function names are case insensitive** and can be referenced before they are defined.

?> You can specify what **type of variable** may be passed as an argument. To specify the type of argument that you are expecting, you add the type name in front of the argument definition.

!> If your function is called and the variable passed is the incorrect type, then PHP 7 will raise a **TypeError** exception.

```php
<?php
function add(int x, int y): int {
    return x + y;
}

add(50, 23);
```

> In the above example, **x and y are parameters**. **50 and 23 are argumants**.

### ❇Enforcing Type Hinting

?> There are two ways that you can enforce scalar type hinting:

- **coercive**

```php
<?php
function sayHello(string $name) {
 echo gettype($name);
}
sayHello(100); // string
```

- **strict**

```php
<?php
declare(strict_types=1);

function sayHello(string $name) {
 echo gettype($name);
}

sayHello(100);
/*
Fatal error: Uncaught TypeError: Argument 1 passed to sayHello() must be of
the type string, integer given,
*/
```

### ❇Alternate Null Type Syntax

?> PHP 7.1 introduced a new way to type hint variables that may be null.

?> The argument is not optional; you have to explicitly pass null or an Object of the specified type.

```php
<?php
function myFunc(?MyObject $myObj)
{
 echo "hello world";
}
// this is allowed
myFunc(null);
// this produces a fatal error: Too few arguments
myFunc();
```

### ❇Optional Arguments

?> You can specify a **default value for a parameter** that has the effect of making it optional.

```php
<?php
function sayHi($message = 'world') {
 echo "Hello $message";
}
sayHi();
```

### ❇Overloading Functions

?> **Function overloading** or **method overloading** is a feature that permits making creating several methods with a similar name that works differently from one another in the type of the input parameters it accepts as arguments.

?> PHP will not let you re declare the same function name twice.

?> In PHP overloading means the behavior of method changes dynamically according to the input parameter. Overloading Concept requires Magic methods. Overloading when performed creates properties and methods dynamically which is together called the entities.

```php
<?php
class Toys
{
public function __call($name,$param){
echo "Magic method invoked while method overloading with object reference<br/>";
}
public static function __callStatic($name,$param){
echo "Magic method invoked while method overloading with static access<br/>";
}
}
$objToys = new Toys;
$objToys->overloaded_method();
Toys::overloaded_property();
```

### ❇Property Overloading

?> PHP property overloading allows us to create dynamic properties in the object context. In this case as well, we use magic methods.

```php
<?php
class Toys
{

    private $str;

    public function __set($name, $value)
    {
        $this->str[$name] = $value;
    }

    public function __get($name)
    {
        echo "Overloaded Property name = " . $this->str[$name] . "<br/>";
    }

    public function __isset($name)
    {
        if (isset($this->str[$name])) {
            echo "Property \$$name is set.<br/>";
        } else {
            echo "Property \$$name is not set.<br/>";
        }
    }

    public function __unset($name)
    {
        unset($this->str[$name]);
        echo "\$$name is unset <br/>";
    }
}

$objToys = new Toys;
/* setters and getters on dynamic properties */
$objToys->overloaded_property = "new";
echo $objToys->overloaded_property . "\n\n";
/*Operations with dynamic properties values*/
isset($objToys->overloaded_property);
unset($objToys->overloaded_property);
isset($objToys->overloaded_property);
```

### ❇Variadics

?> We call **variadics** as spread operator in JavaScript.

> **PHP 5.6 introduced variadics** that explicitly accept a variable number of parameters. By using the **...** token in your argument list.

!> If you are mixing normal fixed parameters with a variadic syntax, then the **variadic parameter must be the last parameter** in the list of parameters.

?> variadic parameter is made available as an ordinary array \$params

```php
<?php
function fun($required, $optional = null, ...$variadicParams)
{
    printf(
        'Required: %d; Optional: %d; number of variadic parameters:%d' . PHP_EOL,
        $required,
        $optional,
        count($variadicParams)
    );
}

fun(1);
fun(1, 2);
fun(1, 2, 3);
fun(1, 2, 3, 4);
fun(1, 2, 3, 4, 5);

# This outputs:
# Required: 1; Optional: 0; number of variadic parameters:0
# Required: 1; Optional: 2; number of variadic parameters:0
# Required: 1; Optional: 2; number of variadic parameters:1
# Required: 1; Optional: 2; number of variadic parameters:2
# Required: 1; Optional: 2; number of variadic parameters:3
```

### ❇References

?> The **&** operator marks the parameter as being passed by reference. Changes to this parameter in the function will change the variable passed to it.

!> If a function argument is not defined as being a reference, then you cannot pass a reference in that argument.

```php
<?php
function addOne(&$arg) {
 $arg++;
}

$a = 0;
addOne($a);
echo $a; // 1
```

```php

<?php
function addOne($arg) {
 $arg++;
}
$a = 0;
addOne(&$a); // fatal error as of PHP 5.4.0
echo $a;
```

### ❇Variable Functions

```php
<?php
function foo() {
 echo 'Foo';
}

$var = 'foo';
$var(); // calls foo()
```

### ❇Return Type Declaration

?> We should place a colon and the type name after the parameters braces. If the function is going to return null, you can specify that it will return "void" (PHP 7.1+)

```php
<?php
function getFullName(string $firstName, string $lastName): string {
 return 123;
}

$name = getFullName('Mary', 'Moon');
echo gettype($name); // string
```

```php
<?php
function sayHello(): void {
 echo "Hello World";
}
// Hello World
sayWorld();
```

### ❇Return by Reference

?> It is possible to declare a function so that it returns a reference to a variable, rather than a copy of the variable.

```php
<?php
function &getValue() {...}
//When calling the function, you also place the & operator
//in front of the call:
$myValue = &getValue()
```

### ❇Variable Scope in Functions

?> PHP has three levels of scope

- global
- function
- class

?> Every time a function is called, a new function scope is created.

!> You can include global scope variables into your function. Most coding standards strongly discourage global variables because they introduce problems when writing tests, can introduce weird context problems, and make debugging more difficult.

```php
<?php
$glob = "Global variable";
function myFunction() {
 global $glob; // first method
 $glob = $GLOBALS['glob']; // second method
 $glob = "Changed";
}
myFunction();
echo $glob; // Changed
```

### ❇Lambda & Closure

?> A **lambda** in PHP is an anonymous function that can be stored as a variable. PHP lambdas and closures are implemented as objects instantiated from the Closure class. You can call **lambdas and closures** using the syntax you use for variable functions.

```php
<?php
$lambda = function($a, $b) {
 echo $a + $b;
};
echo gettype($lambda); // Object
echo (int)is_callable($lambda); // 1
echo get_class($lambda); // Closure
```

?> A **closure** in PHP is an anonymous function that encapsulates variables so they can be used once their original references are out of scope.

```php

<?php
$string = "Hello World!";
$closure = function() use ($string) {
 echo $string;
};
$closure();
```

### ❇Early and Late Binding

```php
<?php
$a = "some string";
// early binding (default)
$b = function() use ($a) {
 echo $a;
};
$a = "Hello World";
// some string
$b();
```

```php

<?php
$a = "some string";
// late binding (reference)
$b = function() use (&$a) {
 echo $a;
};
$a = "Hello World";
// Hello World
$b();
```

!> PHP will **use early binding by default**. If you want to use late binding, you should use a reference when importing.

### ❇Self Executing Closures

```php
(function () {
    echo 'Self-executing anonymous function' . PHP_EOL;
    $definedInClosure = 'Variable set'. PHP_EOL;
    echo $definedInClosure;
})();

var_dump(isset($definedInClosure));//False
```

### ❇Callbacks/Callables

?> **Callbacks** can be denoted by callable type. Some functions like **call_user_func() or usort()** accept user-defined callback functions as a parameter.

- A callable for a function can be one of the following:
  - An inline anonymous function.
  - A lambda or closure variable.
  - A string denoting a PHP function (**but not language constructs**).
  - A string denoting a user-defined function.
  - An array containing an instance of an object in the first element, and the string name of the function to call in the second element.
  - A string containing the name of a static method in a class.

```php
// An example callback function
function my_callback_function() {
    echo 'hello world!';
}

// An example callback method
class MyClass {
    static function myCallbackMethod() {
        echo 'Hello World!';
    }
}

// Type 1: Simple callback
call_user_func('my_callback_function');

// Type 2: Static class method call
call_user_func(array('MyClass', 'myCallbackMethod'));

// Type 3: Object method call
$obj = new MyClass();
call_user_func(array($obj, 'myCallbackMethod'));

// Type 4: Static class method call (As of PHP 5.2.3)
call_user_func('MyClass::myCallbackMethod');
```

```php
// Type 5: Relative static class method call (As of PHP 5.3.0)
class A {
    public static function who() {
        echo "A\n";
    }
}

class B extends A {
    public static function who() {
        echo "B\n";
    }
}

call_user_func(array('B', 'parent::who')); // A
```

```php
// Type 6: Objects implementing __invoke can be used as callables (since PHP 5.3)
class C {
    public function __invoke($name) {
        echo 'Hello ', $name, "\n";
    }
}

$c = new C();
call_user_func($c, 'PHP!');
```