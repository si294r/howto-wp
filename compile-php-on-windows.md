
## Compile PHP on Windows

> [!TIP]
> Old Reference - https://medium.com/@erinus/how-to-build-php-on-windows-a7ad0a87862a

> [!WARNING]
> EXPERIMENTAL ONLY !!! <br />
> The compilation results here are not used in local development 

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

4. In `C:\php-sdk`
- run `phpsdk-vs16-x64.bat`
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
  
- run `phpsdk_buildtree php-dev`
```
$ phpsdk_buildtree php-dev

C:\php-sdk\php-dev\vs16\x64
$
```

- download php source
	- from https://windows.php.net/downloads/releases/php-8.3.6-src.zip
	- extract to `C:\php-sdk\php-dev\vs16\x64\php-8.3.6-src`
		
- `cd php-8.3.6-src`
```
$ cd php-8.3.6-src

C:\php-sdk\php-dev\vs16\x64\php-8.3.6-src
```
	
- run `phpsdk_deps -u`
```
$ phpsdk_deps -u
INFO: Could not find files for the given pattern(s).

Configuration: 8.3-vs16-x64-stable

Processing package apache-2.4.43-vs16-x64.zip
Processing package c-client-2007f-1-vs16-x64.zip
Processing package fbclient-3.0.6-nocrt-x64.zip
Processing package freetype-2.11.1-vs16-x64.zip
Processing package glib-2.53.3-1-vs16-x64.zip
Processing package ICU-72.1-vs16-x64.zip
Processing package libargon2-20190702-vs16-x64.zip
Processing package libavif-0.9.0-1-vs16-x64.zip
Processing package libbzip2-1.0.8-vs16-x64.zip
Processing package libcurl-8.7.1-vs16-x64.zip
Processing package libenchant2-2.2.8-vs16-x64.zip
Processing package libffi-3.3-4-vs16-x64.zip
Processing package libiconv-1.16-5-vs16-x64.zip
Processing package libintl-0.18.3-8-vs16-x64.zip
Processing package libjpeg-turbo-2.1.0-vs16-x64.zip
Processing package liblmdb-0.9.22-6-vs16-x64.zip
Processing package liblzma-5.2.5-vs16-x64.zip
Processing package libonig-6.9.8-vs16-x64.zip
Processing package libpng-1.6.34-8-vs16-x64.zip
Processing package libpq-11.4-1-vs16-x64.zip
Processing package libqdbm-1.8.78-vs16-x64.zip
Processing package libsasl-2.1.27-3-vs16-x64.zip
Processing package libsodium-1.0.18-vs16-x64.zip
Processing package libssh2-1.10.0-2-vs16-x64.zip
Processing package libtidy-5.6.0-2-vs16-x64.zip
Processing package libwebp-1.3.2-vs16-x64.zip
Processing package libxml2-2.10.3-vs16-x64.zip
Processing package libxpm-3.5.12-8-vs16-x64.zip
Processing package libxslt-1.1.37-vs16-x64.zip
Processing package libzip-1.7.1-1-vs16-x64.zip
Processing package mpir-3.0.0-vs16-x64.zip
Processing package net-snmp-5.7.3-3-vs16-x64.zip
Processing package nghttp2-1.51.0-vs16-x64.zip
Processing package openldap-2.4.47-1-vs16-x64.zip
Processing package openssl-3.0.13.pl1-vs16-x64.zip
Processing package sqlite3-3.40.0-vs16-x64.zip
Processing package wineditline-2.206-vs16-x64.zip
Processing package zlib-1.2.12-vs16-x64.zip
Updates performed successfully.
Old dependencies backed up into 'C:\php-sdk\php-dev\vs16\x64\deps.202404190217'.

C:\php-sdk\php-dev\vs16\x64\php-8.3.6-src
$
```
		
- run `configure --disable-all --enable-cli`
```
$ configure --disable-all --enable-cli
PHP Version: 8.3.6

Saving configure options to config.nice.bat
Checking for cl.exe ...  <in default path>
  Detected compiler Visual C++ 2019
  Detected x64 compiler
Checking for link.exe ...  <in default path>
Checking for nmake.exe ...  <in default path>
Checking for lib.exe ...  <in default path>
Checking for bison.exe ...  <in default path>
  Detected bison version 3.3.2
Checking for sed.exe ...  <in default path>
Checking for re2c.exe ...  <in default path>
  Detected re2c version 1.1.1
Checking for zip.exe ...  <in default path>
Checking for lemon.exe ...  <in default path>
Checking for 7za.exe ...  <in default path>
Checking for mc.exe ...  C:\Program Files (x86)\Windows Kits\10\bin\10.0.22621.0\x64
Checking for mt.exe ...  C:\Program Files (x86)\Windows Kits\10\bin\10.0.22621.0\x64
Enabling multi process build

Build dir: C:\php-sdk\php-dev\vs16\x64\php-8.3.6-src\x64\Release_TS
PHP Core:  php8ts.dll and php8ts.lib
Checking for ML64.exe ...  <in default path>

Checking for wspiapi.h ...  <in default path>
Enabling IPv6 support
Enabling SAPI sapi\cli
Checking for library edit_a.lib;edit.lib ... <in deps path> \lib\edit_a.lib
Checking for editline/readline.h ...  <in deps path> \include
Enabling extension ext\date
Enabling extension ext\hash
Checking for KeccakHash.h ...  ext/hash/sha3/generic64lc
Checking for PMurHash.h ...  ext/hash/murmur
Checking for xxhash.h ...  ext/hash/xxhash
Enabling extension ext\json
Enabling extension ext\pcre
Enabling extension ext\random
Enabling extension ext\reflection
Enabling extension ext\spl
Checking for timelib_config.h ...  ext/date/lib
Enabling extension ext\standard

Creating build dirs...
Generating files...
Generating Makefile
Generating main/internal_functions.c
Generating main/config.w32.h
Generating phpize
Done.



Enabled extensions:
-----------------------
| Extension  | Mode   |
-----------------------
| date       | static |
| hash       | static |
| json       | static |
| pcre       | static |
| random     | static |
| reflection | static |
| spl        | static |
| standard   | static |
-----------------------


Enabled SAPI:
-------------
| Sapi Name |
-------------
| cli       |
-------------


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

C:\php-sdk\php-dev\vs16\x64\php-8.3.6-src
$
```
		
- run `nmake`
	
- the compiled PHP will be :
  `C:\php-sdk\php-dev\vs16\x64\php-8.3.6-src\x64\Release_TS`

