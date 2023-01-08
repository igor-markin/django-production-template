# Django Production Template    
This is a template of a dockerized Django project with Postgres, Gunicorn, and Nginx.
  
## What is inside?  
### Docker Images  
- Python 3.10-alpine  
- Postgres 15.1-alpine  
- Nginx 1.23-alpine  
  
### Django Project  
- Django 4.1.5  
- Gunicorn 20.1.0  
  
## How to use?  
### Production server  
- Build and up: `docker-compose -f docker-compose.prod.yml up -d --build`  
- Migrate migrations: `docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput`  
- Stop and delete volumes: `docker-compose -f docker-compose.prod.yml down -v`

**After startup, the production server will:**
- check the code for errors using flake8
- install dependencies
- wait for the database to start
- launch Django at http://localhost:1337/

### Development Server  
- Build and up: `docker-compose up -d --build`  
- Stop and delete volumes: `docker-compose down -v`  

**After startup, the production server will:**
- install dependencies
- wait for the database to start
- clean up the database
- apply migrations
- launch Django at http://localhost:8000/

**Warning!** Don't forget to change credentials in .env files and to add them to .gitignore.

*The template is based on [an article of Michael Herman](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/).*