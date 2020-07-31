# 🔥Performance

!> Extension **xdebug** is for debugging and should not be installed in production.

?> Keep your PHP version up to date. PHP 7 is about 30%  faster than PHP 5 and some people claim it is even faster. PHP 7.2 is faster than PHP 7.1.

?> PHP uses a container called a **zval** to store variables.

?> PHP will initiate garbage collection when the root buffer is full or when the function **gc_collect_cycles()** is called.

> [🌐 Brief explanation in PHP's Garbage Collection](https://www.sitepoint.com/better-understanding-phps-garbage-collection/)

?> PHP is compiled into a sequence of intermediate instructions that are executed in order by the runtime engine. These instructions are called **opcodes or bytecodes** and this process occurs every time the script is run. The bytecode is interpreted by the runtime engine. Therefore, **PHP is both precompiled and interpreted**. An **opcode cache** stores the converted instructions for a script. Subsequent calls to the script do not require the script to be interpreted prior to being run.

?> In 2013, Zend contributed their optimization engine to PHP. Known as **opcache**, it is baked into distributions of PHP as of version 5.5 and is probably the most commonly used PHP opcode cache.

?> Opcache is built into PHP 7.1 and is enabled by default in your php.ini settings. Using the opcode cache results in significant performance increases.

?> Setting **opcache.revalidate_freq** determines the interval in seconds that PHP will scan for changes in the source file before recompiling it.

?> **PHP extensions** extend on the functionality offered by the core language. **PECL** is a repository for PHP extensions. PHP includes several extensions that cannot be removed from PHP with compilation flags. These extensions include core functionality such as reflection, arrays, date and time, SPL, and math.

?> **Extensions are enabled** through the php.ini file using the “extension” setting to specify the filename of the extension

```bash
extension=mcrypt.so;
```

?> You can **set the extension directory** with a setting in your php.ini file

```bash
extension_dir = "/usr/lib/php5/"
```

?> To show a list of extensions installed.

```bash
php -m
```

?> Check if an extension is loaded.

```php
<?php
if (!extension_loaded('gd')) {
 if (!dl('gd.so')) {
 exit;
 }
}
```

### ❇OPcache Preloading

?> PHP can be configured to preload scripts into the opcache when the engine starts. Any symbols (functions, classes, etc.) in those files will then become globally available for all requests without needing to be explicitly included.

!> This feature is only practical to use in production, not in a development environment.😟

?> **"Preload everything"** may be the easiest strategy, but not necessarily the best strategy. **Preloading** is only useful when there is a persistent process from one request to another.

> Preloading helps to load files responsible for running **PHP CLI apps**.

!> Preloading is not supported on Windows.

```php
# php.ini
opcache.preload=preload.php
```

```php
# preload.php
# pre loading all files from "src" directory.
<?php
$directory = new RecursiveDirectoryIterator(__DIR__ . '/src');
$fullTree = new RecursiveIteratorIterator($directory);
$phpFiles = new RegexIterator($fullTree, '/.+((?<!Test)+\.php$)/i', RecursiveRegexIterator::GET_MATCH);

foreach ($phpFiles as $key => $file) {
    require_once($file[0]);
}
?>
```

[🌍 Reference](https://www.php.net/manual/en/opcache.preloading.php)
