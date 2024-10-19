# Kittygram

[![GitHub Actions Status](https://github.com/Port-tf/kittygram/actions/workflows/main.yml/badge.svg)](https://github.com/Port-tf/kittygram/actions)


**Kittygram** — социальная сеть для обмена фотографиями любимых питомцев. Это полностью рабочий проект, который состоит из бэкенд-приложения на Django и фронтенд-приложения на React.

## Основные возможности
- Регистрация и авторизация пользователей.
- Загрузка, редактирование и удаление фотографий питомцев.
- Просмотр и лайк фотографий других пользователей.
- Интерактивный фронтенд на React.
- Бэкенд с использованием Django и Django REST Framework.

## Стек технологий
- **Backend**: Python, Django, Django REST Framework, PostgreSQL.
- **Frontend**: React, JavaScript, HTML, CSS.
- **Контейнеризация**: Docker, Docker Compose.
- **CI/CD**: GitHub Actions, DockerHub.
- **Прочие инструменты**: Nginx, Gunicorn, Certbot для SSL.

## Как развернуть проект

### Шаг 1. Клонируйте репозиторий
```
bash
git clone https://github.com/Port-tf/kittygram.git
cd kittygram
```

### Шаг 2. Заполните .env файл
В корневой директории проекта создайте файл .env со следующими параметрами:

```
DB_NAME=<имя_базы_данных>
DB_USER=<пользователь_базы_данных>
DB_PASSWORD=<пароль_базы_данных>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<секретный_ключ_Django>
DEBUG=False
ALLOWED_HOSTS=<ваш_домен_или_IP>
```

### Шаг 3. Запустите проект в Docker
Проект использует Docker для контейнеризации. Запустите проект с помощью Docker Compose:

```
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py collectstatic --noinput
```

### Шаг 4. Примените миграции и соберите статику

```
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py collectstatic --noinput
```

### Шаг 5. Настройте Nginx и SSL
Nginx уже настроен для работы с проектом через Docker, но убедитесь, что вы установили SSL-сертификат через Certbot:

```
sudo certbot --nginx -d <ваш_домен>
```

## Как запустить тесты локально
### 1. Создайте виртуальное окружение:

```
python3 -m venv venv
source venv/bin/activate
```

### 2. Установите зависимости:

```
pip install -r backend/requirements.txt
```

### 3. Запустите тесты с помощью pytest:

```
pytest
```

## Настройка CI/CD через GitHub Actions

### 1. В корне репозитория создайте файл tests.yml со следующим содержимым:

```
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

### 2. Скопируйте содержимое файла .github/workflows/main.yml в файл kittygram_workflow.yml в корневой директории проекта.

### 3. Пуш в ветку main автоматически запускает тестирование и деплой проекта. После успешного деплоя в телеграм придет уведомление.

## Чек-лист для проверки перед отправкой задания
- Проект Taski доступен по доменному имени, указанному в tests.yml.
- Проект Kittygram доступен по доменному имени, указанному в tests.yml.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя приходит сообщение в телеграм.
- В корне проекта есть файл kittygram_workflow.yml.

№№ Автор
№№№ Проект разработан Шевчуком Максимом
