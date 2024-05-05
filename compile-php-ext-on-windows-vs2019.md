
## Compile PHP Extension on Windows VS2019

> [!TIP]
> Old Reference - https://damjan.cvetko.org/blog/2021-09-01-php-compiling-ext-update/

1. Install Visual Studio Community 2019 from microsoft store: https://apps.microsoft.com/search?query=Visual+Studio+Community+2019&hl=en-us&gl=US
![image](https://github.com/si294r/howto-wp/assets/10229458/07dc9377-dc8e-46e5-a514-2392414091c5)
	- Install with checkout Desktop Development with C++
	- On Installation details add :
		- MSVC v142 - VS 2019 C++ build tools (Latest)
		- Windows 11 SDK
  <img width="929" alt="image" src="https://github.com/si294r/howto-wp/assets/10229458/71b8dda1-c60a-42c5-a89c-6d8330a84045">
	
3. Clone git https://github.com/php/php-sdk-binary-tools (use Github Desktop)
	- to folder `C:\php-sdk`
	- use branch `master`

4. Download Development Package (SDK to develop PHP extensions)
	- from https://windows.php.net/download/
	- example from https://windows.php.net/downloads/releases/php-devel-pack-8.3.6-Win32-vs16-x64.zip
	- then extract to `C:\php-devel`

5. Download Extension Source from PECL, example APCu
	- from https://pecl.php.net/get/apcu-5.1.23.tgz
	- then extract to `C:\php-ext\apcu-5.1.23`

6. In `C:\php-sdk`
- run php sdk script accordingly
```
C:\php-sdk>phpsdk-vs16-x64.bat
[vcvarsall.bat] Environment initialized for: 'x64'

PHP SDK 2.2.1-dev

OS architecture:    x64
Build architecture: x64
Visual C++:         14.29.30154.0
PHP-SDK path:       C:\php-sdk

C:\php-sdk
$
```
		
- go to extension folder accordingly
```
$ cd ..\php-ext\apcu-5.1.23

C:\php-ext\apcu-5.1.23
$
```
		
- run phpize relatively
```
$ ..\..\php-devel\php-8.3.6-devel-vs16-x64\phpize.bat
Rebuilding configure.js
C:\php-devel\php-8.3.6-devel-vs16-x64
module ...
Now run 'configure --help'

C:\php-ext\apcu-5.1.23
$
```
		
- if run `configure --help`, there will be option `--enable-apcu`
	
- run configure.bat accordingly
```
$ configure.bat --enable-apcu
Saving configure options to config.nice.bat
Checking for cl.exe ...  <in default path>
  Detected compiler Visual C++ 2019
  Detected x64 compiler

.......

Enabled extensions:
----------------------
| Extension | Mode   |
----------------------
| apcu      | shared |
----------------------


-----------------------------------------
|                     |                 |
-----------------------------------------
| Build type          | Release         |
| Thread Safety       | Yes             |
| Compiler            | Visual C++ 2019 |
| Target Architecture | x64             |
| Host Architecture   | x64             |
| Optimization        | PGO disabled    |
| Native intrinsics   | SSE2            |
| Static analyzer     | disabled        |
-----------------------------------------


Type 'nmake' to build PHP

C:\php-ext\apcu-5.1.23
$
```
		
- run `nmake`, or `nmake clean && nmake` to rebuild
```
$ nmake clean && nmake

Microsoft (R) Program Maintenance Utility Version 14.29.30154.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Cleaning PECL targets only
		rd /s /q C:\php-ext\apcu-5.1.23\x64\Release_TS\pecl
The system cannot find the file specified.
Cleaning distribution build dirs
		cd C:\php-ext\apcu-5.1.23\x64\Release_TS
Could Not Find C:\php-ext\apcu-5.1.23\x64\Release_TS\*.res

Microsoft (R) Program Maintenance Utility Version 14.29.30154.0
Copyright (C) Microsoft Corporation.  All rights reserved.

..........

   Creating library C:\php-ext\apcu-5.1.23\x64\Release_TS\php_apcu.lib and object C:\php-ext\apcu-5.1.23\x64\Release_TS\php_apcu.exp
EXT apcu build complete

C:\php-ext\apcu-5.1.23
$
```
		
7. copy result dll to php extension folder, ex :
	- from `C:\php-ext\apcu-5.1.23\x64\Release_TS\php_apcu.dll`
	- to `C:\xampp\php\ext\php_apcu.dll`
		
8. re-configure php.ini and restart apache

