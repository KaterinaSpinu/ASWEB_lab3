# ASWEB_lab3

Постановка задачи

Целью данной работы является обучение добавлению и настройке сайтов (виртуальных хостов). А также, ознакомление с запуском сайтов (виртуальных хостов) в контейнере

Практическая часть

1.	Создайте папку `asweb03`. 
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/a5a06826-445c-4a7b-b393-a461009d1c2f)

2.	Создайте папки `database` - для базы данных, `files` - для хранения конфигураций и `site` - в данной папке будет расположен сайт.
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/5af91c5a-f2e1-4285-a278-9f1b22703a35)
 
3.	Скачиваем с сайта [CMS Wordpress](https://wordpress.org/) и распаковываем в папку `site`. 
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/10ca64a4-1164-42ac-8fa0-39300086c96b)
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/fe464c6d-174a-41ac-a6db-36a278ad0bdd)

Выполним следующие команды: 

4.	Команда скачивает образ httpd и запускает на его основе контейнер с именем httpd
docker run -d --name httpd  httpd:2.4
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/b856e1fd-ff80-4246-bbba-d3bbb2218985)

5.	Копируем конфигурационный файл из контейнера в папку .\files\httpd
docker cp httpd:/usr/local/apache2/conf/httpd.conf .\files\httpd\httpd.conf
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/3ef61665-50c0-4512-8919-56abd857e101)

6.	Останавливаем контейнер httpd
docker stop httpd
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/a406f07e-afb7-4f98-8b1b-d60e763e733e)

7.	 Удаляем контейнер
docker rm httpd
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/e1f0a426-0383-45d4-bb9b-097c8479653e)

8.	В созданом файле `.\files\httpd\httpd.conf` раскоментируем следующие  строки, содержащие подключение расширений `mod_proxy.so`, `mod_proxy_http.so`, `mod_proxy_fcgi.so`.
9.	Добавим следующие строки:
1)	определение доменного имени сайта
ServerName wordpress.localhost:80
2)	 перенаправление php запросов контейнеру php-fpm
ProxyPassMatch ^/(.*\.php(/.*)?)$ fcgi://php-fpm:9000/var/www/html/$1
3)	индексный файл
DirectoryIndex /index.php index.php
4)	 Находим `DocumentRoot` и задаем ему значение `/var/www/html`, также и в следующей за параметром строке.

10.	Создаем файл `Dockerfile.httpd` со следующим содержимым:
dockerfile
FROM httpd:2.4
RUN apt update && apt upgrade -y
COPY ./files/httpd/httpd.conf /usr/local/apache2/conf/httpd.conf
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/7d864436-76d2-4179-877d-c462ec025e42)

11.	Создаем файл `Dockerfile.php-fpm` со следующим содержимым:
dockerfile
FROM php:7.4-fpm
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-configure pdo_mysql \
	&& docker-php-ext-install -j$(nproc) gd mysqli
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/5ee26898-4c62-4eed-8744-471629d66f67)

 
12.	Создаем файл `Dockerfile.mariadb` со следующим содержимым:
dockerfile
FROM mariadb:10.8
RUN apt-get update && apt-get upgrade -y

![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/3569a68c-0db7-4859-81ac-f7604bb4ae53)

13.  Создаем файл `docker-compose.yml` со следующим содержимым: 
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/14c730bd-cdd2-4157-b80c-c7978acf5636)

14.	 Выполним команду:
docker-compose build
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/ec10bcf8-5f36-4da3-ac26-ff8bce1dae27)

•	Сколько секунд собирался проект?_
Проект собирался 2.2 секунды

15.	Выполним команду:
docker-compose up -d
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/9a86b5b6-567a-42e7-b6db-aa5769849a0a)

16.	Откроем в браузере страницу: http://wordpress.localhost и произведем установку сайта.   
 ![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/c7cbd94a-7c46-4654-9b98-e02cbb1a5163)
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/bb6d5a78-1bb4-4144-a41e-6429cf1be51a)
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/010c8e85-f71b-436a-a96d-483ab78d2838)
![image](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/320d7bc5-329e-4775-8ac8-34446c37e676)

Ответы на вопросы:

1)	Каким образом можно скачать файл в консоли при помощи утилиты curl?
curl [ОПЦИИ] [АРГУМЕНТ]

2)	Зачем необходимо создавать для каждого сайта свою базу и своего пользователя?
Разные сайты могут администрировать разные пользователи. Также, не нужно будет менять права доступа.

3)	Как поменять доступ к системе управления БД на порт 1234?
Изменить в конфигурационном файле apache:
Listen 1234;
<VirtualHost *:1234>;

4)	Как скопировать файл из контейнера в хостовый компьютер?
docker cp container:source_path host_destination_path

5)	 За что отвечает директива `DocumentRoot` в конфигурационном файле Apache HTTP Server?
Эта директива устанавливает каталог, из которого httpd будет брать файлы.











