# 🔥Variables & Constants

?> PHP language **construct and function names are not case-sensitive**, but variable and constant names are.

```php
<?php
ECHO "Hello World"; // Works
$variable = "Hello World";
echo $VARIABLE; // won't work
```

?> Using **echo** in html(embed)

```php
<?= $variable; ?>
<?php echo $variable; ?>
```

?> PHP is a **loosely typed language**. PHP change type of the variable during run time, there is no need to declare type explicitly when initialized. But this is changed with php7.4. **With php 7.4 Class properties now support type declarations**.

### ❇Naming Variables

- Names are case sensitive
- Names may contain letters, numbers, and the underscore character
- Names should not begin with a number

?> PHP has three categories of variables

- scalars
- composite
- resources

### ❇Scalar

| Type    | Contains                              |
| ------- | ------------------------------------- |
| Boolean | True or False                         |
| Integer | A signed numeric Integer              |
| Float   | A signed numeric double or float data |
| String  | An ordered collection of binary data  |

### ❇Composite

?>There are two composite types:

- arrays
- objects.

### ❇Casting Variables

?>It is possible to explicitly cast variables using one of two options:

> Use a casting operator

```php
<?php
$a = '123';
$a = (int)$a;
$a = (bool)$a;
```

> Use a PHP function

```php
<?php
$a = '123';
$a = intval($a);
$a = boolval($a);
$a = floatval($a);
$a = strval($a);
```

### ❇Constants

!> Only the const keyword can be used to create a namespaced constant

```php
<?php
define('PI', 3.142);
echo PI;
define('UNITS', ['MILES_CONVERSION' => 1.6, 'INCHES_CONVERSION' => '2.54']);
echo "5km in miles is " . 5 * UNITS['MILES_CONVERSION'];
/*
 3.1425km in miles is 8
*/
```

```php
<?php
const UNITS = ['MILES_CONVERSION' => 1.6,
 'INCHES_CONVERSION' => '2.54'];
echo "5km in miles is " . 5 * UNITS['MILES_CONVERSION'];
/*
 5km in miles is 8
*/
```

```php
<?php
namespace Foo;
const AVOCADO = 6.02214086;

namespace Bar;
// using define() will generate a warning
define(MOLE, 'hill');
```

### ❇Super Globals

?> Superglobals are available in every scope. You can alter the values of superglobals

| Super Global | Stores                                                                                                  |
| ------------ | ------------------------------------------------------------------------------------------------------- |
| \$GLOBALS    | An array of variables that exist in the global scope.                                                   |
| \$\_SERVER   | An array of information about paths, headers, and other information relevant to the server environment. |
| \$\_GET      | Variables sent in a GET request.                                                                        |
| \$\_POST     | Variables sent in a GET request.                                                                        |
| \$\_FILES    | An associative array of files that were uploaded as part of a POST request.                             |
| \$\_COOKIE   | An associative array of variables passed to the current script via HTTP cookies.                        |
| \$\_SESSION  | An associative array containing session variables available to the current script.                      |
| \$\_REQUEST  | POST, GET, and COOKIE request variables                                                                 |
| \$\_ENV      | An associative array of variables passed to the current script via the environment method.              |

### ❇Magic Constants

?> Magic constants are those which PHP provides automatically to every running script.

| Constants         | Contains                                                                         |
| ----------------- | -------------------------------------------------------------------------------- |
| \_\_LINE\_\_      | The current line number of the PHP script being executed                         |
| \_\_FILE\_\_      | The fully resolved (including symlinks) name and path of the file being executed |
| \_\_CLASS\_\_     | The name of the class being executed                                             |
| \_\_METHOD\_\_    | The name of the class method being executed                                      |
| \_\_FUNCTION\_\_  | The name of the function being executed                                          |
| \_\_TRAIT\_\_     | The namespace and name of the trait that the code is running in                  |
| \_\_NAMESPACE\_\_ | The current namespace                                                            |
