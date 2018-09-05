# MySQL

- MySQL 설치

```commandline
sudo apt-get update
sudo apt-get install mysql-server
```

- MySQL 외부 접속

```commandline
mysql -u root -p
```

``` mysql
grant all privileges on *.* to 'root'@'%' identified by 'Password';
flush privileges;
exit;
```

```commandline
cd /etc/mysql/mysql.conf.d/
sudo nano mysqld.cnf
// bind-address = 127.0.0.1 아래와 같이 수정
bind-address = 0.0.0.0
```

- MySQL 한글 깨짐 현상 해결

```commandline
cd /etc/mysql/conf.d/
sudo nano mysql.cnf
// client 부분밑에 추가
[client]
default-character-set = utf8
// mysqld 부분밑에 추가
[mysqld]
init_connect = SET collation_connection = utf8_general_ci
init_connect = SET NAMES utf8
character-set-server = utf8
collation-server = utf8_general_ci
// mysqldump 부분밑에 추가
[mysqldump]
default-character-set = utf8
// mysql 부분밑에 추가
[mysql]
default-character-set = utf8
```

- MySql 서버 시작

```commandline
sudo service mysql start
```

- MySql 자동 실행

```commandline
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf --list // service 리스트가 출력되어 확인 하실 수 있습니다.
sudo service --status-all // service 명령어로 리스트 및 상태를 확인합니다.
sudo sysv-rc-conf mysql off // ex) sudo sysv-rc-conf bind9 off
sudo sysv-rc-conf mysql on // ex) sudo sysv-rc-conf bind9 on
```

- Database 생성

```sql
CREATE DATABASE mydatabase;
```

- Django 데이터 베이스 셋팅 수정

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mydatabase',
        'USER': 'ID',
        'PASSWORD': 'Password',
        'HOST': 'Hostname'
    }
}
```

- mysqlclient 설치

```commandline
sudo -s
source /venv/bin/activate
pip install mysqlclient
```