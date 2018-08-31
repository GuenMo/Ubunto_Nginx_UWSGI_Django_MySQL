# Django

- 프로젝트 폴더 생성 & 권한, 소유권 설정

```commandline
sudo mkdir -p /var/www/onlineshop
sudo chown deployer:djangogroup /var/www/onlineshop
sudo usermod -a -G djangogroup ubuntu
sudo chmod g+w /var/www/onlineshop
```

- pyenv 설치

```commandline
git clone https://github.com/pyenv/pyenv.git ~/.pyenv

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
```

설치 확인

```commandline
source ~/.bash_profile
pyenv versions
```

- python 설치

원하는 python 버전을 설치 한다.

```commandline
pyenv install 3.6.6
```

설치 확인

```commandline
pyenv versions
pyenv shell 3.6.6
python --version
```

- python-virtualenv 설치

```commandline
sudo apt-get install -y python-virtualenv
```

- virtualenv 활성화

```commandline
cd /var/www/onlineshop
virtualenv --python=python3 venv
source venv/bin/activate
```

- Django 설치

```commandline
pip install django
```

- 테스트 프로젝트 생성

```commandline
djang-admin startproject mysite .
python manage.py migrate
python manage.py createsuperuser
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
python manage.py runserver 0.0.0.0:8080
```