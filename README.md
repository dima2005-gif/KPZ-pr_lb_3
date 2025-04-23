# Практична робота №3
## Ознайомлення зі структурою бойлерплейту, налаштування середовища та запуск проєкту.
### 1. Склонувати репозиторій (https://github.com/mkosir/typeorm-express-typescript)
git_clone.png

### 2.Змінемо порт для нашої бази даних (БД)
Для цього відкриємо файл docker-compose.dev.yml
docker-compose_dev_yml.png
Нас цікавить пункт там де БД.
Змінемо зовнішній порт БД з 5432 на 9432
## До
before_DB.png
## Після
after_DB.png

### 3. Запуск docker:dev
Перейдемо до файлу package.json
package_json.png
Нас тут цікавить пункт "docker:dev". Натиснемо біля нього на трикутник
аби запустити команду
docker_dev.png


### 4. Запуск БД
Натиснемо на кнопку "діжкою", потім натискаємо "+",перейдемо по шляху
Date Source --> PostgreSQL
postgreesql.png
завантажемо драйвер.
Введемо дані для конекта з БД 
DB_connect.png
Далі натискаємо кнопку Test Connection і тестуємо конект з БД
При тестуванні конекту виявилась помилка
error.png
Будемо виправляти.

Завдяки туторіалу від (https://github.com/OldAchoK/Troubleshooting-on-typeorm-express-typescript-WINDOWS-docker-boot-up/blob/213a973aa0891a281cbd1c6f6342700fe246f244/README.md) була розв'язана проблема.
Ось результат
gg.png
Тепер заново конектимось до БД
При вводі порта вказуємо той що у нас в файлі docker-compose.div.yml
postgressql_connect_succeeded
database.png
