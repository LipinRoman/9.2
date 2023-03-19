# Домашнее задание к занятию 9.2 «Система мониторинга Zabbix» - Липин Роман

Задание 1

Установите Zabbix Server с веб-интерфейсом.
Процесс выполнения

    Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
    Установите PostgreSQL. Для установки достаточна та версия что есть в системном репозитороии Debian 11
    Пользуясь конфигуратором комманд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache
    Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server

Требования к результаты

    Прикрепите в файл README.md скриншот авторизации в админке
    Приложите в файл README.md текст использованных команд в GitHub

![11.png](https://github.com/LipinRoman/9.2/blob/master/img/11.png)

wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb
sudo apt install /home/user/zabbix-release_6.4-1+ubuntu22.04_all.deb
sudo apt update
sudo apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-nginx-conf zabbix-sql-scripts zabbix-agent postgresql
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix 
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
sudo nano /etc/zabbix/zabbix_server.conf  
sudo nano /etc/zabbix/nginx.conf 
sudo systemctl restart zabbix-server zabbix-agent nginx php8.1-fpm
sudo systemctl enable zabbix-server zabbix-agent nginx php8.1-fpm 

Задание 2

Установите Zabbix Agent на два хоста.
Процесс выполнения

    Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
    Установите Zabbix Agent на 2 виртмашины, одной из них может быть ваш Zabbix Server
    Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов
    Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera
    Проверьте что в разделе Latest Data начали появляться данные с добавленных агентов

Требования к результаты

    Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
    Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
    Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
    Приложите в файл README.md текст использованных команд в GitHub

![21.png](https://github.com/LipinRoman/9.2/blob/master/img/21.png)
![22.png](https://github.com/LipinRoman/9.2/blob/master/img/22.png)
![23.png](https://github.com/LipinRoman/9.2/blob/master/img/23.png)

wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb
sudo apt install /home/user/-i zabbix-release_6.4-1+ubuntu22.04_all.deb
sudo apt update
sudo apt install zabbix-agent2 zabbix-agent2-plugin-*
sudo nano /etc/zabbix/zabbix_agent2.conf
sudo systemctl restart zabbix-agent2.service
sudo systemctl enable zabbix-agent2.service

Задание 3 со звёздочкой*

Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.
Требования к результаты

    Приложите в файл README.md скриншот раздела Latest Data, где видно свободное место на диске C:


