# 🔥PHP Introduction

?> PHP is an **interpreted**, **high-level**, **general purpose**, **dynamically typed** programming language.

?> PHP is an **multi threaded**, **synchronous** programming language.

?> **SAPI** stands for "Server API". It is the mechanism that controls the interaction between the "outside world" and the PHP/Zend engine. So, you would always want to use it. In fact, you cannot avoid using it without a lot of effort since even **CLI is considered a SAPI**.

### ✳Compiled vs Interpreted Programming Languages

<img src="./assets/images/compliervsinterpreter.png" alt="compliervsinterpreter" width="650" height="400"/>

### ✳High Level vs Low Level Programming languages

<img src="./assets/images/highvslow.png" alt="highvslow" width="600" height="350"/>

### ✳General vs Specific Programming Languages

<img src="./assets/images/generalvsspecific.jpg" alt="generalvsspecific" width="700"/>

### ✳Static vs Dynamically typed Programming Languages

<img src="./assets/images/dynamicvsstatic.png" alt="dynamicvsstatic" width="500"/>

### ✳Multi threaded vs Single threaded

?> Yes, PHP is a multi threaded language. **pthreads** is an object-orientated API that provides all of the tools needed for multi-threading in PHP. PHP applications can create, read, write, execute and synchronize with Threads, Workers and Threaded objects.

!>The pthreads extension **cannot be used in a web server environment**. Threading in PHP is therefore **restricted to CLI-based applications** only.

!> **pthreads (v3) can only be used with PHP 7.2+**: This is due to ZTS mode being unsafe in 7.0 and 7.1.

> [🌐 Reference](https://www.php.net/manual/en/intro.pthreads.php)

### ✳Synchronous vs Asynchronous

<img src="./assets/images/syncvsasync.png" alt="syncvsasync" width="700"/>

> Running **asynchronous** means you don't have to wait for something to happen before continue doing your thing. You send an email and go on with your life until you receive a response. You don't have to remain idle until the response comes back. Whereas synchronous mean you should wait for something to happen before continue doing your thing.

?> PHP code is blocking(synchronous), meaning that one block of code will not run until the block prior to it has finished. It wasn't built with asynchronous execution in mind like Go, NodeJs, and other languages.

> PHP's support for threading was introduced via a separate extension called pthreads, which enables asynchronous behavior in PHP.

?> Spatie has built a package called [spatie/async](https://github.com/spatie/async) which runs and manages several PHP processes to run your code in an asynchronous fashion.

> [🌐 Reference](https://divinglaravel.com/asynchronous-php)