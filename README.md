Kittygram - социальная сеть для размещение фотографий домашних животных.

Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:
git clone git@github.com:Bant0n/kittygram_final.git

Перейти в корневую директорию:
cd kittygram_final

Создать файл .evn для хранения ключей
Пример для примера .evn используйте файл .env_example

Запустить docker-compose.production:
docker compose -f docker-compose.production.yml up

Выполнить миграции, сбор статики:
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

Создать суперпользователя, ввести почту, логин, пароль:
docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
