# Django

- 프로젝트 폴더 생성 & 권한, 소유권 설정

```commandline
sudo mkdir -p /var/www/onlineshop
sudo chown deployer:djangogroup /var/www/onlineshop
sudo usermod -a -G djangogroup ubuntu
sudo chmod g+w /var/www/onlineshop
```

- 프로젝트 환경 설정

```commandline
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev libmysqlclient-dev
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
