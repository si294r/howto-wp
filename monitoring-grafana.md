## Monitoring WordPress with Grafana

> [!TIP]
> - https://grafana.com/docs/grafana-cloud/monitor-applications/application-observability/setup/quickstart/php/
> - https://github.com/open-telemetry/opentelemetry-php-instrumentation

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
- register free grafana account
- follow the docs to get API Token and configure in environment variable
- update `C:\xampp\apache\conf\extra\httpd-xampp.conf`
  ```
  SetEnv OTEL_PHP_AUTOLOAD_ENABLED true
  SetEnv OTEL_SERVICE_NAME local-wordpress-installation
  SetEnv OTEL_TRACES_EXPORTER otlp
  SetEnv OTEL_METRICS_EXPORTER otlp
  SetEnv OTEL_LOGS_EXPORTER otlp
  SetEnv OTEL_PROPAGATORS baggage,tracecontext
  SetEnv OTEL_EXPORTER_OTLP_PROTOCOL "http/protobuf"
  SetEnv OTEL_EXPORTER_OTLP_ENDPOINT "https://otlp-gateway-prod-ap-southeast-1.grafana.net/otlp"
  SetEnv OTEL_EXPORTER_OTLP_HEADERS "Authorization=Basic [PUT-API-TOKEN-HERE]"
  ```
- update `C:\xampp\htdocs\.htaccess`
  ```
  php_value auto_prepend_file "C:/xampp/otel/vendor/autoload.php"
  ```

![image](https://github.com/si294r/howto-wp/assets/10229458/a7e9525a-8d36-47ef-8a24-5fae9cfb9be8)
