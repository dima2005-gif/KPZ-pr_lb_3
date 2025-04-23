# Величко Дмитро ІПЗ 3.02
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


# Лабораторна робота №3
## Налаштування дебагера, підключення до бази даних та використання інструментів візуалізації.
З практичної роботи №3 беремо і запускаємо наш проект. Перевіремо нашу БД. Для цього вкладці Datebase відкриємо 
БД і перейдемо по шляху ```boilerplate@localhost-->boilerplate-->public-->tables-->users```.
Тепер натиснемо на ```users``` і нам в усій красі видасть таблицю з користувачами.
![Image](https://github.com/user-attachments/assets/b3b3e449-4aeb-49b8-9d9b-e0af650cc391)
### 1. Запити 
Перед поальшою роботоую встановимо деякі залежності, а саме cross-env для коректної роботи проекту.
Виконаємо комaнду ```npm install cross-env --save-dev```
Переглянемо структуру нашого проекту і замітимо каталог ```postman``` у якому є 2 файли.
![Image](https://github.com/user-attachments/assets/8591dc5e-5fb3-401c-89eb-667067ea1123)

Тепер відкриваємо Postman. Тепер безпосередньо у нашому Postman
ми імпортуємо наші файли з директорії ```postman```.

![Image](https://github.com/user-attachments/assets/c43453c9-0bf7-43be-a4a7-c75736ddd495)

Після імпорту з'явилась колекція ```RESTful API Boilerplate```

![Image](https://github.com/user-attachments/assets/eca645c2-6118-4272-8769-56cdac3e608d)

Тепер зробимо ```GET``` запит для усіх юзерів.
![Image](https://github.com/user-attachments/assets/186b1127-478a-4767-a1ec-baae9385dabb)
Як бачимо у нас помилка.

Перейдемо у ```Environments``` і натиснемо на кнопку ```Set active```.
Тепер заново запускаємо ```GET``` запит для всіх юзерів.
![Image](https://github.com/user-attachments/assets/9c76ee0c-8c79-4719-8a09-1459ab2bc164)
Ця помилка каже нам, що сервак працює, і він розуміє наш запит.

Розбиремось зі системою роутів.

У WebStorm знаходемо каталог ```src```, а у ньому каталог routes. 

![Image](https://github.com/user-attachments/assets/1e1be4fb-3161-4507-8fda-71755aada81d)

Відриємо файл ```index.ts``` і побачимо що, наш роутер використовує ```/v1``` для конекта.
Тоді перейдемо у наш Postman і у вкладці ```Environments``` і у колонці ```Current value``` додамо наш роутер ```/v1```
![Image](https://github.com/user-attachments/assets/dbcdbf56-b8b3-469e-89f0-ecf09275067b)

Тепер знову заходимо у колекції у папку ```/users``` і надаємо ```GET``` запит 
![Image](https://github.com/user-attachments/assets/1fb217fc-1f84-4f1f-81a0-64eee3870bdc)
Так знову помилка. Тут проблема з токеном.

Тепер відправимо запит. Перейдемо у файл ```/auth``` у ```/login``` надамо запит.
![Image](https://github.com/user-attachments/assets/ee62ae63-5ad5-4c27-97ac-97c5d6575196)

Так тепер у цьому же файлі у рядку написати ```/auth/login```. І знову надмо наш запит.
![Image](https://github.com/user-attachments/assets/8acd006e-c945-4cfc-b501-bd2494603dc0)
Так запит відбувся і у нас токен змінився.

Тепер у паці ```/users``` надамо запит.
![Image](https://github.com/user-attachments/assets/05a1c8a5-ca97-4e5c-83af-37cc04dddf5f)
І Еврика! Наш запит працює. Тепер сервер наш налаштований. Перейдемо до зв'язку з БД.

### 2. Дебагинг
Перейдемо у нашу IDE і заходимо у файл ```.env```. Тут ми закоментуємо деякі рядки.

![Image](https://github.com/user-attachments/assets/9d8352ce-a5dd-4dc7-8d45-7ee6e6fc3e84)

Так тепер перейдемо у файл ```package.json``` і задебажимо ```dev```.

![Image](https://github.com/user-attachments/assets/2815c56e-bcc9-4489-ae43-092131f55c72)

Усе БД законектився.

# Висновок
У ході роботи було засвоєно налаштовано наш проект, а саме бекенд частину. А саме було налаштовано:
- Розгорнули проект
- Налаштували і створили контейнери
- Налаштували і підключили БД у контейнері
- Налаштування сервера у Postman
- Підключення БД до сервера

Це дало змогу створити повноцінне серверне середовище для подальшої розробки й тестування функціоналу. Отримані знання й практичні навички можна застосовувати під час майбутніх проєктів, що потребують використання контейнеризації, баз даних і REST API.
