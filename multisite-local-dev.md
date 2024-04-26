
## Wordpress Multisite Local Development - Optional

1. Setup wp-config.php
	- `define( 'WP_ALLOW_MULTISITE', true );`
	
3. Move source code to folder `c:/xampp/htdocs/[*.php]`,
	- rename existing file `c:/xampp/htdocs/index.php`

3. Update Query
   ```
   UPDATE `wp_users` SET `user_url` = 'http://localhost/' WHERE `wp_users`.`ID` = 1;
   UPDATE `wp_options` SET `option_value` = 'http://localhost' WHERE `wp_options`.`option_id` = 1; 
   UPDATE `wp_options` SET `option_value` = 'http://localhost' WHERE `wp_options`.`option_id` = 2;
   UPDATE `wp_yoast_indexable` SET `permalink` = 'http://localhost/' WHERE `wp_yoast_indexable`.`id` = 3;
   UPDATE `wp_yoast_seo_links` SET `url` = 'http://localhost/wp-admin/' WHERE `wp_yoast_seo_links`.`id` = 1;
   ```
	- Important : change `localhost` to `lebihcerdas.local`

4. Setup DNS to enable multi subdomain using wildcards
	- For Windows Download Acrylic DNS Proxy (https://mayakron.altervista.org/support/acrylic/Home.htm)
	- Install and run Acrylic UI, then go to menu File >> Open Acrylic Hosts, and add local domain
    ```
    127.0.0.1 localhost localhost.localdomain lebihcerdas.local *.lebihcerdas.local
    ::1 localhost localhost.localdomain lebihcerdas.local *.lebihcerdas.local
    ```
    <img width="723" alt="acrylic" src="https://github.com/si294r/howto-wp/assets/10229458/e79897dc-ab49-4e2e-8437-844238b25413">
    <br /><br />

	- Configure Network Setting in Windows 11 to use local DNS, see here :
		https://mayakron.altervista.org/support/acrylic/Windows10Configuration.htm
    <br />
    <img width="532" alt="configure dns IPv4" src="https://github.com/si294r/howto-wp/assets/10229458/fea92184-e96b-4aa6-b74d-e430c5d9ef50">
    <br /><br />
    <img width="680" alt="configure dns IPv6" src="https://github.com/si294r/howto-wp/assets/10229458/3ce5319e-4a89-496b-8425-058cfde8e254">

5. In wordpress admin go to menu Tools >> Network Setup 
	- select sub-domains and click install 

6. Update `wp-config.php`, after `define( 'WP_ALLOW_MULTISITE', true );`, add this line :
   ```
   define( 'MULTISITE', true );
   define( 'SUBDOMAIN_INSTALL', true );
   define( 'DOMAIN_CURRENT_SITE', 'lebihcerdas.local' );
   define( 'PATH_CURRENT_SITE', '/' );
   define( 'SITE_ID_CURRENT_SITE', 1 );
   define( 'BLOG_ID_CURRENT_SITE', 1 );
   ```
	
7. Update `.htaccess`
   ```
   RewriteEngine On
   RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
   RewriteBase /
   RewriteRule ^index\.php$ - [L]
   
   # add a trailing slash to /wp-admin
   RewriteRule ^wp-admin$ wp-admin/ [R=301,L]
   
   RewriteCond %{REQUEST_FILENAME} -f [OR]
   RewriteCond %{REQUEST_FILENAME} -d
   RewriteRule ^ - [L]
   RewriteRule ^(wp-(content|admin|includes).*) $1 [L]
   RewriteRule ^(.*\.php)$ $1 [L]
   RewriteRule . index.php [L]
   ```
