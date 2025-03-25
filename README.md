# Django Books 📚

The **Django Books** project is a web application for managing a book list. It allows users to create accounts, add books to a personal list, filter them by authors or genres, and track reading progress. The project is built using Django with its standard ORM and Bootstrap for the interface.

## Key Features 🌟
- **User Account**: Registration, login, and profile management.
- **Personal Book List**: Add, remove, and edit books.
- **Filtering**: Sort books by author, genre, or reading status.
- **AJAX Updates**: Dynamically refresh the list without page reloads.
- **Responsive Design**: Intuitive Bootstrap-based interface.

## Technologies 💻
- **Backend**: Django ORM, authentication, migrations.
- **Frontend**: HTML, JavaScript (AJAX, HTMX), Bootstrap.
- **Database**: PostgreSQL.
- **Caching**: Memcached for performance optimization.
- **Server**: Gunicorn as the WSGI server, Nginx for proxying and static files.
- **Containerization**: Docker for simplified deployment.

## Installation and Setup 🛠️

### Requirements
- Python 3.8+
- Django 4.0+
- PostgreSQL 15
- Docker (optional, for containerization).

### Steps:
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Rust-it/Django_books.git
   cd Django_books
   ```
2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Set Up Environment**:
* Create a .env file for development and .env.prod for production.
* Add the following variables to .env:
   ```env
   DEBUG = True
   SECRET_KEY = your_unique_key
   DJANGO_ALLOWED_HOSTS = '127.0.0.1'
   CSRF_TRUSTED_ORIGINS = 'http://127.0.0.1'
   CACHES_BACKEND = 'django.core.cache.backends.memcached.PyMemcacheCache'
   CACHES_LOCATION = 'memcached:11211'
   INTERNAL_IPS = '127.0.0.1'

   SQL_ENGINE=django.db.backends.postgresql
   SQL_DATABASE=your_database_name
   SQL_USER=your_username
   SQL_PASSWORD=your_password
   SQL_HOST=db
   SQL_PORT=5432
   DATABASE=postgres
   ```
* For .env.prod, configure production settings:
   ```env
   DEBUG = False
   SECRET_KEY = your_production_secret_key
   DJANGO_ALLOWED_HOSTS = '127.0.0.1'
   CSRF_TRUSTED_ORIGINS = 'http://127.0.0.1'
   CACHES_BACKEND = 'django.core.cache.backends.memcached.PyMemcacheCache'
   CACHES_LOCATION = 'memcached:11211'
   INTERNAL_IPS = '127.0.0.1'

   SQL_ENGINE=django.db.backends.postgresql
   SQL_DATABASE=production_db_name
   SQL_USER=production_db_user
   SQL_PASSWORD=production_db_password
   SQL_HOST=db
   SQL_PORT=5432
   DATABASE=postgres
   ```
4. **Apply Migrations**:
   ```bash
   python manage.py migrate
   ```
5. **Create a Superuser (Optional)**:
   ```bash
   python manage.py createsuperuser
   ```
6. **Run the Server**:
* For development:
   ```bash
   python manage.py runserver
   ```
* For production (using Gunicorn and Nginx):
   ```bash
   gunicorn --workers 3 Django_books.wsgi:application
   ```
   Configure Nginx to proxy requests to Gunicorn.
7. **Docker (Optional):**
* Build and run the containers:
   ```bash
   docker-compose up --build
   ```
