# SSH

## 윈도우용 SSH 설치

> <http://cmder.net/>

## 비밀번호로 접속

Cmder 를 실행 시키고 아래 명령어로 접속

```commandline
ssh username@remote_host
```

## RSA Key로 접속

- Key Pair 를 만든다.

```commandline
ssh-keygen
// Output
Generating public/private rsa key pair.
Enter file in which to save the key (/your_home/.ssh/id_rsa):
```

- Rsa key가 만들어진 폴더로 이동 한다.

```commandline
cd /your_home/.ssh/
```

- 퍼블릭키를 서버로 복사 한다.

```commandline
cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
// Output
The authenticity of host '203.0.113.1 (203.0.113.1)' can't be established.
ECDSA key fingerprint is fd:fd:d4:f9:77:fe:73:84:e1:55:00:ad:d6:6d:22:fe.
Are you sure you want to continue connecting (yes/no)? yes
// Output
username@203.0.113.1's password:
```

> 참고 <https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1604>