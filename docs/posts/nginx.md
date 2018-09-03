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

- uWSGI를 Nginx에 연결

```commandline
sudo nano /etc/nginx/sites-avaliable/onlineshop

upstream django {
    server unix:/var/www/onlineshop/run/uwsgi.sock;
}

server {
    listen 80;
    server_name 192.168.150.246;
    charset     utf-8;

    location = /favicon.ico { access_log off; log_not_found off; }

    location /media  {
        alias /var/www/onlineshop/media;
    }

    location /static {
        alias /var/www/onlineshop/static;
    }

    location / {
        include /etc/nginx/uwsgi_params;
        uwsgi_pass django;
    }
}
```

- link 만들기

```commandline
sudo ln -s /etc/nginx/sites-available/onlineshop /etc/nginx/sites-enabled/
sudo vim /etc/nginx/nginx.conf
//내용 수정
server_name_hask_bucket_size 128
```

- Nginx 재실행

```commandline
sudo nginx –t
sudo systemctl restart nginx
```