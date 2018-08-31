# uWSGi

- uWSGI 설치

```commandline
pip install uwsgi
```

- 서버 구동 테스트

```commandline
uwsgi --http :8080 --home /var/www/onlineshop/venv/ --chdir /var/www/onlineshop/ --module mysite.wsgi
```

> admin 페이지에 접속해보면 static 파일들이 기능을 못하고 있다. 이는 nginx에서 처리 해준다.

- 자동 실행 설정

```commadline
cd /var/www/onlineshop
sudo mkdir run logs ssl
sudo chown deployer:www-data run
sudo chown deployer:www-data logs
```