## Configuration and Performance

> [!WARNING]
> EVALUATION NEEDED

1. PHP Config `php.ini`
    - set `date.timezone=Asia/Jakarta` 
    - enable `extension=zip` for Composer
    - https://make.wordpress.org/hosting/handbook/server-environment/#php-extensions
      - `extension=intl`
      -	`zend_extension=opcache`
    - enable `extension=sqlite3`
    - enable `extension=apcu`
      - see https://github.com/si294r/howto-wp/blob/main/compile-php-ext-on-windows-vs2019.md
    - enable `extension=opentelemetry` and `extension=protobuf`
      - see Log and Monitoring (https://github.com/si294r/howto-wp/blob/main/monitoring-grafana.md)


2. Database Config `my.ini`, refer to https://www.mysqlcalculator.com/
    ```
    default-time-zone=+07:00
    
    innodb_buffer_pool_size=320M
    ## Set .._log_file_size to 25 % of buffer pool size
    innodb_log_file_size=100M
    innodb_log_buffer_size=160M
    ```

