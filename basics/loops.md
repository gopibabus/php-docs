# 🔥Loops

### ❇While, do While

```php
<?php
while (expression) {
 // statements to execute
}
```

```php
do {
 // statements to execute
} while (expression)
```

### ❇for

```php
<?php
for ($i = 0; $i < 10; $i++) {
 // do something
}
```

### ❇foreach

```php
<?php
$arr = [
 'a' => 'one',
 'b' => 'two',
 'c' => 'three'
];

foreach ($arr as $value) {
 echo $value; // one, two, three
}

foreach ($arr as $key => $value) {
 echo $key; // a, b, c
 echo $value; // one, two, three
}
```

### ❇continue

?> Using **continue** has the effect of stopping/skipping the **current iteration** and allowing the loop to process the next evaluation condition. This allows you to let any further iterations to occur.

```php
<?php
foreach ($arr as $key => $value) {
    if (!($key % 2)) { // skip even members
        continue;
    }
    do_something_odd($value);
}
```

### ❇break

?>Using **break** has the effect of **stopping the entire loop** and no further iterations will occur.

> The **break** statement takes an **optional integer value** that can be used to break out of multiple levels of a nested loop. If no value is specified, it defaults to 1.

```php

<?php

$arr = array('one', 'two', 'three', 'four', 'stop', 'five');
foreach ($arr as $val) {
    if ($val == 'stop') {
        break;    /* You could also write 'break 1;' here. */
    }
    echo "$val";
}
```

```php
<?php
/* Using the optional argument. */
$i = 0;
while (++$i) {
    switch ($i) {
        case 5:
            echo "At 5";
            break 1;  /* Exit only the switch. */
        case 10:
            echo "At 10";
            break 2;  /* Exit the switch and the while. */
        default:
            break;
    }
}
```