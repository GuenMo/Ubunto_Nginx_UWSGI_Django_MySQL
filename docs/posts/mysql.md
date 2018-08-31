# MySQL

- MySQL 설치

```commandline
sudo su
apt-get update
apt-get install mysql-server
```

- MySQL 외부 접속

```commandline
mysql -u root -p
```

``` mysql
grant all privileges on *.* to 'root'@'%' identified by 'alfred1234';
flush privileges;
```

```commandline
cd /etc/mysql/mysql.conf.d/
nano mysqld.cnf
// bind-address = 127.0.0.1 아래와 같이 수정
bind-address = 0.0.0.0
```

- MySQL 한글 깨짐 현상 해결

```commandline
cd /etc/mysql/conf.d/
nano mysql.cnf
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
service mysql start
```

- MySql 자동 실행

```commandline
apt-get install sysv-rc-conf
sysv-rc-conf --list // service 리스트가 출력되어 확인 하실 수 있습니다.
service --status-all // service 명령어로 리스트 및 상태를 확인합니다.
sysv-rc-conf mysql off // ex) sudo sysv-rc-conf bind9 off
sysv-rc-conf mysql on // ex) sudo sysv-rc-conf bind9 on
```
