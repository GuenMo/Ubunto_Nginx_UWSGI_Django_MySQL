# Ubuntu 웹 서버 환경 설정

> <http://cmder.net/>

- Root Login

Cmder 를 실행 시키고 아래 명령어로 접속

```commandline
ssh root_user@remote_host
```

- 배포용 계정 만들기

```commandline
sudo useradd –g sudo –b /home –m –s /bin/bash deployer
sudo passwd deployer
```

- 새로운 Cmder 열어서 Key Pair 생성

```commandline
ssh-keygen
// Output
Generating public/private rsa key pair.
Enter file in which to save the key (/your_home/.ssh/id_rsa):
```

- Rsa key가 만들어진 폴더로 이동

```commandline
cd /your_home/.ssh/
```

- 퍼블릭 키 서버로 복사

```commandline
cat ~/.ssh/id_rsa.pub | ssh deployer@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
// Output
The authenticity of host '203.0.113.1 (203.0.113.1)' can't be established.
ECDSA key fingerprint is fd:fd:d4:f9:77:fe:73:84:e1:55:00:ad:d6:6d:22:fe.
Are you sure you want to continue connecting (yes/no)? yes
// Output
deployer@203.0.113.1's password:
```

- 퍼블릭 키로 login

```commandline
ssh deployer@remote_host
```

> 참고 <https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1604>

- 시스템 업데이트

```commandline
sudo apt-get update
sudo apt-get upgrade
```

- 한국어 설치

```commandline
sudo apt-get install -y language-pack-ko language-pack-ko-base
sudo nano /etc/default/locale
LANG="ko_KR.UTF-8"
LANGUAGE="ko_KR:ko:en_US:en"
sudo dpkg-reconfigure locales
```

- Build-essential 설치

```commandline
// 장표
sudo apt-get install -y build-essential python3-dev python3-pip python3-cffi libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libgdk-pixbuf2.0-0 libffi-dev shared-mime-info libssl-dev python3-venv
```

```commandline
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev libmysqlclient-dev
```

- git 설치

```commandline
sudo apt-get instll git
```

- Nginx 설치 및 구동 확인

```commandline
sudo apt-get install -y nginx
sudo systemctl status nginx
```

- MySQL 서버 클라이언트 설치

```commandline
sudo apt-get install -y mysql-server mysql-client libmysqlclient-dev
```



- 질문

```commandline
# 장표 질문?
sudo groupadd djangogroup # 후반에서는 그룹을 www-data 사용?
sudo useradd –g djangogroup –b /home –m –s /bin/bash django # -s /bin/bash ?
sudo passwd django
sudo mkdir -p /var/www/onlineshop # 프로젝트 폴더는 위치?
sudo chown django:djangogroup /var/www/onlineshop
sudo usermod –a –G djangogroup ubuntu # djangogroup django ? ubutu? -g -G 차이점 ubuntu 그룹 확인
sudo chmod g+w /var/www/onlineshop
# 질문?
sudo visudo
%그룹이름 ALL=(ALL) ALL
유저이름 ALL=(ALL:ALL) ALL
그룹 권한 과 유저 권한 구분
djangogroup
```