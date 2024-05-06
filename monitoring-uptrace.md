## Monitoring WordPress with Uptrace

> [!TIP]
> - https://uptrace.dev/get/opentelemetry-php.html#already-using-otlp-exporter

> [!NOTE]
> Compile PHP extension refer to https://github.com/si294r/howto-wp/blob/main/compile-php-ext-on-windows-vs2019.md

- Configure opentelemetry & protobuf extension
  - compile extension https://pecl.php.net/get/opentelemetry-1.0.2.tgz
  - enable `extension=opentelemetry` in `php.ini`
  - compile extension https://pecl.php.net/get/protobuf-4.26.1.tgz
  - enable `extension=protobuf` in `php.ini`
- go to `cd C:\xampp\otel`, and install auto instrument for wordpress
  ```
  composer require open-telemetry/sdk
  composer require open-telemetry/exporter-otlp
  composer require open-telemetry/opentelemetry-auto-wordpress
  composer require php-http/guzzle7-adapter
  ```
- register free uptrace account
- check email to get API KEY and configure in environment variable
- update `C:\xampp\apache\conf\extra\httpd-xampp.conf`
  ```
  SetEnv OTEL_PHP_AUTOLOAD_ENABLED true
  SetEnv OTEL_SERVICE_NAME local-wordpress-installation
  SetEnv OTEL_TRACES_EXPORTER otlp
  SetEnv OTEL_METRICS_EXPORTER otlp
  SetEnv OTEL_LOGS_EXPORTER otlp
  SetEnv OTEL_EXPORTER_OTLP_ENDPOINT "https://otlp.uptrace.dev"
  SetEnv OTEL_EXPORTER_OTLP_PROTOCOL "http/protobuf"
  SetEnv OTEL_EXPORTER_OTLP_HEADERS "uptrace-dsn=https://[PUT-API-KEY-HERE]@api.uptrace.dev?grpc=4317"
  SetEnv OTEL_EXPORTER_OTLP_COMPRESSION gzip
  SetEnv OTEL_EXPORTER_OTLP_METRICS_DEFAULT_HISTOGRAM_AGGREGATION BASE2_EXPONENTIAL_BUCKET_HISTOGRAM
  SetEnv OTEL_EXPORTER_OTLP_METRICS_TEMPORALITY_PREFERENCE DELTA
  SetEnv OTEL_BSP_EXPORT_TIMEOUT 10000
  SetEnv OTEL_BSP_MAX_EXPORT_BATCH_SIZE 10000
  SetEnv OTEL_BSP_MAX_QUEUE_SIZE 30000
  SetEnv OTEL_BSP_MAX_CONCURRENT_EXPORTS 2
  ```
- update `C:\xampp\htdocs\.htaccess`
  ```
  php_value auto_prepend_file "C:/xampp/otel/vendor/autoload.php"
  ```

![image](https://github.com/si294r/howto-wp/assets/10229458/6895babf-9a83-45ed-bf6b-f02a210a4b42)
