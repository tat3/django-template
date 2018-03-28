# Django template
Default settings for my Django projects.

# Requirements
* Docker
* Docker Compose

# Usage

## Initial settings
```
$ project="project_name"
$ container=${project}_app_1
$ app="app_name"

$ docker-compose build
$ docker-compose up
$ docker exec -it ${container} django-admin startproject ${project}

$ mkdir ${project}/${app}
$ docker exec -it ${container} python manage.py startapp ${app} ${project}/${app}
```
...

## Git
```
$ git init
$ git config --global user.email user@example.com
$ git remote add origin https://github.com/tat3/hoge.git
$ git push origin master
```

## Deploy to Heroku
```Procfile
gunicorn mysite.wsgi --log-file -
```
Fix `mysite.wsgi` to `{project_name}.wsgi`.

```
$ heroku create ${myapp}
$ heroku config:set PRODUCTION=True
$ heroku config:set SECRET_KEY='hogehoge'
$ heroku config:set DISABLE_COLLECTSTATIC=1
$ git push heroku master
```

### Introduce whilenoise
```python:setting.py
MIDDLEWARE_CLASSES += (
    'whitenoise.middleware.WhiteNoiseMiddleware',
)
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

```