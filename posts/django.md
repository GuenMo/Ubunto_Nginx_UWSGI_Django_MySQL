# Django

- 프로젝트 폴더 생성 & 권한, 소유권 설정

```commandline
sudo mkdir -p /var/www/live_test
sudo chown deployer:djangogroup /var/www/live_test
sudo usermod -a -G djangogroup ubuntu
sudo chmod g+w /var/www/live_test
```

- virtualenv 생성 & 활성화

```commandline
cd /var/www/live_test
sudo python3 -m venv venv
```

- Django 설치

```commandline
sudo -s
source venv/bin/activate
pip install django
```

- Project 생성

```command
django-admin.py startproject mysite .
python manage.py migrate
python manage.py createsuperuser
```

- 데이터베이스 소유 변경

```commandline
sudo chown deployer:www-data db.sqlite3
```

- 프로젝트 셋팅 변경

```commandline
nano mysite/settings.py
ALLOWED_HOSTS = ['*']
STATIC_ROOT = os.path.join(BASE_DIR, 'static/')
```

- static files 모으기

```commandline
python manage.py collectstatic
```

- 서버 구동 테스트

```commandline
exit
source venv/bin/activate
python manage.py runserver 0.0.0.0:8000
```