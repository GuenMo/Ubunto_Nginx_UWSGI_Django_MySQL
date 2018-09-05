# Ubuntu 웹 서버 환경 설정

## ssh

> <http://cmder.net/>

- Key Pair 생성

cmdr을 실행하고 `ssh-keygen`을 실행 한다.

```commandline
ssh-keygen
```

- Rsa key가 만들어진 폴더로 이동

```commandline
cd /your_home/.ssh/
```

- 퍼블릭 키 서버로 복사

`[uid], [hostname]` 수정하고 실행

```commandline
cat ~/.ssh/id_rsa.pub | ssh [uid]@[hostname] "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

- 퍼블릭 키로 login

```commandline
ssh [uid]@[hostname]
```

> 참고 <https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1604>

## Ubuntu Setting

- 시스템 업데이트

```commandline
sudo apt-get update
sudo apt-get upgrade
```

- 한국어 설치

```commandline
sudo apt-get install -y language-pack-ko language-pack-ko-base
```

`/etc/default/locale` 수정

```command
sudo nano /etc/default/locale

LANG="ko_KR.UTF-8"
LANGUAGE="ko_KR:ko:en_US:en"
```

![Local Image](/img/ubuntu_setting/ubuntu_setting01.png)

```command
sudo dpkg-reconfigure locales
```

- Build-essential 설치

```commandline
sudo apt-get install -y build-essential python3-dev python3-pip python3-cffi libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libgdk-pixbuf2.0-0 libffi-dev shared-mime-info libssl-dev python3-venv
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

- 배포용 계정 만들기

```commandline
sudo groupadd djangogroup
sudo useradd -g djangogroup -b /home -m -s /bin/bash deployer
sudo passwd deployer
```

## 네트워크 드라이브

- 마운트 할 폴더를 만든다

```commandline
sudo mkdir -p /mnt/ISSAC/Project
```

- 마운트 할 대상을 연결 한다.

```commandline
mount -t cifs //ip_addres/Project /mnt/ISSAC/Project -o uid=[ubuntu_id], username="XXXXXX",password="XXXXXX",domain="XXXXXX"
```

- 마운트 해제

```commandline
umount //ip_addres/Project
```

- 부팅시 자동 마운트

```commandline
nano /etc/fstab
//ip_addres/Project /mnt/ISSAC/Project cifs uid=[ubuntu_id],username=XXXXXX,password=XXXXXXXX,domain=XXXXXXX 0 0
```

- 마운트가 끝났으면, df 명령어로 연결을 확인해 봅니다.

```commandline
df -h
```