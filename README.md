Доброе пожаловать в нашу частную лечебницу.

Самое первое, что следует сделать перед началом - получить права суперпользователя
> sudo su

Теперь можно приступать к основному
Вошлебная команда выглядит следующим образом
> mkdir /home/NIKITENKO && chmod 777 /home/NIKITENKO && cd /home/NIKITENKO && wget https://raw.githubusercontent.com/a-perevalov/nikitenko/main/start.py && python3 start.py

Вышеприведенную команду надо просто скопировать и запустить в командной строке. Данный скрипт всё сделает самостоятельно.
Не работает двунаправленный буффер обмена? Зайди на эту страницу из браузера внутри виртуальной машины.

На самый крайний случай написан второй скрипт, который всё останавливает, удаляет, приводит к изначальному состоянию:
> cd /home/NIKITENKO && wget https://raw.githubusercontent.com/a-perevalov/nikitenko/main/stop.py && python3 stop.py

Разберем что именно происходит во время выполнения скрипта:
- Создаются 4 контейнера в соответствии с заданием. Их имена:
> nikitenko_attacker_1
> nikitenko_user_1
> nikitenko_fail2ban_1
> nikitenko_posgres_1
- Создаются две сети (внешняя для attacker и user и внутренняя для postgres):
> й
