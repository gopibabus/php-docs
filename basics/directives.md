# 🔥PHP CONFIG FILE

<img alt="php.ini" width="=700" src="/assets/images/phpini.jpg" />

[REFERENCE](http://git.php.net/?p=php-src.git;a=blob;f=php.ini-production;hb=HEAD)

---

## How To Find PHP (php.ini) Configuration File

* PHP can be controlled from the terminal using **php command line utility**, in conjunction with the **-i** switch which enables showing of PHP information and configurations and grep command help you to can find the PHP configuration file

    ```text
    php -i | grep "Loaded Configuration File"

    Output:
    Loaded Configuration File => /etc/php/7.2/cli/php.ini
    ```

---

## About php.ini

> PHP's initialization file, generally called php.ini, is responsible for
> configuring many of the aspects of PHP's behavior.

PHP comes packaged with two INI files. One that is recommended to be used in production environments and one that is recommended to be used in development environments.

`php.ini-production` contains settings which hold security, performance and best practices at its core. But please be aware, these settings may break compatibility with older or less security conscience applications. We recommending using the production ini in production and testing environments.

`php.ini-development` is very similar to its production variant, except it is much more verbose when it comes to errors. We recommend using the development version only in development environments, as errors shown to application users can inadvertently leak otherwise secure information.

---

## PHP Configuration Hierarchy

PHP attempts to find and load this configuration from a number of locations.
The following is a summary of its search order:

1. SAPI module specific location.
2. The PHPRC environment variable.
3. A number of predefined registry keys on Windows
4. Current working directory (except CLI)
5. The web server's directory (for SAPI modules), or directory of PHP (otherwise in Windows)
6. The directory from the `--with-config-file-path` compile time option, or the Windows directory **(C:\windows or C:\winnt)**

---

## About PHP Directives and their Values

* Directives following the section heading `[PATH=/www/mysite]` only apply to PHP files in the `/www/mysite` directory.

* Directives following the section heading `[HOST=www.example.com]` only apply to PHP files served from `www.example.com`.

* Directives set in these special sections cannot be overridden by user-defined INI files or at runtime.

* Currently, `[PATH=]` and `[HOST=]` sections only work under `CGI/FastCGI`.

* Directives are specified using the following syntax:
  * directive = value
  * Directive names are *case sensitive* - foo=bar is different from FOO=bar.
  * Directives are variables used to configure PHP or PHP extensions.
  * There is no name validation.  If PHP can't find an expected directive because it is not set or is mistyped,
  a default value will be used.

> The value can be a string, a number, a PHP constant (e.g. E_ALL or M_PI), one
> of the INI constants (On, Off, True, False, Yes, No and None) or an expression
> (e.g. E_ALL & ~E_NOTICE), a quoted string ("bar"), or a reference to a
> previously set variable or directive (e.g. ${foo})

---

## Expressions in INI file

Expressions in the INI file are limited to bitwise operators and parentheses:

* |  bitwise OR
* ^  bitwise XOR
* &  bitwise AND
* ~  bitwise NOT
* !  boolean NOT

Boolean flags can be turned on using the values 1, On, True or Yes.
They can be turned off using the values 0, Off, False or No.

An empty string can be denoted by simply not writing anything after the equal
sign, or by using the None keyword:

* `foo =`         : sets foo to an empty string
* `foo = None`    : sets foo to an empty string
* `foo = "None"`  : sets foo to the string 'None'

> If you use constants in your value, and these constants belong to a
> dynamically loaded extension (either a PHP extension or a Zend extension),
> you may only use these constants *after* the line that loads the extension.

---

## php.ini-development INI file

### Commonly Used Settings

Complete explanation of all settings are included in the later part in this document

* display_errors
  * Default Value: On
  * Development Value: On
  * Production Value: Off

* display_startup_errors
  * Default Value: Off
  * Development Value: On
  * Production Value: Off

* error_reporting
  * Default Value: E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED
  * Development Value: E_ALL
  * Production Value: E_ALL & ~E_DEPRECATED & ~E_STRICT

* html_errors
  * Default Value: On
  * Development Value: On
  * Production value: On

* log_errors
  * Default Value: Off
  * Development Value: On
  * Production Value: On

* max_input_time
  * Default Value: -1 (Unlimited)
  * Development Value: 60 (60 seconds)
  * Production Value: 60 (60 seconds)

* output_buffering
  * Default Value: Off
  * Development Value: 4096
  * Production Value: 4096

* register_argc_argv
  * Default Value: On
  * Development Value: Off
  * Production Value: Off

* request_order
  * Default Value: None
  * Development Value: "GP"
  * Production Value: "GP"

* session.gc_divisor
  * Default Value: 100
  * Development Value: 1000
  * Production Value: 1000

* session.sid_bits_per_character
  * Default Value: 4
  * Development Value: 5
  * Production Value: 5

* short_open_tag
  * Default Value: On
  * Development Value: Off
  * Production Value: Off

* variables_order
  * Default Value: "EGPCS"
  * Development Value: "GPCS"
  * Production Value: "GPCS"

---

## User defined php.ini

* Name for user-defined php.ini (.htaccess) files. Default is ".user.ini"

    ```text
    user_ini.filename = ".user.ini"
    ```

* To disable this feature set this option to empty value

    ```text
    user_ini.filename =
    ```

* TTL(time-to-live) for user-defined php.ini files in seconds. Default is 300 seconds (5 minutes)

    ```text
    user_ini.cache_ttl = 300
    ```

---

## Language Options(Devlopment Environment)

1. Enable the PHP scripting language engine under Apache. Turns PHP parsing on or off. This directive is really only useful in the Apache module version of PHP. It is used by sites that would like to turn PHP parsing on and off on a per-directory or per-virtual server basis. By putting engine off in the appropriate places in the httpd.conf file, PHP can be enabled or disabled.

    ```text
    engine = On
    ```

2. This directive determines whether or not PHP will recognize code between `<? and ?>` tags as PHP source which should be processed as such. It is generally recommended that `<?php and ?>` should be used and that this feature should be disabled, as enabling it may result in issues when generating XML documents `<?xml ?>`, however this remains supported for backward compatibility reasons.

    > Note that this directive does not control the `<?=` shorthand tag, which can be used regardless of this directive.
    >> Default Value: On </br>
    >> Development Value: Off </br>
    >> Production Value: Off </br>

    ```text
    short_open_tag = Off
    ```

3. The number of significant digits displayed in floating point numbers.

    ```text
    precision = 14
    ```

4. Output buffering is a mechanism for controlling how much output data (excluding headers and cookies) PHP should keep internally before pushing that data to the client. If your application's output exceeds this setting, PHP will send that data in chunks of roughly the size you specify. Turning on this setting and managing its maximum buffer size can yield some interesting side-effects depending on your application and web server. You may be able to send headers and cookies after you've already sent output through print or echo. You also may see performance benefits if your server is emitting less packets due to buffered output versus PHP streaming the output as it gets it. On production servers, 4096 bytes is a good setting for performance reasons.

    > Note: Output buffering can also be controlled via Output Buffering Control functions.</br>
    >> On = Enabled and buffer is unlimited. (Use with caution)</br>
    >> Off = Disabled</br>
    >> Integer = Enables the buffer and sets its maximum size in bytes.</br>
    >>
    >> Note: This directive is hardcoded to Off for the CLI SAPI></br>
    >>Default Value: Off</br>
    >>Development Value: 4096</br>
    >>Production Value: 4096

    ```text
    output_buffering = 4096
    ```

5. You can redirect all of the output of your scripts to a function.  For example, if you set output_handler to "mb_output_handler", character encoding will be transparently converted to the specified encoding. Setting any output handler automatically turns on output buffering.

    > Note: People who wrote portable scripts should not depend on this
    > ini directive. Instead, explicitly set the output handler using ob_start().</br>
    > Using this ini directive may cause problems unless you know what script
    > is doing.</br>
    >
    > Note: You cannot use both "mb_output_handler" with "ob_iconv_handler"
    > and you cannot use both "ob_gzhandler" and "zlib.output_compression".
    >
    > Note: output_handler must be empty if this is set 'On' !!!!</br>
    > Instead you must use zlib.output_handler.</br>
    > [Reference](http://php.net/output-handler)</br>

    ```text
    output_handler =
    ```

6. URL rewriter function rewrites URL on the fly by using output buffer. You can set target tags by this configuration. "form" tag is special tag. It will add hidden input tag to pass values. Refer to session.trans_sid_tags for usage.

    > Default Value: "form="</br>
    > Development Value: "form="</br>
    > Production Value: "form="</br>

    ```text
    url_rewriter.tags
    ```

7. URL rewriter will not rewrites absolute URL nor form by default. To enable absolute URL rewrite, allowed hosts must be defined at RUNTIME. Refer to session.trans_sid_hosts for more details.

    > Default Value: ""</br>
    > Development Value: ""</br>
    > Production Value: ""</br>

    ```text
    url_rewriter.hosts
    ```
