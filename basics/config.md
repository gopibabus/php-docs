# 🔥PHP Configuration (php.ini)

?> The **php.ini** file defines the configuration for each PHP environment.

> PHP offers a flexible configuration strategy whereby base configuration settings may be overridden by user configuration files and even at runtime by PHP itself.

?> In addition to the php.ini file, it is possible to specify a directory that PHP will scan for additional configuration files. Additional **ini** files will override the settings in **php.ini**. It will only affect settings that are flagged as **PHP_INI_PERDIR or PHP_INI_USER**.

?> If you are using **Apache**, then you can use **.htaccess** to manage user INI settings. You must set the **AllowOverride** setting in your vhost config to true in any directories that you want the **.htaccess** file to be read.

?> You can use the **php_ini_scanned_files()** function to obtain a list of the files that were included, as well as the order of inclusion.

?> The config file is read whenever the server (apache) or process (fpm/cli) starts.

?> It is possible to use OS environment variables in your PHP.ini file.

```bash
; PHP_MEMORY_LIMIT is taken from environment
memory_limit = ${PHP_MEMORY_LIMIT}
```

### ❇php.ini Directives

| Directive                         | Purpose                                                                                     | Default Value     |
| --------------------------------- | ------------------------------------------------------------------------------------------- | ----------------- |
| enable_safe_mode = on             | Safe mode is most relevant to CGI use.                                                      | ON                |
| register_globals = on             | EGPCS (Environment, GET, POST, Cookie, Server) variables are registered as global variables | ON                |
| upload_max_filesize               | Maximum allowed size for uploaded files in the scripts.                                     |                   |
| post_max_size                     | Maximum allowed size of POST data that PHP will accept.                                     |                   |
| upload_tmp_dir = [DIR]            | Don’t uncomment this setting.                                                               |                   |
| display_errors = off              | Showing errors.                                                                             | OFF               |
| error_reporting = E_ALL           | Types of errors to be shown.                                                                | E_ALL & ~E_NOTICE |
| error_prepend_string = [“”]       | Make different color of messages.                                                           |                   |
| max_execution_time = 30           | Maximum execution time is set to seconds for any script.                                    | 30                |
| short_open_tags = Off             | To use XML functions, we have to set this option as off.                                    | OFF               |
| auto-prepend-file = [filepath]    | Automatically **include() file** at the beginning of every PHP file.                        |                   |
| auto-append-file = [filepath]     | Automatically **include() file** it at the end of every PHP file.                           |                   |
| include_path = [DIR]              | Require multiple files from the specified directories.                                      |                   |
| doc_root = [DIR]                  | To apply PHP to certain portion of a website.                                               |                   |
| file_uploads = [on/off]           | This flag is set to ON if file uploads are included in the PHP code.                        |                   |
| mysql.default_host = hostname     | To connect to MySQL default server.                                                         |                   |
| mysql.default_user = username     | To connect to MySQL default username.                                                       |                   |
| mysql.default_password = password | To connect to MySQL default password.                                                       |                   |

> [🌐 PHP.ini Directives](basics/directives.md)

> [🌐 PHP.ini Config file](basics/php.ini.md)
