# Домашнее задание к занятию "Система мониторинга Zabbix" - `Курапов Антон`


### Задание 1
Установите Zabbix Server с веб-интерфейсом.

#### Прикрепите в файл README.md скриншот авторизации в админке.
![alt text](https://github.com/AntonKurapov66/zabbix-hw/blob/main/img/1.PNG)
#### Приложите в файл README.md текст использованных команд в GitHub.
*sudo apt install postgresq  
*wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb  
*dpkg -i zabbix-release_6.4-1+ubuntu22.04_all.deb  
*sudo apt update  
*sudo apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent  
*sudo passwd postgres #изменил пароль для пользователя postgres  
*su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD'\'123456789\'';"'  
*su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'  
*zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix  
*sudo nano /etc/zabbix/zabbix_server.conf #внутри изменил DBPassword=123456789  
*sudo systemctl restart zabbix-server zabbix-agent apache2  
*sudo systemctl enable zabbix-server zabbix-agent apache2  

### Задание 2
Установите Zabbix Agent на два хоста.

#### Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
![alt text](https://github.com/AntonKurapov66/zabbix-hw/blob/main/img/2.PNG)
#### Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
![alt text](https://github.com/AntonKurapov66/zabbix-hw/blob/main/img/3.PNG)
#### Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
Выбрал одну метрику,чтобы было нагляднее видно что метрика собирается с обоих хостов.
![alt text](https://github.com/AntonKurapov66/zabbix-hw/blob/main/img/4.PNG)
#### Приложите в файл README.md текст использованных команд в GitHub
*в web zabbix server настроил два хоста :
 *51.250.79.84 - zabbix-server and zabbix-agent
 *158.160.60.103 -zabbix-agent2
