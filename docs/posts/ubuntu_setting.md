# Ubuntu 웹 서버 환경 설정

## Ubuntu Setting

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
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3.6-dev
```

- git 설치

```commandline
sudo apt-get install git
```

- MySQL 서버 클라이언트 설치

```commandline
sudo apt-get install -y mysql-server mysql-client libmysqlclient-dev
```

## 배포용 유저 생성

> <http://cmder.net/>

- Root Login

Cmder 를 실행 시키고 아래 명령어로 접속

```commandline
ssh root_user@remote_host
```

- 배포용 계정 만들기

```commandline
sudo groupadd djangogroup
sudo useradd –g djangogroup –b /home –m –s /bin/bash deployer
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

## 네트워크 드라이브

- 마운트 할 폴더를 만든다

```commandline
sudo mkdir -p /mnt/ISSAC/Project
```

- 마운트 할 대상을 연결 한다.

```commandline
mount -t cifs //ip_addres/Project /mnt/ISSAC/Project -o username="XXXXXX",password="XXXXXX",domain="XXXXXX"
```

- 마운트 해제

```commandline
umount //ip_addres/Project
```

- 부팅시 자동 마운트

```commandline
nano /etc/fstab
//ip_addres/Project /mnt/ISSAC/Project cifs username=XXXXXX,password=XXXXXXXX,domain=XXXXXXX 0 0
```

- 마운트가 끝났으면, df 명령어로 연결을 확인해 봅니다.

```commandline
df -h
```