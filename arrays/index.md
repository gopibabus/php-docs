# 🔥Arrays

?> There are three types of array in PHP:

- indexed
- Associative
- Multidimensional

```php
<?php
// numeric index, auto assigned key
$arr = array(10, 'abc', 30);
// numeric index, key explicitly set
$arr = array(0 => 10, 1 => 'abc', 2 => 30 );
// associative
$arr = array('name' => 'foo', 'age' => 20);
// short syntax
$arr = ['name' => 'foo', 'age' => 20];

$student = [
    'name' => 'foo',
    'age' => 20,
    'address' => ['address1' => 'bodawada', 'city' => 'prakasam'],
];

echo $student['address']['city'];//prakasam
```

!> If you do not specify a key in the brackets, PHP assumes that you are trying to reference a new element. Note that PHP chose the key by incrementing the highest numeric key in the array.

?> PHP arrays are zero-based. PHP array keys are case sensitive: **\$arr['A']** and **\$arr['a']** are different elements.

?> Keys are unique; if multiple elements in an array use the same key, then PHP will use the last one for the value and overwrite all the preceding values.

```php
$arr = [0 => 'id', 'name' => 'foo', 'age' => 20];
$arr[] = 'example';
print_r($arr);

# Output
Array
(
    [0] => id
    [name] => foo
    [age] => 20
    [1] => example
)
```

### ❇Array Operators

?> Arrays are equivalent if they have the same key and value pairs.

?> Arrays are identical if they have the same key and value pairs, are in the same order, and the key-value are of the same type.

?> The **+** operator will produce the union of two arrays. When using the + union operator, PHP appends the array on the right of the operator to the left. If a key exists in both arrays, then the left array value is used for the key.

```php
<?php
$a = ['a' => 'hello', 'b' => 'world'];
$b = ['a' => 'goodbye', 'c' => 'cruel'];
echo implode(' ', $a + $b); // hello world cruel
```

```php
<?php
$a = ['a', 'b', '1'];
$b = ['a', 'b', 1];
$c = ['1', 'b', 'a'];
$d = [2 => 1, 0 => 'a', 1 => 'b'];
var_dump($a == $b); // true
var_dump($a === $b); // false
var_dump($a == $c); // false
var_dump($a == $d); // true
var_dump($a === $d); // false
```

### ❇Iterating through Arrays

```php
<?php
$arr = [
 'a' => 'apple',
 'b' => 'banana',
 'c' => 'cherry'
];
foreach($arr as $value) {
 echo $value . PHP_EOL;
}
foreach($arr as $key => $value) {
 echo $key . ' = ' . $value . PHP_EOL;
}
```

```php
<?php
$arr = [
 'a' => 'apple',
 'b' => 'banana',
 'c' => 'cherry'
];
while (list($key, $val) = each($arr)) {
 echo "$key is $val" . PHP_EOL;
}

//Output
a is apple
b is banana
c is cherry
```

### ❇Standard PHP Library(SPL): ArrayObject Class

?> **ArrayObject** class that allows you to create objects from arrays.

```php
$fruits = array(
    "d" => "lemon",
    "a" => "orange",
    "b" => "banana",
    "c" => "apple",
);
$fruitArrayObject = new ArrayObject($fruits);
$fruitArrayObject->ksort();
foreach ($fruitArrayObject as $key => $val) {
    echo "$key = $val\n";
}
```
