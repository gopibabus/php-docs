# 🔥PHP Operators

### ❇Arithmetic

| Operation      | Example    | Description                              |
| -------------- | ---------- | ---------------------------------------- |
| Addition       | 1 + 2.3    | sum of 2 numbers                         |
| Subtraction    | 4 – 5      | difference of 2 numbers                  |
| Division       | 6 / 7      |                                          |
| Multiplication | 8 \* 9     | product of 2 numbers                     |
| Modulus        | 10 % 11    | Gives the remainder of dividing 10 by 11 |
| Power          | 12 \*\* 13 | Raises 12 to the power of 13             |

### ❇Unary

| Command     | Output | Value of \$a after | Description |
| ----------- | ------ | ------------------ | ----------- |
| \$a = 1     |        | 1                  | Assignment  |
| echo \$a++; | 1      | 2                  | Postfix     |
| echo ++\$a; | 3      | 3                  | Prefix      |
| echo \$a--; | 3      | 2                  | Postfix     |
| echo --\$a; | 1      | 1                  | Prefix      |

### ❇Logic

| Operator | Example      | True When                              |
| -------- | ------------ | -------------------------------------- |
| and      | $a and $b    | Both $a and $b evaluate true           |
| and      | $a && $b     |                                        |
| or       | $a or $b     | Either $a or $b evaluate true          |
| or       | \$a \|\| \$b |                                        |
| xor      | $a xor $b    | One of (but not both) $a or $b is True |
| xor      | $a ^ $b      |                                        |
| not      | !\$a         | \$a is not true (false)                |

!> logical operators **and** , **or** have lower priority over equality operator **=**

### ❇Bitwise Operators

| Operator | Operation   | Description                                                                                           |
| -------- | ----------- | ----------------------------------------------------------------------------------------------------- |
| &        | Bitwise AND | The result will have a bit set if both of the operands bits were set                                  |
| \|       | Bitwise OR  | If one or both of the operands have a bit set then the result will have that bit set                  |
| ^        | Bitwise XOR | If one and only one of the operands (not both) has the bit set then the result will have the bit set. |

| Operation | Name        | Result in Binary | Result in Decimal |
| --------- | ----------- | ---------------- | ----------------- |
| 50        |             | 00110010         |                   |
| 50 >> 1   | Shift Right | 00011001         | 25                |
| 50 << 1   | Shift Left  | 01100100         | 100               |

### ❇Reference Operator

?> By default, **PHP assigns all scalar variables by value**. PHP always assigns **Objects by reference**. if you try to explicitly create it by reference, PHP will generate a parse error.

```php
<?php
$a = 1;
$b = &$a; // assign by reference
$b += 5;
echo $a; // 6

class MyClass {}
// Parse error: syntax error, unexpected 'new'
$a = &new MyClass;
```

### ❇Comparison Operators

| Operator | Description                                     |
| -------- | ----------------------------------------------- |
| >        | Greater than                                    |
| >=       | Greater than or equal to                        |
| <        | Less than                                       |
| <=       | Less than or equal to                           |
| <>       | Not equal                                       |
| ==       | Equivalent(Values should be equal)              |
| ===      | Identical(Values and DataTypes should be equal) |
| !=       | Not equivalent                                  |
| !==      | Not identical                                   |

### ❇@ Operator

!> **@** operator will suppress error messages. It’s bad practice to suppress PHP errors with the **@** operator.

### ❇Back Tick Operator

?> This operator is equivalent to calling the **shell_exec()** command.

```php
<?php
// This is the equivalent of echo shell_exec('whoami');
echo `whoami`;
```

```php
<?php
// Error messages will be suppressed
$dbConnection = @mysqli_connect(...);
```

### ❇Ternary Operator

```php
<?php
$a = 'foo';
$b = (isset($a)) ? 'true' : 'false';
echo $b; // true
```

### ❇Elvis Operator

```php
<?php
$a = "gopi";
$b = $a ?: 'foo';
echo $b; // gopi
```

### ❇Null Coalescing Operator

```php
<?php
// Long form ternary syntax
$sortDirection = (isset($_GET['sort_dir'])) ? $_GET['sort_dir'] : 'ASC';

// Equivalent syntax using the null coalescing operator
$sortDirection = $_GET['sort_dir'] ?? 'ASC';

// The null-coalesce operator can be chained
$sortDirection = $_GET['sort_dir'] ?? $defaultSortDir ?? 'ASC';

// The Elvis operator raises E_NOTICE if the GET variable is not set
$sortDirection = $_GET['sort_dir'] ?: 'ASC';
```

### ❇Coalescing Assign Operator

```php
<?php

//PHP < 7
$data['key'] = isset($data['key']) ? $data['key'] : 'some_default';

//PHP 7.X < 7.4
$data['key'] = $data['key'] ?? 'some_default';

//PHP >= 7.4
$data['key'] ??= 'some_default';
```

### ❇Spaceship (<=>)

| Operation              | Value |
| ---------------------- | ----- |
| 1 <=> 0                | 1     |
| 1 <=> 1                | 0     |
| 1 <=> 2                | -1    |
| 'apples' <=> 'Bananas' | 1     |
| 'Apples' <=> 'bananas' | -1    |

### ❇Spread Operator

```php
$arr1 = [3,4,5];
$arr2 = [8,9,10];

//Before PHP 7.4
$superArray = array_merge([1,2], $arr1, [6,7], $arr2);

//From PHP 7.4
$superArray = [1, 2, ...$arr1, 6, 7, ...$arr2];
```
