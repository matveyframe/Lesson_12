1) Написать скрипт, который запрашивает имя пользователя и выводит персонализированное приветствие
```
#!bin/bash

read -p  "Введите имя пользователя: " name

echo "Приятно познакомиться "$name"!"
```
![](https://github.com/matveyframe/Lesson_12/blob/main/Whoami.sh%20result.PNG "Logo Title Text 1")

2) Установить nginx (sudo apt install -y nginx) и написать скрипт для мониторинга состояния демона nginx (systemctl status) с и автоматическим перезапуском (systemctl restart), если он не запущен
```
#!/bin/bash

Proc=nginx.service
status="Active: active (running)"

if systemctl status $Proc |grep -q "$status"; then
        echo "Nginx is active"
else
        systemctl restart nginx
        echo "Nginx rebooting"
        systemctl status nginx | grep active
        exit 0
fi
```
![](https://github.com/matveyframe/Lesson_12/blob/main/monitoring_nginx.sh%20result.PNG "Logo Title Text 1")

3) Написать скрипт для мониторинга доступности хоста (можно использовать ping) с записью результата в лог с датой и временем (формат произвольный).
```
LOG_DIR="/home/matvey/home_works/lesson_12"
DATE=$(date "+%Y-%m-%dT%H:%M:%S")
LOG_PING=${LOG_DIR}/${DATE}

mkdir -p $LOG_PING  > dev/null 2>&1
ping ya.ru -c 4 > ${LOG_PING}/ping.log 2>&1
```

![](https://github.com/matveyframe/Lesson_12/blob/main/Ping_Host.sh%20result.PNG "Logo Title Text 1")
