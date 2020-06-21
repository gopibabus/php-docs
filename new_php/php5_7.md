# 🔥PHP 5 vs PHP 7

> [🌐 Reference](https://www.stitcher.io/)

<img src="./assets/images/php5v7.png" alt="php" width="700"/>

Following are major differences, when we compare PHP 7 with PHP 5

### ✳New Zend Engine
* The Zend engine has been powering PHP since 1999 when it was introduced with the then new PHP 4.
* PHP 5.X series use Zend Engine II that enhanced the funtionality of the initial engine and adds an extensible object model and a significant performance enhancement to the language.
* PHP 7 receives a brand new version of the engine coming under the code name of PHP-NG (Next Generation).

### ✳Twice The Speed
* The most easily recognizable advantage of the **new PHPNG engine** is the significant performance improvement and remarkably optimized memory usage.

### ✳Facilitates Error Handling
* Handling fatal and catchable fatal errors have never been an easy task for PHP coders till PHP 5.
* The new Engine Exceptions will allow you to **replace these kind of errors with exceptions**. If the exception is not caught, PHP will continue to return the same fatal errors as it does in the current 5.X series.

### ✳64-Bit Windows Systems Support
* The 5.X series don’t yet provide 64-bit integer or large file support.
* PHP 7 will change this as it introduces consistent 64-bit support which means both native 64-bit integers and large files will be supported, allowing you to confidently run the language on your 64-bit Windows system in the future.

### ✳New Spaceship
* The notation of the new operator looks like this: **<=>**.
* The spacehip operator returns 0 if both operands are equal, 1 if the left is greater, and -1 if the right is greater.
* Inspired from programming languages like Perl and Ruby.

```php
 // Comparing Integers

echo 1 <=> 1; // outputs 0
echo 3 <=> 4; // outputs -1
echo 4 <=> 3; // outputs 1

// String Comparison

echo "a" <=> "a"; // outputs 0
echo "m" <=> "y"; // outputs -1
echo "y" <=> "c"; // outputs 1
```

### ✳Null Coalescing operator
* The Null Coalescing operator is denoted with two question marks ( **??** ).
* The null coalesce operator returns the result of its first operand if it exists and is not null, and the second operand in any other cases.

```php
$username = $_GET['user'] ?? 'nobody';
// This is equivalent to:
$username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
```

### ✳Null coalescing assignment operator
* Introduced in PHP7.4

```php
$data['date'] = $data['date'] ?? new DateTime();
// alternative to above piece of code
$data['date'] ??= new DateTime();
```
### ✳Type Declarations
*  PHP 7 enables developers to enhance the quality of their code with the help of return type declarations.

```php
//Return array
function foo(): array {
    return [];
}
```

### ✳Scalar type declarations
* PHP 7 introduces 4 new type declarations for scalar types: int, float, string and bool.

```php
function sumOfInts(int ...$ints)
{
    return array_sum($ints);
}
```

### ✳Anonymous Classes
* An anonymous class is a class without a name.

```php
<?php
interface Logger {
    public function log(string $msg);
}

class Application {
    private $logger;

    public function getLogger(): Logger {
         return $this->logger;
    }

    public function setLogger(Logger $logger) {
         $this->logger = $logger;
    }
}

$app = new Application;
$app->setLogger(new class implements Logger {
    public function log(string $msg) {
        echo $msg;
    }
});

var_dump($app->getLogger());
```

### ✳Imports From the Same Namespace

```php
<?php
// Pre PHP 7 code
use some\namespace\ClassA;
use some\namespace\ClassB;
use some\namespace\ClassC as C;

use function some\namespace\fn_a;
use function some\namespace\fn_b;
use function some\namespace\fn_c;

use const some\namespace\ConstA;
use const some\namespace\ConstB;
use const some\namespace\ConstC;

// PHP 7+ code
use some\namespace\{ClassA, ClassB, ClassC as C};
use function some\namespace\{fn_a, fn_b, fn_c};
use const some\namespace\{ConstA, ConstB, ConstC};
?>
```

### ✳JSON errors can be thrown
* Introduced in PHP 7.3

```php
json_encode($data, JSON_THROW_ON_ERROR);

json_decode("invalid json", null, 512, JSON_THROW_ON_ERROR);

// Throws JsonException
```

### ✳Arrow Functions
* Introduced in PHP 7.4
* They can always access the parent scope, there's no need for the **use** keyword.

```php
//prior 7.4
array_map(function (User $user) {
    return $user->id;
}, $users)

//with php7.4
array_map(fn (User $user) => $user->id, $users)
```

### ✳Typed properties
* Introduced in PHP 7.4
* Class variables can be type hinted.

```php
class A
{
    public string $name;

    public ?Foo $foo;
}
```

### ✳Array spread operator
* Introduced in PHP 7.4

```php
$arrayA = [1, 2, 3];

$arrayB = [4, 5];

$result = [0, ...$arrayA, ...$arrayB, 6 ,7];

// [0, 1, 2, 3, 4, 5, 6, 7]
```

### ✳Numeric Literal Separator
```php
$unformattedNumber = 107925284.88;

$formattedNumber = 107_925_284.88;
```

### ✳Preloading
* If you're using a framework, its files have to be loaded and linked on every request. Preloading allows the server to load PHP files in memory on startup, and have them permanently available to all subsequent requests.
* If the source of preloaded files are changed, the server has to be restarted.

### ✳libsodium
* Introduced in PHP 7.2
* The Sodium crypto library (libsodium) is a modern, easy-to-use software library for encryption, decryption, signatures, password hashing and more.

```php
$msg = 'This is a super secret message!';

// Generating an encryption key and a nonce
$key   = random_bytes(SODIUM_CRYPTO_SECRETBOX_KEYBYTES); // 256 bit
$nonce = random_bytes(SODIUM_CRYPTO_SECRETBOX_NONCEBYTES); // 24 bytes

// Encrypt
$ciphertext = sodium_crypto_secretbox($msg, $nonce, $key);
// Decrypt
$plaintext = sodium_crypto_secretbox_open($ciphertext, $nonce, $key);

echo $plaintext === $msg ? 'Success' : 'Error';
```

```php
$msg = 'This is the message to authenticate!';
$key = random_bytes(SODIUM_CRYPTO_SECRETBOX_KEYBYTES); // 256 bit

// Generate the Message Authentication Code
$mac = sodium_crypto_auth($msg, $key);

// Altering $mac or $msg, verification will fail
echo sodium_crypto_auth_verify($mac, $msg, $key) ? 'Success' : 'Error';
```

> [🌐 Reference](https://www.zend.com/blog/libsodium-and-php-encrypt)