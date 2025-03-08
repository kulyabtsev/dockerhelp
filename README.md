# Справка по командам docker

> [!NOTE]
> В таблице приведена «полная версия» Docker-команд.</br>
> Например, docker container start — это полная версия, и если бы  вы написали docker start, то исполнилась бы та же самая команда. Это нужно для наглядности, чтобы сразу было видно, к какой части Docker они относятся (container — к контейнерам, image — к образам). При этом во многих источниках команды используются в короткой форме.</br>
> Дополнительные материалы:</br>
> [Как устроен Docker](https://cloud.yandex.ru/ru/blog/posts/2022/03/docker-containers)

| Команда | Описание команды |
|:--------| -----------------|
| ` docker container run ubuntu echo "Hello World!" ` | Запуск вывода строки Hello World! из Docker-контейнера |
| ` docker container ps ` | Посмотреть, какие контейнеры сейчас запущены |
| ` docker container ps -a ` | Просмотреть все контейнеры, которые когда-либо запускались |
| ` docker container run --name=<своё название> ubuntu echo "Hello World!" ` | Задать своё имя контейнера |
| ` docker container start -i <name или id> ` | Запуск контейнера по его имени |
