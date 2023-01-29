# php.ini 

1. Add the following string in order to disable the insecure functions:

```
disable_functions = phpinfo, system, mail, exec
```
An additional security can be obtained by disabling the following functions:
```
disable_functions = exec,passthru,shell_exec,system,proc_open,popen,curl_exec,curl_multi_exec,parse_ini_file,show_source
```
insecure php functions

2. Scope the allowed resources amount, if it is acceptable for your application:

Maximum script execution time (in seconds) 
```
max_execution_time = 30
```
Maximum time for request data parsing by each script 
```
max_input_time = 60
```
Maximum size of uploaded file 
```
upload_max_filesize = 2M
```
Maximum script memory amount (8MB) 
```
memory_limit = 8M (the default value is 128M, but it is acceptable to set the lower one if it won’t decrease your application performance)
```
Maximum POST data size, acceptable for PHP 
```
post_max_size = 8M
```
3. The following list of functions can be restricted in the case they aren’t necessary for your application:

Disallow HTTP file uploads 
```
file_uploads = Off
```
Disallow displaying the PHP error messages for the end-users 
```
display_errors = Off
```
Limit the external access to your PHP environment 
```
safe_mode_allowed_env_vars = PHP_
```
Restrict the sending back of PHP information 
``` 
expose_php = Off
```
Turn off the globals registration for input data 
```
register_globals = Off
```
Restrict remote files opening 
```
allow_url_fopen = Off
```
4. In order to get more information about the security state, enable the following functions:

Ensure appropriateness of PHP redirecting 
```
cgi.force_redirect = 0
```
Enable all possible errors 
```
logging log_errors = On
```
5. Switch on available safe modes:

Enable safe mode 
```
safe_mode = On
```
Enable SQL safe mode 
```
sql.safe_mode = On
```
