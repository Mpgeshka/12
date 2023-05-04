# Выполнение первой части задания

Для начала подключимся к удаленной машине:
```powershell
Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.19.0-41-generic x86_64)
* Documentation:  https://help.ubuntu.com
* Management:     https://landscape.canonical.com
* Support:        https://ubuntu.com/advantage

Last login: Thu May  4 19:36:50 2023
```
1. Используйте команды операционной системы Linux и создайте две новых директории – «Игрушки для школьников» и «Игрушки для дошколят» 
```powershell
madmin@madmin-VirtualBox:~$ mkdir Игрушки_для_школьников

madmin@madmin-VirtualBox:~$ mkdir Игрушки_для_дошколят
```
2. Создайте в директории «Игрушки для школьников» текстовые файлы - «Роботы», «Конструктор», «Настольные игры»
```powershell
madmin@madmin-VirtualBox:~$ cd Игрушки_для_школьников
madmin@madmin-VirtualBox:~/Игрушки_для_школьников$ touch Роботы.txt
madmin@madmin-VirtualBox:~/Игрушки_для_школьников$ touch Конструктор.txt
madmin@madmin-VirtualBox:~/Игрушки_для_школьников$ touch Настольные_игры.txt
```
3. Создайте в директории «Игрушки для дошколят» текстовые файлы «Мягкие игрушки», «Куклы», «Машинки»
```powershell
madmin@madmin-VirtualBox:~/Игрушки_для_школьников$ cd
madmin@madmin-VirtualBox:~$ cd Игрушки_для_дошколят
madmin@madmin-VirtualBox:~/Игрушки_для_дошколят$ touch Мягкие_игрушки.txt
madmin@madmin-VirtualBox:~/Игрушки_для_дошколят$ touch Куклы.txt
madmin@madmin-VirtualBox:~/Игрушки_для_дошколят$ touch Машинки.txt
madmin@madmin-VirtualBox:~/Игрушки_для_дошколят$ cd
```
4. Объединить 2 директории в одну «Имя Игрушки»
```powershell
madmin@madmin-VirtualBox:~$ sudo snap install tree
[sudo] password for madmin: 
tree 1.8.0+pkg-3fd6 from 林博仁(Buo-ren, Lin) (brlin) installed
madmin@madmin-VirtualBox:~$ mkdir Имя_игрушки
madmin@madmin-VirtualBox:~$ mv Игрушки_для_школьников/ Игрушки_для_дошколят/ Имя_игрушки/
madmin@madmin-VirtualBox:~$ cd Имя_игрушки
madmin@madmin-VirtualBox:~/Имя_игрушки$ tree

.
├── Игрушки_для_дошколят
│   ├── Куклы.txt
│   ├── Машинки.txt
│   └── Мягкие_игрушки.txt
└── Игрушки_для_школьников
    ├── Конструктор.txt
    ├── Настольные_игры.txt
    └── Роботы.txt

2 directories, 6 files
madmin@madmin-VirtualBox:~/Имя_игрушки$ cd
```
5. Переименовать директорию «Имя Игрушки» в «Игрушки»
```powershell
madmin@madmin-VirtualBox:~$ mv Имя_игрушки/ Игрушки
madmin@madmin-VirtualBox:~$ ls
Desktop    Downloads  Pictures  snap       Videos
Documents  Music      Public    Templates  Игрушки
```
6. Просмотреть содержимое каталога «Игрушки».
```powershell
madmin@madmin-VirtualBox:~$ cd Игрушки
madmin@madmin-VirtualBox:~/Игрушки$ tree
.
├── Игрушки_для_дошколят
│   ├── Куклы.txt
│   ├── Машинки.txt
│   └── Мягкие_игрушки.txt
└── Игрушки_для_школьников
    ├── Конструктор.txt
    ├── Настольные_игры.txt
    └── Роботы.txt

2 directories, 6 files
```
Еще один вариант:
```powershell
madmin@madmin-VirtualBox:~/Игрушки$ ls -la
total 16
drwxrwxr-x  4 madmin madmin 4096 мая  4 22:06 .
drwxr-x--- 17 madmin madmin 4096 мая  4 22:30 ..
drwxrwxr-x  2 madmin madmin 4096 мая  4 21:34 Игрушки_для_дошколят
drwxrwxr-x  2 madmin madmin 4096 мая  4 21:33 Игрушки_для_школьников
madmin@madmin-VirtualBox:~/Игрушки$ cd
```
7. Установить и удалить snap-пакет. Установка была произведена в пункте 4.
```powershell
madmin@madmin-VirtualBox:~$ sudo snap remove tree
[sudo] password for madmin: 
tree removed
```
8. Добавить произвольную задачу для выполнения каждые 3 минуты
```powershell
madmin@madmin-VirtualBox:~$ crontab -e

# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
*/3 * * * * echo 'А у нас новая модель машины' >> /home/madmin/Игрушки/Игрушки_для_дошколят/Машинки.txt

^G Help        ^O Write Out   ^W Where Is    ^K Cut         ^T Execute     ^C Location
^X Exit        ^R Read File   ^\ Replace     ^U Paste       ^J Justify     ^/ Go To Line

crontab: installing new crontab
```