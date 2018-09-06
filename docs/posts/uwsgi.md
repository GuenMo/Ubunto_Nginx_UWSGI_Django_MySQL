# uWSGi

- uWSGI 설치

```commandline
sudo -s
source venv/bin/activate
pip install uwsgi
```

- 서버 구동 테스트

```commandline
uwsgi --http :8000 --home /var/www/live_test/venv/ --chdir /var/www/live_test/ --module mysite.wsgi
deactivate
```

> admin 페이지에 접속해보면 static 파일들이 기능을 못하고 있다. 이는 nginx에서 처리 해준다.

- 자동 실행 설정

```commadline
cd /var/www/live_test
sudo mkdir uwsgi
sudo chown deployer:www-data uwsgi
cd /var/www/live_test/uwsgi
sudo mkdir run logs ssl
sudo chown deployer:www-data run
sudo chown deployer:www-data logs
```

- uwsgi.ini 파일 추가

```commandline
sudo nano /var/www/live_test/uwsgi/run/uwsgi.ini

[uwsgi]
uid = deployer
base = /var/www/live_test
home = %(base)/venv
chdir = %(base)
module = mysite.wsgi:application
env = DJANGO_SETTINGS_MODULE=mysite.settings
master = true
processes = 5
socket = %(base)/uwsgi/run/uwsgi.sock
logto = %(base)/uwsgi/logs/uwsgi.log
chown-socket = %(uid):www-data
chmod-socket = 660
vacuum = true
```

- uwsgi.service 추가

```commandline
sudo nano /etc/systemd/system/uwsgi.service

[Unit]
Description=uWSGI Emperor service

[Service]
ExecStart=/var/www/live_test/venv/bin/uwsgi --emperor /var/www/live_test/uwsgi/run
User=deployer
Group=www-data
Restart=on-failure
KillSignal=SIGQUIT
Type=notify
NotifyAccess=all
StandardError=syslog

[Install]
WantedBy=multi-user.target
```

```commandline
sudo systemctl start uwsgi
sudo systemctl enable uwsgi
sudo systemctl status uwsgi
```