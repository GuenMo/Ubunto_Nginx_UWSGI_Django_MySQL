# Django

- 프로젝트 폴더 생성 & 권한, 소유권 설정

```commandline
sudo mkdir -p /var/www/onlineshop
sudo chown deployer:djangogroup /var/www/onlineshop
sudo usermod –a –G djangogroup ubuntu
sudo chmod g+w /var/www/onlineshop
```

- 프로젝트 환경 설정

sudo 권한으로 가상환경을 활성화 시키고 pip로 패키지를 설치 해야 하나?

그렇다면 `sudo source venv/bin/activate` 이렇게 실행해도 되는지?

`run`과 `logs` 폴더의 그룹설정을 `www-data`?

python 3.5.2 에서 apt install python-django-common 을 설치해야 django가 설치 된다?

![uwsgi-error](/img/uwsgi_install_error.png)

권한,소유, 실행?

![uwsgi-error](/img/uwsgi_install_error2.png)

```commandline
cd /var/www/onlineshop
sudo python3 -m venv venv
sudo -s // root
source venv/bin/activate
pip install django uwsgi
exit // ubuntu ?
source venv/bin/activate
sudo mkdir run logs ssl // root ?
sudo chown django:www-data run // www-data?
sudo chown django:www-data logs // www-data?
```

실패 ㅜㅜ

- 프로젝트 환경 설정

```commandline
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev libmysqlclient-dev
```

- pyenv 설치

>pyenv란 무엇인가?
pyenv란 여러 버전의 Python을 쉽게 바꿔서 쓸 수 있게 해주는 도구이다.
예를 들면 3.5.2버전을 쓰다가, 명령어 한 줄로 2.7.12로 버전을 바꾸어서 쓸 수 있게 해준다.
이는 pyenv-virtualenv와 같이 쓰면 더욱 활용도가 높아진다.

git clone 을 이용하여 소스를 다운받고 몇 가지 설정을 해준다.

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
apt-get install python-virtualenv
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

- uWSGI 설치

```commandline
pip install uwsgi
```