# Практична робота №3
## Ознайомлення зі структурою бойлерплейту, налаштування середовища та запуск проєкту.
### 1. Склонувати репозиторій [typeorm-express-typescript](https://github.com/mkosir/typeorm-express-typescript)
![Image](https://github.com/user-attachments/assets/4d34c64f-892f-4d4f-8363-7cf8df6df23a)


### 2.Змінемо порт для нашої бази даних (БД)
Для цього відкриємо файл ```docker-compose.dev.yml```
![Image](https://github.com/user-attachments/assets/81595688-3698-45cd-81b0-d8b68e6f4593)
Нас цікавить пункт там де БД.
Змінемо зовнішній порт БД з ```5432``` на ```9432```
## До
![Image](https://github.com/user-attachments/assets/eeb5feb7-3e20-48ff-bc87-b085875a2fe0)
## Після
![Image](https://github.com/user-attachments/assets/62c3ca0a-dfc5-4981-b3d0-945de4530030)

### 3. Запуск docker:dev
Перейдемо до файлу ```package.json```
![Image](https://github.com/user-attachments/assets/38d494c0-096c-4ef2-ab2c-ab6a1a08e456)
Нас тут цікавить пункт ```"docker:dev"```. Натиснемо біля нього на трикутник
аби запустити команду
![Image](https://github.com/user-attachments/assets/c77025bc-d7d2-4de8-b03d-a930855d7165)
Cтворяться контейнери.


### 4. Запуск БД
Натиснемо на кнопку "діжкою", потім натискаємо "+",перейдемо по шляху
```Date Source --> PostgreSQL```
![Image](https://github.com/user-attachments/assets/0736cc48-4ff7-4954-ac0c-8d75bc739357)
завантажемо драйвер.
Введемо дані для конекта з БД 
![Image](https://github.com/user-attachments/assets/a76a4bba-24da-4fdd-84c4-fa3886854bac)

Далі натискаємо кнопку ```Test Connection``` і тестуємо конект з БД. При тестуванні конекту виявилась помилка
![Image](https://github.com/user-attachments/assets/9b8219b3-c11e-456a-a7ea-2a80af69a24f)

Будемо виправляти.

Завдяки туторіалу від [Troubleshooting-on-typeorm-express-typescript-WINDOWS-docker-boot-up](https://github.com/OldAchoK/Troubleshooting-on-typeorm-express-typescript-WINDOWS-docker-boot-up/blob/213a973aa0891a281cbd1c6f6342700fe246f244/README.md) була розв'язана проблема.
Ось результат
![Image](https://github.com/user-attachments/assets/ae0f124d-0077-4673-adef-fc90c20e34a9)
Тепер заново конектимось до БД
При вводі порта вказуємо той що у нас в файлі ```docker-compose.div.yml```
![Image](https://github.com/user-attachments/assets/fe0eafbf-e4cc-4c06-bb39-6bc3f83527a5)
![Image](https://github.com/user-attachments/assets/260dd2d4-6190-4b39-9403-52fee9ab4770)
