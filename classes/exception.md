# Exceptions

### Multi-catch exception handling

?> Added in v7.1

```php

try {
 // ...
} catch(ErrorA | ErrorB $e) {
 //
} catch(Exception $e) {
 // general case
}

```