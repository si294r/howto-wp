## Upgrade PHP Local Development

> [!NOTE] 
> Upgrade to PHP 8.5

 - upgrade to `php 8.5.0`
	- download windows zip - `VS17 x64 Thread Safe (2025-Nov-18 08:24:22 UTC)`
		https://downloads.php.net/~windows/releases/archives/php-8.5.0-Win32-vs17-x64.zip
	  extract to `c:\xampp\php` (rename old directory "php" to "php-8.2.28")
	- download ext
		- apcu : https://downloads.php.net/~windows/pecl/releases/apcu/5.1.28/php_apcu-5.1.28-8.5-ts-vs17-x64.zip
		- opentelemetry : https://downloads.php.net/~windows/pecl/releases/opentelemetry/1.2.1/php_opentelemetry-1.2.1-8.5-ts-vs17-x64.zip
		- protobuf : https://downloads.php.net/~windows/pecl/releases/protobuf/4.33.2/php_protobuf-4.33.2-8.5-ts-vs17-x64.zip
	- copy `C:\xampp\php\php.ini` from prev php directory
	- copy `C:\xampp\php\extras\browscap.ini` from prev php directory

## Old Upgrade

> [!NOTE] 
> Upgrade required to try woocomerce plugin

### NOTES
 - Server Crash when activate woocommerce plugin : The connection was reset.
	- Cek `C:\xampp\htdocs\wp-content\debug.log` : Empty
	- Cek `C:\xampp\php\logs\php_error_log` : Empty
	- Cek `C:\xampp\apache\logs\error.log` : VirtualProtect() failed [87] The parameter is incorrect
 - Search error in google... result : problem with php extension opcache

### Solution 1
 - disable opcache, then activate woocommerce plugin is success

### Solution 2
 - upgrade php from `8.2.12` to `8.2.28`
	- download windows zip - `VS16 x64 Thread Safe (2025-Mar-11 18:57:48)`
		https://windows.php.net/downloads/releases/php-8.2.28-Win32-vs16-x64.zip
	  extract to `c:\xampp\php` (rename old directory "php" to "php-backup-20240505")
	- download ext
		- apcu : https://downloads.php.net/~windows/pecl/releases/apcu/5.1.24/php_apcu-5.1.24-8.2-ts-vs16-x64.zip
		- opentelemetry : https://downloads.php.net/~windows/pecl/releases/opentelemetry/1.1.3/php_opentelemetry-1.1.3-8.2-ts-vs16-x64.zip
		- protobuf : https://downloads.php.net/~windows/pecl/releases/protobuf/4.29.5/php_protobuf-4.29.5-8.2-ts-vs16-x64.zip
	- copy `C:\xampp\php\php.ini` from prev php directory
	- copy `C:\xampp\php\extras\browscap.ini` from prev php directory

### Solution 3
 - upgrade to `php 8.4.8`
	- download windows zip - `VS17 x64 Thread Safe (2025-Jun-03 17:40:02)`
		https://windows.php.net/downloads/releases/php-8.4.8-Win32-vs17-x64.zip
	  extract to `c:\xampp\php` (rename old directory "php" to "php-8.2.28")
	- download ext
		- apcu : https://downloads.php.net/~windows/pecl/releases/apcu/5.1.24/php_apcu-5.1.24-8.4-ts-vs17-x64.zip
		- opentelemetry : https://downloads.php.net/~windows/pecl/releases/opentelemetry/1.1.3/php_opentelemetry-1.1.3-8.4-ts-vs17-x64.zip
		- protobuf : https://downloads.php.net/~windows/pecl/releases/protobuf/4.29.5/php_protobuf-4.29.5-8.4-ts-vs17-x64.zip
	- copy `C:\xampp\php\php.ini` from prev php directory
	- copy `C:\xampp\php\extras\browscap.ini` from prev php directory
