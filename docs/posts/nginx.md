# Nginx

- Nginx 설치

```commandline
sudo apt-get install nginx
```

- 구동 확인

```commandline
sudo systemctl status nginx
```

웹 브라우져에서 서버 IP 입력 해본다.
![Local Image](/img/nginx01.png)

- 장표 내용

```commandline  
sudo ln -s /etc/nginx/sites-available/onlineshop /etc/nginx/sites-enabled/
sudo vim /etc/nginx/nginx.conf
//내용 수정
server_name_hask_bucket_size 128
sudo nginx –t
sudo systemctl restart nginx
```