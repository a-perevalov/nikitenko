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
  > Внешняя сеть:
  > nikitenko_ext_net
  > 10.20.30.0/24
  > Внутренняя сеть:
  > nikitenko_int_net
  > 1.2.3.4/24
 - Соответственно, контейнерам присвоены следующие адреса (обрати внимание, у fail2ban два адреса, так как он связывает две сети и является шлюзом для обоих):
  > nikitenko_attacker_1 - 10.20.30.100
  > nikitenko_user_1 - 10.20.30.101
  > nikitenko_fail2ban_1 - 10.20.30.250 + 1.2.3.250
  > nikitenko_posgres_1 - 1.2.3.4
 - Создается база данных с именем db, в базу данных заводятся следующие роли и пользователи:
  > NIKITENO - суперпользователь. По заданию он может подключиться к базе данных только локально (то есть из контейнера postgres)
  > admin, writer, reader - простые пользователи с разными правами. По заданию
