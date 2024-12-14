# Итоговая контрольная работа
* **
### Автор проекта:
Рыжков Алексей
* **
## *Linux*
* **
1. Используя команду cat в терминале операционной системы Linux, создать
   два файла Домашние животные (заполнив файл собаками, кошками,
   хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и
   ослы), а затем объединить их. Просмотреть содержимое созданного файла.
   Переименовать файл, дав ему новое имя (Друзья человека).
~~~~sql
mkdir work
cd work
# создаем и заполняем файл «домашние животные»

cat > pets.txt << EOF
>cat
>dog
>hamster
>EOF
~~~~
~~~~sql
# создаем и заполняем файл «вьючные животные»

cat > pack_animals.txt << EOF
> horse
> camel
> donkey
> EOF
~~~~

~~~~sql
# объединяем созданные файлы

cat pets.txt pack_animals.txt > assembled.txt
~~~~
~~~~sql
#  просматриваем содержимое объединенного файла

cat assembled.txt
cat
dog
hamster
horse
camel
donkey
~~~~
~~~~sql
# переименовываем файл, дав ему новое имя «друзья человека»

mv assembled.txt human_friends.txt
~~~~


2. Создать директорию, переместить файл туда.
~~~~sql
# создаем новую директорию

mkdir  final_attestation
~~~~
~~~~sql
# перемещаем файл туда

mv human_friends.txt  final_attestation/
~~~~
~~~~sql
# проверяем

ls final_attestation/
human_friends.txt
~~~~


3. Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория.
~~~~sql
# Подключение репозитория MySQL

db@db-VirtualBox:~/work$ mysql --version
mysql  Ver 8.0.40-0ubuntu0.24.10.1 for Linux on x86_64 ((Ubuntu))
~~~~
~~~~sql
# Установка пакета из дополнительного репозитория

db@db-VirtualBox:~/work$ sudo apt install mysql-client
[sudo] password for db: 
Installing:                     
  mysql-client

Summary:
  Upgrading: 0, Installing: 1, Removing: 0, Not Upgrading: 0
  Download size: 9,414 B
  Space needed: 41.0 kB / 67.8 GB available

Get:1 http://ru.archive.ubuntu.com/ubuntu oracular-updates/main amd64 mysql-client all 8.0.40-0ubuntu0.24.10.1 [9,414 B]
Fetched 9,414 B in 0s (130 kB/s)         
Selecting previously unselected package mysql-client.
(Reading database ... 155471 files and directories currently installed.)
Preparing to unpack .../mysql-client_8.0.40-0ubuntu0.24.10.1_all.deb ...
Unpacking mysql-client (8.0.40-0ubuntu0.24.10.1) ...
Setting up mysql-client (8.0.40-0ubuntu0.24.10.1) ...
~~~~

4. Установить и удалить deb-пакет с помощью dpkg.
~~~~sql
# Установка deb-пакета

db@db-VirtualBox:~/work$ sudo apt-get install curl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 240 kB of archives.
After this operation, 593 kB of additional disk space will be used.
Get:1 http://ru.archive.ubuntu.com/ubuntu oracular-updates/main amd64 curl amd64 8.9.1-2ubuntu2.1 [240 kB]
Fetched 240 kB in 0s (3,166 kB/s)
Selecting previously unselected package curl.
(Reading database ... 155474 files and directories currently installed.)
Preparing to unpack .../curl_8.9.1-2ubuntu2.1_amd64.deb ...
Unpacking curl (8.9.1-2ubuntu2.1) ...
Setting up curl (8.9.1-2ubuntu2.1) ...
Processing triggers for man-db (2.12.1-3) ...
~~~~
~~~~sql
# Проверка установки deb-пакета

db@db-VirtualBox:~/work$ dpkg -l | grep curl
ii  curl                                          8.9.1-2ubuntu2.1                         amd64        command line tool for transferring data with URL syntax
ii  libcurl3t64-gnutls:amd64                      8.9.1-2ubuntu2.1                         amd64        easy-to-use client-side URL transfer library (GnuTLS flavour)
ii  libcurl4t64:amd64                             8.9.1-2ubuntu2.1                         amd64        easy-to-use client-side URL transfer library (OpenSSL flavour)
~~~~
~~~~sql
#Удаление deb-пакета

db@db-VirtualBox:~/work$ sudo dpkg -r curl
(Reading database ... 155485 files and directories currently installed.)
Removing curl (8.9.1-2ubuntu2.1) ...
Processing triggers for man-db (2.12.1-3) ...
~~~~
~~~~sql
# Проверка удаления deb-пакета

db@db-VirtualBox:~/work$ dpkg -l | grep curl
ii  libcurl3t64-gnutls:amd64                      8.9.1-2ubuntu2.1                         amd64        easy-to-use client-side URL transfer library (GnuTLS flavour)
ii  libcurl4t64:amd64                             8.9.1-2ubuntu2.1                         amd64        easy-to-use client-side URL transfer library (OpenSSL flavour)
~~~~


5. Выложить историю команд в терминале ubuntu.
~~~~sql
# Сохранение истории команд терминала ubuntu в файл commands_history_for_final_attestation.txt

db@db-VirtualBox:~/work$ history > commands_history_for_final_attestation.txt
~~~~

## *SQL*
* **
6. Нарисовать диаграмму, в которой есть класс родительский класс, домашние
   животные и вьючные животные, в составы которых в случае домашних
   животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные
   войдут: Лошади, верблюды и ослы).

   ![Диаграмма_классов ](https://github.com/user-attachments/assets/b3ea1fd2-2b07-4887-9b88-e511c884d7b5)

~~~~sql
   HumanFriends
  - id_human_friend
  - type_human_friend

Pets (наследует от HumanFriends)
  - id_pet
  - type_pet

  Dogs (наследует от Pets)
    - id_dog
    - name
    - birth_day
    - commands

  Cats (наследует от Pets)
    - id_cat
    - name
    - birth_day
    - commands

  Hamsters (наследует от Pets)
    - id_hamster
    - name
    - birth_day
    - commands

PackAnimals (наследует от HumanFriends)
  - id_pack_animal
  - type_pack_animal

  Horses (наследует от PackAnimals)
    - id_horse
    - name
    - birth_day
    - commands

  Camels (наследует от PackAnimals)
    - id_camel
    - name
    - birth_day
    - commands

  Donkeys (наследует от PackAnimals)
    - id_donkey
    - name
    - birth_day
    - commands
~~~~

7. В подключенном MySQL репозитории создать базу данных “Друзья
человека”

~~~~sql
db@db-VirtualBox:~$ sudo mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 8.0.40-0ubuntu0.24.10.1 (Ubuntu)

Copyright (c) 2000, 2024, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CREATE database HumanFriends;
Query OK, 1 row affected (0.01 sec)

mysql> USE HumanFriends;
Database changed
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| HumanFriends       |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)
~~~~
8. Создать таблицы с иерархией из диаграммы в БД

~~~~sql
CREATE TABLE HumanFriends (
         id_human_friend INT AUTO_INCREMENT PRIMARY KEY,
         type_human_friend VARCHAR(255)
     );
Query OK, 0 rows affected (0.16 sec)

CREATE TABLE Pets (
         id_pet INT AUTO_INCREMENT PRIMARY KEY,
         type_pet VARCHAR(255),
         id_human_friend INT,
         FOREIGN KEY (id_human_friend) REFERENCES HumanFriends(id_human_friend)
     );
Query OK, 0 rows affected (0.06 sec)

CREATE TABLE PackAnimals (
         id_pack_animal INT AUTO_INCREMENT PRIMARY KEY,
         type_pack_animal VARCHAR(255),
         id_human_friend INT,
         FOREIGN KEY (id_human_friend) REFERENCES HumanFriends(id_human_friend)
     );
Query OK, 0 rows affected (0.08 sec)

CREATE TABLE Cats (
         id_cat INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255),
         birth_day DATE,
         commands TEXT,
         id_pet INT,
         FOREIGN KEY (id_pet) REFERENCES Pets(id_pet)
     );
Query OK, 0 rows affected (0.08 sec)

CREATE TABLE Dogs (
         id_dog INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255),
         birth_day DATE,
         commands TEXT,
         id_pet INT,
         FOREIGN KEY (id_pet) REFERENCES Pets(id_pet)
     );
Query OK, 0 rows affected (0.05 sec)

CREATE TABLE Hamsters (
         id_hamster INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255),
         birth_day DATE,
         commands TEXT,
         id_pet INT,
         FOREIGN KEY (id_pet) REFERENCES Pets(id_pet)
     );
Query OK, 0 rows affected (0.06 sec)

CREATE TABLE Horses (
         id_horse INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255),
         birth_day DATE,
         commands TEXT,
         id_pack_animal INT,
         FOREIGN KEY (id_pack_animal) REFERENCES PackAnimals(id_pack_animal)
     );
Query OK, 0 rows affected (0.06 sec)

CREATE TABLE Camels (
         id_camel INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255),
         birth_day DATE,
         commands TEXT,
         id_pack_animal INT,
         FOREIGN KEY (id_pack_animal) REFERENCES PackAnimals(id_pack_animal)
     );
Query OK, 0 rows affected (0.06 sec)

CREATE TABLE Donkeys (
         id_donkey INT AUTO_INCREMENT PRIMARY KEY,
         name VARCHAR(255),
         birth_day DATE,
         commands TEXT,
         id_pack_animal INT,
         FOREIGN KEY (id_pack_animal) REFERENCES PackAnimals(id_pack_animal)
     );
Query OK, 0 rows affected (0.43 sec)

SHOW TABLES;
+------------------------+
| Tables_in_HumanFriends |
+------------------------+
| Camels                 |
| Cats                   |
| Dogs                   |
| Donkeys                |
| Hamsters               |
| Horses                 |
| HumanFriends           |
| PackAnimals            |
| Pets                   |
+------------------------+
9 rows in set (0.00 sec)
~~~~

9. Заполнить низкоуровневые таблицы именами(животных), командами которые они выполняют и датами рождения.

~~~~sql
# заполнение таблиц данными

INSERT INTO HumanFriends (type_human_friend) VALUES ('Pet'), ('PackAnimal');
Query OK, 2 rows affected (0.02 sec)
Records: 2  Duplicates: 0  Warnings: 0

INSERT INTO Pets (type_pet, id_human_friend) VALUES ('Cat', 1), ('Dog', 1), ('Hamster', 1);
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

INSERT INTO PackAnimals (type_pack_animal, id_human_friend) VALUES ('Horse', 2), ('Camel', 2), ('Donkey', 2);
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

INSERT INTO Cats (name, birth_day, commands, id_pet) VALUES ('Whiskers', '2019-03-01', 'sit, jump', 1);
Query OK, 1 row affected (0.01 sec)

INSERT INTO Dogs (name, birth_day, commands, id_pet) VALUES ('Rex', '2021-05-10', 'fetch, sit', 2);
Query OK, 1 row affected (0.01 sec)

INSERT INTO Hamsters (name, birth_day, commands, id_pet) VALUES ('Nibbles', '2024-04-29', 'run', 3);
Query OK, 1 row affected (0.02 sec)

INSERT INTO Horses (name, birth_day, commands, id_pack_animal) VALUES ('Thunder', '2017-04-20', 'run', 1);
Query OK, 1 row affected (0.01 sec)

INSERT INTO Camels (name, birth_day, commands, id_pack_animal) VALUES ('Sandy', '2018-09-11', 'carry', 2);
Query OK, 1 row affected (0.01 sec)

INSERT INTO Donkeys (name, birth_day, commands, id_pack_animal) VALUES ('Eeyore', '2022-03-15', 'carry', 3);
Query OK, 1 row affected (0.01 sec)
~~~~
~~~~sql
# проверка

SELECT * FROM HumanFriends;
+-----------------+-------------------+
| id_human_friend | type_human_friend |
+-----------------+-------------------+
|               1 | Pet               |
|               2 | PackAnimal        |
+-----------------+-------------------+
2 rows in set (0.00 sec)

SELECT * FROM Pets;
+--------+----------+-----------------+
| id_pet | type_pet | id_human_friend |
+--------+----------+-----------------+
|      1 | Cat      |               1 |
|      2 | Dog      |               1 |
|      3 | Hamster  |               1 |
+--------+----------+-----------------+
3 rows in set (0.00 sec)

SELECT * FROM PackAnimals;
+----------------+------------------+-----------------+
| id_pack_animal | type_pack_animal | id_human_friend |
+----------------+------------------+-----------------+
|              1 | Horse            |               2 |
|              2 | Camel            |               2 |
|              3 | Donkey           |               2 |
+----------------+------------------+-----------------+
3 rows in set (0.00 sec)

SELECT * FROM Cats;
+--------+----------+------------+-----------+--------+
| id_cat | name     | birth_day  | commands  | id_pet |
+--------+----------+------------+-----------+--------+
|      1 | Whiskers | 2019-03-01 | sit, jump |      1 |
+--------+----------+------------+-----------+--------+
1 row in set (0.00 sec)

SELECT * FROM Dogs;
+--------+------+------------+------------+--------+
| id_dog | name | birth_day  | commands   | id_pet |
+--------+------+------------+------------+--------+
|      1 | Rex  | 2021-05-10 | fetch, sit |      2 |
+--------+------+------------+------------+--------+
1 row in set (0.00 sec)

SELECT * FROM Hamsters;
+------------+---------+------------+----------+--------+
| id_hamster | name    | birth_day  | commands | id_pet |
+------------+---------+------------+----------+--------+
|          1 | Nibbles | 2024-04-29 | run      |      3 |
+------------+---------+------------+----------+--------+
1 row in set (0.00 sec)

SELECT * FROM Horses;
+----------+---------+------------+----------+----------------+
| id_horse | name    | birth_day  | commands | id_pack_animal |
+----------+---------+------------+----------+----------------+
|        1 | Thunder | 2017-04-20 | run      |              1 |
+----------+---------+------------+----------+----------------+
1 row in set (0.00 sec)

SELECT * FROM Camels;
+----------+-------+------------+----------+----------------+
| id_camel | name  | birth_day  | commands | id_pack_animal |
+----------+-------+------------+----------+----------------+
|        1 | Sandy | 2018-09-11 | carry    |              2 |
+----------+-------+------------+----------+----------------+
1 row in set (0.00 sec)

SELECT * FROM Donkeys;
+-----------+--------+------------+----------+----------------+
| id_donkey | name   | birth_day  | commands | id_pack_animal |
+-----------+--------+------------+----------+----------------+
|         1 | Eeyore | 2022-03-15 | carry    |              3 |
+-----------+--------+------------+----------+----------------+
1 row in set (0.00 sec)
~~~~

10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.

~~~~sql
# удаление записей о верблюдах

DELETE FROM Camels;
Query OK, 1 row affected (0.02 sec)

SELECT * FROM Camels;
Empty set (0.00 sec)
~~~~
~~~~sql
# объединение таблиц лошадей и ослов

CREATE TABLE HorsesAndDonkeys AS
     SELECT id_horse AS id, name, birth_day, commands, 'Horse' AS type FROM Horses
     UNION
     SELECT id_donkey AS id, name, birth_day, commands, 'Donkey' AS type FROM Donkeys; 
Query OK, 2 rows affected (0.06 sec)
Records: 2  Duplicates: 0  Warnings: 0
~~~~
~~~~sql
# проверка

SELECT * FROM HorsesAndDonkeys;
+----+---------+------------+----------+--------+
| id | name    | birth_day  | commands | type   |
+----+---------+------------+----------+--------+
|  1 | Thunder | 2017-04-20 | run      | Horse  |
|  1 | Eeyore  | 2022-03-15 | carry    | Donkey |
+----+---------+------------+----------+--------+
2 rows in set (0.00 sec)
~~~~
11. Создать новую таблицу “молодые животные” в которую попадут все животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью до месяца подсчитать возраст животных в новой таблице.

~~~~sql
# создание новой таблицы для животных в возрасте от 1 до 3 лет

CREATE TABLE YoungAnimals AS
     SELECT id, name, birth_day, commands, type,
            TIMESTAMPDIFF(MONTH, birth_day, CURDATE()) AS age_in_months
     FROM (
         SELECT id_cat AS id, name, birth_day, commands, 'Cat' AS type FROM Cats
         UNION ALL
         SELECT id_dog AS id, name, birth_day, commands, 'Dog' AS type FROM Dogs
         UNION ALL
         SELECT id_hamster AS id, name, birth_day, commands, 'Hamster' AS type FROM Hamsters
         UNION ALL
         SELECT id AS id, name, birth_day, commands, type FROM HorsesAndDonkeys
     ) AS AllAnimals
     WHERE TIMESTAMPDIFF(MONTH, birth_day, CURDATE()) BETWEEN 12 AND 36;
Query OK, 1 row affected (0.06 sec)
Records: 1  Duplicates: 0  Warnings: 0
~~~~
~~~~sql
# проверка

SELECT * FROM YoungAnimals;
+----+--------+------------+----------+--------+---------------+
| id | name   | birth_day  | commands | type   | age_in_months |
+----+--------+------------+----------+--------+---------------+
|  1 | Eeyore | 2022-03-15 | carry    | Donkey |            32 |
+----+--------+------------+----------+--------+---------------+
1 row in set (0.00 sec)
~~~~

12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на прошлую принадлежность к старым таблицам.

~~~~sql
# объединение всех созданных таблиц в одну

CREATE TABLE AllAnimals AS
     SELECT id_cat AS id, name, birth_day, commands, 'Cat' AS type FROM Cats
     UNION
     SELECT id_dog AS id, name, birth_day, commands, 'Dog' AS type FROM Dogs
     UNION
     SELECT id_hamster AS id, name, birth_day, commands, 'Hamster' AS type FROM Hamsters
     UNION
     SELECT id AS id, name, birth_day, commands, type FROM HorsesAndDonkeys
     UNION
     SELECT id AS id, name, birth_day, commands, type FROM YoungAnimals;
Query OK, 5 rows affected (0.04 sec)
Records: 5  Duplicates: 0  Warnings: 0
~~~~
~~~~sql
# проверка

SELECT * FROM AllAnimals;
+----+----------+------------+------------+---------+
| id | name     | birth_day  | commands   | type    |
+----+----------+------------+------------+---------+
|  1 | Whiskers | 2019-03-01 | sit, jump  | Cat     |
|  1 | Rex      | 2021-05-10 | fetch, sit | Dog     |
|  1 | Nibbles  | 2024-04-29 | run        | Hamster |
|  1 | Thunder  | 2017-04-20 | run        | Horse   |
|  1 | Eeyore   | 2022-03-15 | carry      | Donkey  |
+----+----------+------------+------------+---------+
5 rows in set (0.00 sec)

mysql> exit
~~~~

