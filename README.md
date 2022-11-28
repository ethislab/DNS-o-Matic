# DNS-o-Matic


This  project is sourced from  https://github.com/davidegironi/espduckdns with bearssl certstore to use with HTTPS Secure client for DNS update like DNS-o-matic it support only Secure client

The first step of this solution is to fetch the certificate store from Mozilla and upload it to your ESP’s SPIFFS. The example above has a handy [Python script](https://github.com/esp8266/Arduino/blob/master/libraries/ESP8266WiFi/examples/BearSSL_CertStore/certs-from-mozilla.py) that downloads the certificates and creates a “certs.ar” file for you. Copy this file into a folder called “data” within your sketch, then upload the file to SPIFFS. There’s [good documentation](https://www.instructables.com/id/Using-ESP8266-SPIFFS/) available describing how to configure Arduino with a tool to do the upload for you.

Now that the certificate store is on SPIFFS, we have to load it into BearSSL. For this purpose, the [BearSSL_CertStore Arduino example](https://github.com/esp8266/Arduino/blob/master/libraries/ESP8266WiFi/examples/BearSSL_CertStore/BearSSL_CertStore.ino) provides a helpful extension for the BearSSL CertStoreFile class that reads the store from SPIFFS.
Additionally, we also need to sync the time for the ESP with NTP, as that’s required for SSL certificate validation.
