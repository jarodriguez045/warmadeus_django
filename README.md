django
nginx
postgresql
docker
docker-compose
gunicorn

DEVELOPMENT
docker-compose up -d --build

PRODUCTION
in the root dir. create a file .env.prod
in the file add: 
    DEBUG=0
    SECRET_KEY=change_me
    DJANGO_ALLOWED_HOSTS=localhost 127.0.0.1 [::1]
    SQL_ENGINE=django.db.backends.postgresql
    SQL_DATABASE=project_prod
    SQL_USER=project
    SQL_PASSWORD=project
    SQL_HOST=db
    SQL_PORT=5432
    DATABASE=postgres

in the root dir. create a file .env.prod.db
in the file add: 
    POSTGRES_USER=project
    POSTGRES_PASSWORD=project
    POSTGRES_DB=project_prod

NOTE: change password and usernames. keep secret

$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput

http://localhost:1337