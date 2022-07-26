# 4.7-skillbox


#### Создание самоподписанного сертификата

sudo apt install openssl
mkdir cert
cd cert
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt
где:
-x509 — уточнение, что нам нужен именно самоподписанный сертификат;
-newkey — автоматическое создание ключа сертификата;
-days — срок действия сертификата в днях;
-keyout — путь (если указан) и имя файла ключа;
-out —  путь (если указан) и имя файла сертификата.
--+---+
Country Name (2 letter code) [AU]:RU
State or Province Name (full name) [Some-State]:
Locality Name (eg, city) []:Moscow
Organization Name (eg, company) [Internet Widgits Pty Ltd]:My Compony              
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []:my-compony.ru
Email Address []:

#### Для запуска утилиты htpasswd
sudo apt install apache2-utils -y

#### Создаём пользователя и пароль

