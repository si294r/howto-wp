
## Compile PHP Extension on Windows VS2022

### EXPERIMENTAL ONLY !!!

### NOTE: PHP Development Package doesn't provide for VS2022, for this step we use package for VS2019
	
### Old Reference - https://damjan.cvetko.org/blog/2021-09-01-php-compiling-ext-update/

1. Install Visual Studio Community 2022: https://visualstudio.microsoft.com/downloads/
![image](https://github.com/si294r/howto-wp/assets/10229458/07dc9377-dc8e-46e5-a514-2392414091c5)
	- install with checkout Desktop Development with C++
![image](https://github.com/si294r/howto-wp/assets/10229458/cc2d3a0d-c0d5-4013-860d-01dd58d5bd46)

3. Clone git https://github.com/php/php-sdk-binary-tools (use Github Desktop)
	- to folder `C:\php-sdk`
	- use branch `master`

4. Download Development Package (SDK to develop PHP extensions)
	- from https://windows.php.net/download/
	-	example from https://windows.php.net/downloads/releases/php-devel-pack-8.3.6-Win32-vs16-x64.zip
	- then extract to `C:\php-devel`

5. Download Extension Source from PECL, example APCu
	- from https://pecl.php.net/get/apcu-5.1.23.tgz
	- then extract to `C:\php-ext\apcu-5.1.23`
	
6. In `C:\php-sdk`
- run php sdk script accordingly 
```
C:\php-sdk>phpsdk-vs17-x64.bat
[vcvarsall.bat] Environment initialized for: 'x64'

PHP SDK 2.2.1-dev

OS architecture:    x64
Build architecture: x64
Visual C++:         14.39.33523.0
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
  Detected compiler Visual C++ 2022
  Detected x64 compiler
  
.....

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
| Compiler            | Visual C++ 2022 |
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
		
- run `nmake`
```
$ nmake

Microsoft (R) Program Maintenance Utility Version 14.39.33523.0
Copyright (C) Microsoft Corporation.  All rights reserved.

.......

   Creating library C:\php-ext\apcu-5.1.23\x64\Release_TS\php_apcu.lib and object C:\php-ext\apcu-5.1.23\x64\Release_TS\php_apcu.exp
EXT apcu build complete

C:\php-ext\apcu-5.1.23
$
```
