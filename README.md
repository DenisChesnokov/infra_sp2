## Учебный проект для освоения Docker
В данном проекте формируется три связанных контейнера docker содержащие web приложение, базу данных и сервер nginx

## Переменные окружения
Дла формирования переменных окружения создайте в папке infra файл .env, для подключения к БД используйте следующие переменные
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME='' # имя базы данных, по умолчанию postgres
POSTGRES_USER= # логин для подключения к базе данных
POSTGRES_PASSWORD= # пароль для подключения к БД 
DB_HOST= # название сервиса (контейнера c БД)
DB_PORT= # порт для подключения к БД

## Запуск проекта
1. В директории ./infra запустите команду docker-compose up -d
2. Выполните миграции БЛ командрой docker-compose exec web python manage.py migrate
3. Создайте суперпользователя docker-compose exec web python manage.py createsuperuser
4. Подготовьте статику командой docker-compose exec web python manage.py collectstatic --no-input
5. Проверьте, что по адресу localhost/redoc в браузере доступно описание api
6. Проверьте, что по даресу localhost/admin появилось поля для авторизации
7. Авторизируйтесь суперпользователем и создайте пару записей.