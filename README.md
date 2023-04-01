![workflow](https://github.com/Oksana-laura/foodgram-project-react/actions/workflows/......yml/badge.svg)

# «Продуктовый помощник» Foodgram
На этом сайте пользователи могут публиковать рецепты, подписываться на публикации других пользователей, добавлять понравившиеся рецепты в список «Избранное», а перед походом в магазин скачивать сводный список продуктов, необходимых для приготовления одного или нескольких выбранных блюд.

## Запуск проекта на удаленном сервере
Склонируйте репозиторий и перейдите в него в командной строке:

    git clone https://github.com/Oksana-laura/yamdb_final.git

Выполните вход на свой удаленный сервер

Скопируйте подготовленные файлы docker-compose.yaml и nginx/default.conf из вашего проекта на сервер

    scp docker-compose.yaml <username>@<host>/home/<username>/docker-compose.yaml
    sudo mkdir nginx
    scp default.conf <username>@<host>/home/<username>/nginx/default.conf

Остановите службу nginx

    sudo systemctl stop nginx 

Установите docker на сервер:

    sudo apt install docker.io

Установите docker-compose на сервер:

    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Запустите docker-compose:

    docker-compose up -d --build

Соберите файлы статики, и запустите миграции командами:

    docker-compose exec web python3 manage.py makemigrations
    docker-compose exec web python3 manage.py migrate
    docker-compose exec web python3 manage.py collectstatic --no-input

Создайте суперпользователя командой:

    docker-compose exec web python3 manage.py createsuperuser


## Автор проекта
- Оксана Лаура