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
 