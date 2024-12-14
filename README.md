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

   
