# 🔥Control Structures

### ❇if, else, elseif

```php
<?php
if (condition) {
 // statements to execute
} elseif (second condition) {
 // statements to execute
} else {
 // statements to execute
}
```

### ❇switch

```php

<?php
switch ($statusCode) {
    case 200:
    case 300:
        $message = null;
        break;
    case 400:
        $message = 'not found';
        break;
    case 500:
        $message = 'server error';
        break;
    default:
        $message = 'unknown status code';
        break;
}
```

### ❇match

?> Introduced in PHP 8. We can only write one expression. match will do **strict type checks** instead of loose ones. It's like using **===** instead of **==**.

```php
$message = match ($statusCode) {
    200, 300 => null,
    400 => 'not found',
    500 => 'server error',
    default => 'unknown status code',
};
```

> [🌐 Reference](https://stitcher.io/blog/php-8-match-or-switch)
