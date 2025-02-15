# Django Books 📚

Проект **Django Books** — это веб-приложение для управления списком книг по Django и смежным технологиям. Оно позволяет пользователям создавать учетные записи, добавлять книги в личный список, фильтровать их по авторам или жанрам и отслеживать прогресс чтения. Проект построен на базе Django с использованием стандартного ORM и Bootstrap для интерфейса.

---

## Основные возможности 🌟
- **Учетная запись пользователя**: Регистрация, вход и управление профилем.
- **Персональный список книг**: Добавление, удаление и редактирование книг.
- **Фильтрация**: Сортировка книг по автору, жанру или статусу прочтения.
- **AJAX-обновления**: Динамическое обновление списка без перезагрузки страницы.
- **Адаптивный дизайн**: Интуитивный интерфейс на основе Bootstrap.

---

## Технологии 💻
- **Backend**: Django ORM, аутентификация, миграции.
- **Frontend**: HTML, JavaScript (AJAX, HTMX), Bootstrap.
- **База данных**: PostgreSQL.
- **Кеширование**: Memcached для ускорения работы приложения.
- **Сервер**: Gunicorn в качестве WSGI-сервера, Nginx для проксирования и статических файлов.
- **Контейнеризация**: Docker для упрощения развертывания.

---

## Установка и запуск 🛠️

### Требования
- Python 3.8+
- Django 4.0+
- PostgreSQL 15
- Docker (опционально, для контейнеризации).

### Шаги:
1. **Клонируйте репозиторий**:
   ```bash
   git clone https://github.com/Rust-it/Django_books.git
   cd Django_books
   ```
2. **Установите зависимости**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Создайте окружение**:
* Создайте файл .env для разработки и .env.prod для продакшена.
* Добавьте в .env следующие переменные:
   ```env
   DEBUG = True
   SECRET_KEY = ваш_уникальный_ключ
   DJANGO_ALLOWED_HOSTS = '127.0.0.1'
   CSRF_TRUSTED_ORIGINS = 'http://127.0.0.1'
   CACHES_BACKEND = 'django.core.cache.backends.memcached.PyMemcacheCache'
   CACHES_LOCATION = 'memcached:11211'
   INTERNAL_IPS = '127.0.0.1'

   SQL_ENGINE=django.db.backends.postgresql
   SQL_DATABASE=название_базы_данных
   SQL_USER=пользователь
   SQL_PASSWORD=пароль
   SQL_HOST=db
   SQL_PORT=5432
   DATABASE=postgres
   ```
* Для .env.prod настройте переменные для продакшена:
   ```env
   DEBUG = False
   SECRET_KEY = ваш_уникальный_ключ_для_продакшена
   DJANGO_ALLOWED_HOSTS = '127.0.0.1'
   CSRF_TRUSTED_ORIGINS = 'http://127.0.0.1'
   CACHES_BACKEND = 'django.core.cache.backends.memcached.PyMemcacheCache'
   CACHES_LOCATION = 'memcached:11211'
   INTERNAL_IPS = '127.0.0.1'

   SQL_ENGINE=django.db.backends.postgresql
   SQL_DATABASE=название_базы_данных
   SQL_USER=пользователь
   SQL_PASSWORD=пароль
   SQL_HOST=db
   SQL_PORT=5432
   DATABASE=postgres
   ```
4. **Примените миграции:**
   ```bash
   python manage.py migrate
   ```
5. **Создайте суперпользователя (опционально):**
   ```bash
   python manage.py createsuperuser
   ```
6. **Запустите сервер:**
* Для разработки:
   ```bash
   python manage.py runserver
   ```
* Для продакшена (с использованием Gunicorn и Nginx):
   ```bash
   gunicorn --workers 3 Django_books.wsgi:application
   ```
   Настройте Nginx для проксирования запросов к Gunicorn.
7. **Docker (опционально):**
Соберите и запустите контейнеры.