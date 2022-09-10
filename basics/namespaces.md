# 🔥Namespaces

?> **Namespaces** help you avoid naming collisions between libraries or other shared code.

?> The namespace declaration must occur straight after the opening php tag.

!> **Namespaces affect constants**, but you must declare them with the **const keyword** and not with define().

```php
<?php
namespace A {
 // Code is in namespace A
}
```

### ❇Fully Qualified Namespace Names

```php
<?php
namespace MyApp\Helpers;
class Formatters
{
 public static function asCurrency($val) {
 // statement
 }
}
```

```php
<?php
// this file is in a different namespace
namespace MyApp\Lib;
// we must specify the full path to the namespace that the class is in
echo MyApp\Helpers\Formatters::asCurrency(10);
```

### ❇use

?> **use** statement is used to import a namespace so that you don’t have to use the long format all the time.

```php

<?php
// this file is in a different namespace
namespace MyApp\Lib;
// the "use" keyword imports the namespace
use MyApp\Helpers\Formatters;
// we no longer have to provide a full reference
echo Formatters::asCurrency(10);
```

### ❇Global namespace

?> You should precede a name with a backslash **(/\)** to indicate that you intend to use the global namespace.

!> If we had not indicated the global scope with the backslash, the interpreter would look for a class called Exception within the MyApp namespace.

```php
<?php
namespace MyApp;
throw new \Exception('Global namespace');
```

### ❇Import grouping

?> Added in v7.0

```php

// all in separate lines
use App\Entity\Task;
use App\Entity\Reminder;
use App\Entity\Todo;
// now
use App\Entity\{Task, Reminder, Todo};

```