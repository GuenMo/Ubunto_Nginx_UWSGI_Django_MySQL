# Storage

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