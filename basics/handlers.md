# 🔥PHP Handlers

<img src="./assets/images/php_handlers.png" alt="php handlers" width="700" height="400"/>

> Remember that web servers are designed to send static resources including HTML, images, etc., to users. They are not designed to interpret any code themselves. Out of the box none of the major web servers can handle PHP by themselves so they need another program to do it for them. This program, known as a PHP handler.

?> **PHP handlers** are the programs that interpret the PHP code in your web application and process it to be sent as HTML (or another static format) by your web server.

Currently there are 4 major PHP handlers available on Apache. Each of these handle memory, CPU, and file permissions in a different way which can then manifest itself in your web app in everything from performance to important features of your application.

* mod_php (AKA DSO)
* CGI
* FastCGI
* suPHP

!> If you are using nginx web server, it requires **FastCGI**.

## ⚡mod_php (DSO)

?>  **DSO (which is short for Dynamic Shared Object)** or **mod_php** is the oldest and, some would say, the **fastest PHP handler** available.

### ✳Pros
* It essentially makes PHP a part of Apache by having the Apache server interpret the PHP code itself through use of an Apache module known as mod_php.
* This is the **default handler typically installed when installing a web server** package on your server.
* **mod_php** is very fast as it runs directly in the same process as your Apache server.
* Running it together with Apache also means that it has a **very low CPU and memory** requirement.

### ✳Cons
* As mod_php is that it runs as part of Apache which means that it runs as the same user that your Apache process runs as (if you’re on Ubuntu this would www-data).
* This means that all work on files will be done as the Apache user which therefore must have permissions to all of your files.
* In most cases when you upload files to your server you do so as a different user that has login rights to the machine. This means that all the files and folders you upload are “owned” by the user that you used to upload them. If you don’t give permissions to them to the Apache user the web server will not be able to read or write to the files.
* If you do give access to them to the Apache user and your machine is compromised by an attacker that attacker could have access to much more than just the files in the website they used to get in to your system potentially creating problems for every site hosted on your machine.
* The file permission issue is also the biggest source of headache for users of content management systems such as WordPress or Drupal.
* Because the files of your site are often owned by an account other than that which they are running as, users of mod_php are often unable to upload or modify files from within their CMS without substantial work arounds. This work arounds will add extra complexity, which causes another security hole in your site.

## ⚡CGI

?> CGI(Common Gateway Interface) is used as an interface between the web server and the additionally installed applications generating dynamic web content. These applications are called CGI scripts and are written in different script and programming languages such as PHP, Perl, Python, etc.

### ✳Pros
* **CGI** is the fallback in most servers when **mod_php** is not available.
* Instead of running the PHP code within Apache it is now run as it’s own CGI process, that is, in a program outside of your Apache server.
* By default CGI will be called by the Apache server meaning that it will run as the Apache user.
* Unlike mod_php however CGI has the ability to see the PHP as another user using another Apache module.

### ✳Cons
* CGI will be called by the Apache server meaning that it will run as the Apache user with all the problems of doing so that mod_php encountered.
* For performance CGI is not nearly as fast as mod_php and requires more CPU time.

## ⚡suPHP

?> **suPHP** stands for Single user PHP.

### ✳Pros
* suPHP runs PHP outside of the Apache script as CGI.
* Unlike CGI however it will run the scripts as a user other than the Apache user (presumably the user that owns the files).
* This means that if you are using a CMS you will be able to upload files from within your web application using suPHP.
* Because your PHP is being run as a different user any vulnerability in your site can be restricted to only the files of your website thereby providing substantial security benefits.

### ✳Cons
* The cost of the upload ability and security of suPHP is not cheap.
* suPHP is slow and requires quite a bit of CPU to process all the files.
* As it must process the file each and every time it is called, suPHP cannot use any OPCode caching such as APC or memcached resulting in even higher CPU usage by your application.

## ⚡FastCGI
?> **FastCGI (aka: mod_fcgid or FCGI)** is a high performance variation of CGI.

### ✳Pros
* It offers the security benefits of suPHP by executing files as the owner of the file.
* FastCGI allows the use of OPCode caching such as APC or memcached.
* FastCGI is arguably the fastest handler even in comparison with mod_php.
* If you have the memory for it there really isn’t any reason not to run FastCGI in this day and age.

### ✳Cons
* Unlike suPHP however it keeps open a session for the file when the processing is done resulting in significant memory use.

## ⚡FastCGI Process Manager (FPM)
?> **FPM (FastCGI Process Manager)** is an alternative PHP FastCGI implementation with some additional features (mostly) useful for heavy-loaded sites. FPM is a process manager to manage the FastCGI SAPI (Server API) in PHP. Basically, it replaces the need for something like **SpawnFCGI**. It spawns the FastCGI children adaptively (meaning launching more if the current load requires it).

### ✳Pros
* PHP-FPM maintains pools (workers that can respond to PHP requests) to accomplish handling strenuous loads.
* PHP-FPM is faster than traditional CGI-based methods, such as SUPHP, for multi-user PHP environments. It does not overload a system’s memory with PHP from Apache processes.
* Adaptive process spawning.
* Stdout & stderr logging.
* Advanced process management with graceful stop/start.
* Emergency restart in case of accidental opcode cache destruction.
* Accelerated upload support.
* It has a modern and optimized way of running applications.
* Smaller memory footprint, graceful reload without stopping other queries.

### ✳Cons
* Low security as compared to PHP-CGI.
* Requires more configuration than PHP-CGI.

## ⚡Overall View

|                     | mod\_php | CGI  | suPHP | FastCGI | FPM  |
| ------------------- | -------- | ---- | ----- | ------- | ---- |
| Memory Usage        | Low      | Low  | Low   | High    | Low  |
| CPU Usage           | Low      | High | High  | Low     | High |
| Security            | Low      | Low  | High  | High    | High |
| Run as File Owner   | No       | No   | Yes   | Yes     | Yes  |
| Overall Performance | Fast     | Slow | Slow  | Fast    | Fast |

---

* **CGI** scripts is a way how to run a server side script when a HTTP request comes; this has nothing to do with PHP.
* **FastCGI** is a "better CGI" - CGI is known to be slow, Fast CGI is a different approach with much faster results; this has also nothing to do with PHP.
* By using CGI or FastCGI the server runs an executable binary that is the PHP interpreter. This is an isolated process, performed outside the web server's process.
After changes in the PHP settings (in the php.ini file), a PHP process alone can be restarted without this influencing the web server.

---

* **mod_php** is running a PHP as Apache module - that is PHP request is run under Apache process with everything that goes with it - Apache processes are defined by Apache configuration, PHP is run with Apache permission etc.
* By using PHP as a module on the Apache server (**mod_php**), the PHP interpreter is in the web server code. The PHP process is part of the web server process.
If there are any changes in PHP settings, the web server needs to be restarted so that they take effect. PHP directives (php_flag, php_value...) can be placed in the server's .htaccess file.
* **PHP-FPM** is PHP's FastCGI implementation; PHP-FPM runs as a standalone FastCGI server and Apache connects to the server using Apache's module, usually **mod_fcgid** or **mod_fastcgi**
* In PHP-FPM everything is run under PHP configuration, PHP user and Apache connects to PHP as to a server.
* In PHP-FPM configuration it is also possible to have pool of PHP servers and to have PHP server on physically different machine than Apache.
---

> [🌐 Reference](https://archive.chriswiegman.com/2011/10/fastcgi-vs-suphp-vs-cgi-vs-mod_php-dso/index.html)