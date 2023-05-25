# ASWEB_lab3

Введение

Теоретическая часть

Протокол HTTP предполагает возможность передачи в составе запроса URL (единого указателя ресурса) — это позволяет сервису понять, к какому именно сайту обращается браузер или иная клиентская программа. Нужно  только привязать доменное имя к нужному IP-адресу и прописать в конфигурации корневой каталог для виртуального хоста. 
Чтобы веб-приложения на стороне сервера (различные скрипты или даже системы управления контентом — CMS) запускались с правами того или иного пользователя хостинга, в Apache был создан специальный механизм suexec. Сервер баз данных (обычно MySQL) для виртуальных хостов  общий, но доступ есть только к личным базам. 
Виртуальный хостинг (англ. shared hosting) — вид хостинга, при котором множество веб-сайтов расположено на одном веб-сервере. Это самый экономичный вид хостинга, подходящий для небольших проектов.
Для хостинга на виртуальном выделенном сервере (VPS) провайдер выделяет  целую операционную систему. Это аналог обычного железного сервера, только расположен он у провайдера в облаке.
Каждый сервер —отдельный контейнер, для каждого зарезервированы ресурсы, их не нужно ни с кем делить.
Постановка задачи
Целью данной работы является обучение добавлению и настройке сайтов (виртуальных хостов). А также, ознакомление с запуском сайтов (виртуальных хостов) в контейнере

Практическая часть

1. Создаем виртуальную машину Ubuntu
![1111](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/62726f16-53f4-47f9-b6a4-c647fb371387)
2.  Подключаем скаченный файл Ubuntu к виртуальной машине
![2](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/174cae2e-8d20-4e21-b35a-fa4b33caccb1)
![3](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/57644ead-226e-46c3-9bda-04b28f7eb4ed)
3. Настраиваем и устанавливаем Ubuntu 
![4](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/c0a4695a-db0f-4abd-830a-410a39f7ba9c)
![4 png](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/7dbbe55a-4141-49b7-8414-c0db221062a7)
![5](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/6d0cfb35-cea5-4690-a79e-167deaa7507e)
![5](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/ca2d78e0-c081-4534-9ad0-810325a332bc)
![6](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/182ce7a1-d543-4c05-9db1-83808675acd8)
![7](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/4ca55d4f-e04d-492e-8e11-7f58cb303ab0)
4. Устанавливаем логин и пароль
![8](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/ecc81e53-1e78-46c2-bdbc-f828ea107b69)
![9](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/077ca488-233c-4209-8117-6e11a8b60e6d)
![10](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/c5d90ed2-5255-42e5-a966-5bb740239e22)
5. Скачиваем PuTTY и вводим ip адрес виртуальной машины, полученной из предыдущей команды
![11](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/1336072a-0b9f-4dc7-a805-9a4de86fe5e4)
6. Подключаемся по ssh к созданной виртуальной машине и продолжаем настройку виртуального веб сервера
![12](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/123c377c-6da8-4a55-9216-afd6da49efc3)
![12 1](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/548a4a83-6346-4499-b98f-5d1358ff1205)
7.  Просмотр директорий
![13 1](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/71629d82-779c-49a9-8243-27e142110251)
![13 2](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/c7b708d3-f1a8-42b6-b89f-5add5ee9064f)
![13 3](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/397ddf98-97f4-4a1b-a733-3012ba50e9d6)
![13 5](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/7916ec7a-c562-4de1-9dee-1967edd80e66)
8.  Скачиваем apache в командной строке 
![14](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/63af22be-875d-4bf9-9526-091315ce83db)
![15](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/1b9e657d-53c9-4b11-aedc-a6c5d9eb6515)
9.  Открываем и редактируем файл hosts
![16](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/af7c6ffa-efef-4d12-b6b3-e8a259bfee6b)
10. Сопоставляем имя хоста и адрес виртуальной машины
![17](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/4efe5873-2f80-4949-a32b-a7b0b3b13ba4)
![18](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/d4c6b9c4-5f07-495d-a35c-d8d9eadd5a74)
![19](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/a7cdbd3c-d2f2-419b-b221-3e9afd07e589)
11. Создаем папку сервера
![20](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/9e1da241-c20b-4890-bf5b-b0cf21b89200)
![21](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/6f67f94d-9d5c-4df5-85c3-d510b56d7e97)
12. Даем права на чтение и запуск на выполнение, но редактировать может только владелец
![22](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/97359cc8-14ee-40b9-8bb8-ffbc6a467035)
13. Даем  права, как владельцу сервера
![23](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/452ac0ee-7f18-452a-be7b-b8b3cde58dce)
![24](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/26802abb-93e0-4a95-a7a2-452e519d859c)
![25](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/6af252ce-e216-45cb-986b-2fcd9091849c)

14. Копируем и редактируем конфигурационный файл
![26](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/73e8357b-90e3-4113-948f-034f12ddb7fd)
![27](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/189794e6-fec0-43cc-a00c-fec8a33da71c)
15. Включаем виртуальных хост и обновляем apache
![28](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/d6a72c06-764f-4d13-ba74-3e361b4144e2)
![29](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/5f6a41ee-db69-4931-98bd-35e7c779fa42)

16. Устанавливаем php из командной строки 
![30](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/20cd9e16-5136-4b47-9127-504599c135be)
17. Устанавливаем mariadb из командной строки
![31](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/f875bc63-0e29-4772-8b04-da4dfd8a36d8)

18. Запускаем установку базы данных

![32](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/2c0e10f2-c427-4df5-a02c-f7cde867ea51)
![33](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/d8cd0a42-68f7-4c8c-8430-cc86e6e83d18)
![34](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/2a24611b-51f5-4b6c-8140-b93431909196)
![35](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/2e1b8e28-ec19-4131-a32a-31a6a2cb583f)
![36](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/940b9d39-fe5b-4f9f-8364-d3bd28a2102f)
![37](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/fe51c6e2-b970-43ec-ac24-1bde94c2f38d)

19. Устанавливаем php my admin из командной строки
![38](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/67bdbb8e-b792-4e9e-9bd2-3afee49e3108)
![39](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/dea032af-8a68-42e2-bbe3-c198f284b24c)
20. Устанавливаем wordpress из командной строки
![40](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/ac923fe1-cd35-4e75-8d46-90c519b702cf)
21. Разархивируем пакет

![41](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/2e7e375c-3eca-4dad-b257-994f5c86cd21)
![42](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/8bc0252c-3ee9-4da7-90e3-2607c4179f5d)
![43](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/f144dc04-5cca-46f8-94b8-14cc4e0d2d05)
22. Создаем базу данных
![44](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/120befb9-9808-4d00-94e3-c91b1610def2)
![45](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/72db3e79-7e68-4f8c-b884-e046ec61263b)
![46](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/ba933286-10f7-486b-b17c-49a0a7163b7c)
![47](https://github.com/KaterinaSpinu/ASWEB_lab3/assets/126262145/8fe11396-97bd-4215-97de-63106b988259)
 22. Создаем файл и копируем предложенный текст. Далее запускаем установку.

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

Вывод

Виртуальный хостинг не требует администрирования обеспечивающего работу сайта окружения. Клиенту не придется самому устанавливать, настраивать и обновлять системное и прикладное ПО, а в ряде случаев панель управления хостингом позволяет устанавливать и CMS.









