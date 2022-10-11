# django_docker_template

here is sample of django app development environment for docker using mysql.  
and compete that tutorials  
https://docs.djangoproject.com/en/4.1/intro/tutorial01/  

# start containers

```sh
docker-compose build
docker-compose up -d

(base) ishizu.yasunari@hm-p1186 django_docker_template % docker ps
CONTAINER ID   IMAGE               COMMAND                  CREATED              STATUS              PORTS                    NAMES
a1e1c84b9f40   mysql:5.7           "docker-entrypoint.s…"   About a minute ago   Up About a minute   3306/tcp, 33060/tcp      django_docker_template-db-1
b50f2861bc6e   django-web:django   "python manage.py ru…"   4 minutes ago        Up 12 seconds       0.0.0.0:8000->8000/tcp   django_docker_template-web-1
```

# make init config

```sh
docker exec -it django_docker_template-web-1 bash

root@b50f2861bc6e:/django# python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
  
  root@b50f2861bc6e:/django# python manage.py createsuperuser
Username (leave blank to use 'root'): admin
Email address: admin@admin.com
Password:
Password (again):
The password is too similar to the username.
This password is too short. It must contain at least 8 characters.
This password is too common.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
root@b50f2861bc6e:/django# python manage.py startapp sample
root@b50f2861bc6e:/django#
```

# endpoints
```
http://localhost:8000/
http://localhost:8000/admin/
http://localhost:8000/sample/
```
