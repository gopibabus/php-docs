# 🔥Strings

?> PHP strings are a series of bytes. In PHP, strings may be declared either as **simple type** or **complex type**.

```php
<?php
$name = 'Bob';
$a = 'Hello $name\n';
$b = "Hello $name\n";
echo $a; // Hello $name\n
echo $b; // Hello Bob
```

```php
<?php
$catfood = "Cheeseburgers";
echo 'I can haz $catfood'; // I can haz $catfood
echo 'I can haz ' . $catfood; // I can haz Cheeseburgers
echo "I can haz $catfood?"; // I can haz Cheeseburgers?
```

```php
<?php
$dogfood = ['Pellets'];
$catfood = new stdClass();
$catfood->favorite = "Cheeseburger";
echo "$dogfood[0]"; // Pellets
echo "$catfood->favorite"; // Cheeseburger
```

?> PHP allows the use of **curly braces** for you to explicitly tell the parser that part of a string must be evaluated.

```php
$burger = "Cheeseburger";
echo "I can haz {$burger}"; // I can haz Cheeseburger
echo "I can haz ${burger}"; // I can haz Cheeseburger
echo "I can haz $burgers"; // no variable $burgers
echo "I can haz {$burger}s"; // I can haz Cheeseburgers
echo "I can haz { $burger }"; // I can haz { Cheeseburger }
```

```php
$catfood = new stdClass();
$catfood->name = "Cheeseburgers";
$cat = new stdClass();
$cat->canhaz = [$catfood];
echo "$cat->canhaz[0]->name"; // array to string conversion
echo "{$cat->canhaz[0]->name}"; // Cheeseburgers
```

### ❇Heredoc and Nowdoc

?> A **heredoc** is a convenient way to declare a string that spans multiple lines. Heredoc strings are evaluated for control characters and variables, just like double quoted strings are.

> Common uses for heredoc include creating **SQL queries** & **snippets of HTML**.

```php
<?php
$name = "gopi";

echo  <<<HEREDOC
 This is a heredoc string, note:
 1) the capitalization of the tag
 2) the tag name follows variable naming rules
 3) Name : {$name}
HEREDOC;
```

?> **nowdocs** are not evaluated for special characters and variables.

```php
<?php
echo <<<'NOWDOC'
This is a nowdoc string, note:
 1) Single quotes around the label
 2) Variables will not be evaluated
 3) Control characters will not be evaluated
NOWDOC;
```

### ❇Referencing Characters in Strings

?> You can reference a position in a string by using either **square brackets or curly braces**.

```php
<?php
$hello = "world";
echo $hello[0]; // w
echo $hello{1}; // o
```

?> Writing to a position that is out of range will result in the string being padded with spaces to accommodate the missing section.

```php
<?php
$hello = "world";
$hello[10] = "*";
echo $hello; // world     *
```

?> **Comparing strings in PHP** should be done with an appropriate level of care when you’re trying to match different variable types. Using comparison operators like **> and <** might not always work as expected. Instead of using alphabetical sorting, PHP uses the ASCII value of the character to make the comparison.

```php
<?php
$a = "PHP";
$b = "developer";
if ($a > $b) {
 echo "$a > $b";
} else {
 echo "$a < $b";
}
// developer comes before PHP in the alphabet
// but this script outputs
// PHP < developer
```
