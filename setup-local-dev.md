## Setup Wordpress Local Development

1. Setup XAMPP
    - go to https://www.apachefriends.org/download.html
    - download current version ~ 8.2.12
    - install to folder `c:/xampp`
		
2. Setup Wordpress
    - go to https://id.wordpress.org/download/
    - download current version ~ 6.4.3
    - extract to folder `c:/xampp/htdocs/wordpress/[*.php]`
		
3. Setup phpMyAdmin
    - go to http://localhost/phpmyadmin
    - create database and user for wordpress, follow instruction in here :
      https://developer.wordpress.org/advanced-administration/before-install/howto-install/
			
4. Setup `wp-config.php`
    - follow instruction in here :
      https://developer.wordpress.org/advanced-administration/before-install/howto-install/
			
5. Install Wordpress
    - go to http://localhost/wordpress/wp-admin/install.php
      ```
      user : admin
      password : password
      email : admin.wp@gmail.com
      ```
    - Login go to http://localhost/wordpress/wp-login.php
		
6. Add Plugin
    - Query Monitor, by John Blackbourn
    - Plugin Check (PCP), by WordPress Performance Team and Plugin Review Team 
		
7. WPAdmin > Pengaturan > Umum 
    - Zona waktu : UTC+7

