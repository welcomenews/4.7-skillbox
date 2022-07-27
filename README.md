# 4.7-skillbox

```
## Если используем самоподписываемый сертификат то

$ sudo apt install openssl
$ vim /etc/ssl/openssl.cnf 
находим [ v3_ca ] и под ним пишем
subjectAltName = IP:192.168.1.96 <-- это IP наш 


$ vim /usr/lib/systemd/system/docker.service
находим блок [Service] и в него дописываем
Environment=GODEBUG=x509ignoreCN=0
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker.service

## Создание самоподписанного сертификата
mkdir cert
cd cert
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mykey.key -out mycert.crt
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
Common Name (e.g. server FQDN or YOUR name) []:192.168.1.96  <-- это IP наш 
Email Address []:

$ openssl dhparam -out dhparam.pem 2048

$ mkdir -p /etc/docker/certs.d/192.168.1.96/
туда кидаем наш серт mycert.crt только переиновать там его нужно в ca.crt


```
#### Для запуска утилиты htpasswd
sudo apt install apache2-utils -y

#### Создаём пользователя и пароль
htpasswd -B -c ./auth/htpasswd sergey  <-- имя



