# SSL

Проверить сертификат можно с помощью утилиты `openssl` двумя способами

* Запросить информацию о локальных сертификатах, там нужно смотреть на Subject и Issuer, должна выстроиться полная цепочка от CA до конечного сертификата

  ```bash
  openssl x509 -text -noout -in site.crt
  ```

* Второй способ можно использовать, если сертификат уже установлен на сервере:

  ```bash
  openssl s_client -connect site.com:443
  ```

  Сверху в выводе будет полный Certificate chain