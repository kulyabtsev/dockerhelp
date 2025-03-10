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
| ` docker pull <имя образа> ` | Скачать образ  |
| ` docker image ls ` | Посмотреть список скачанных образов |
| ` docker image rm <имя или ID образа> ` | Удаление скачанного образа |


## Dockerfile для Python-скрипта

Чтобы запустить Python-скрипт в Docker, в контейнере должен находиться соответствующий Python-файл. То есть его нужно перенести в контейнер из нашей операционной системы. Это можно (и нужно) делать через инструкции Dockerfile, из которого затем будет собран образ. 
Для этого надо создать файл main.py:
```
if __name__ == '__main__': 
    print('I am in Docker!')
```
Модифицировать Dockerfile:
```
FROM python:3.11-slim
# возьмём образ, который мы скачали ранее и в котором уже установлен Python

LABEL author="mle-student"
# инструкция LABEL задаёт метаданные для контейнера
# можно указать своё имя

COPY . ./my_super_dir
# инструкция COPY копирует содержимое текущей директории в директорию, 
# которую указали второй командой - в данном случае это my_super_dir
# если такой директории не было, docker её создаст
```

## Дюжина инструкций Dockerfile

**FROM** — задаёт базовый (родительский) образ. \
**LABEL** — описывает метаданные. Например — сведения о том, кто создал и поддерживает образ. \
**ENV** — устанавливает постоянные переменные среды. \
**RUN** — выполняет команду и создаёт слой образа. Используется для установки в контейнер пакетов. \
**COPY** — копирует в контейнер файлы и папки. \
**ADD** — копирует файлы и папки в контейнер, может распаковывать локальные .tar-файлы. \
**CMD** — описывает команду с аргументами, которую нужно выполнить когда контейнер будет запущен. Аргументы могут быть переопределены при запуске контейнера. В файле может присутствовать лишь одна инструкция CMD. \
**WORKDIR** — задаёт рабочую директорию для следующей инструкции. \
**ARG** — задаёт переменные для передачи Docker во время сборки образа. \
**ENTRYPOINT** — предоставляет команду с аргументами для вызова во время выполнения контейнера. Аргументы не переопределяются. \
**EXPOSE** — указывает на необходимость открыть порт. \
**VOLUME** — создаёт точку монтирования для работы с постоянным хранилищем.

> [!NOTE]
> Про Docker Registry: https://www.geeksforgeeks.org/what-is-docker-registry/ \
Инструкции в Dockerfile: https://docs.docker.com/develop/develop-images/instructions/ \
Про Dockerfile: https://habr.com/ru/companies/ruvds/articles/439980/


<details>
<summary>Дополнительные материалы</summary>
<ul>
<li>Andrea Ligios <a href="https://www.baeldung.com/ops/docker-compose">Introduction to Docker Compose</a> — в статье рассказано про основные концепции Docker Compose.</li>
<li>Avimanyu Bandyopadhyay <a href="https://linuxhandbook.com/docker-compose-up-start-down-stop/">Docker Compose Up vs Start and Down vs Stop: Differences Explained</a> — здесь вы найдёте описание команд docker compose с детальными примерами.</li>
<li>А на <a href="https://stackoverflow.com/questions/46428420/docker-compose-up-down-stop-start-difference">этой странице</a> различие между командами <strong>docker compose</strong> описано лаконично — такую шпаргалку удобно держать под рукой.</li>
</ul>
</details>
