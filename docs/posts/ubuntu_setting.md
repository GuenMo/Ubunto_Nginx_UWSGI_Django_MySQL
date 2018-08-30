# Ubuntu 웹 서버 환경 설정

1. 시스템 업데이트

    ```commandline
    sudo apt-get update
    sudo apt-get upgrade
    ```

2. 한국어 설치

    ```commandline
    sudo apt-get install -y language-pack-ko language-pack-ko-base
    sudo nano /etc/default/locale
    LANG="ko_KR.UTF-8"
    LANGUAGE="ko_KR:ko:en_US:en"
    sudo dpkg-reconfigure locales
    ```

3. Build-essential 설치

    ```commandline
    // 장표
    sudo apt-get install -y build-essential python3-dev python3-pip python3-cffi libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libgdk-pixbuf2.0-0 libffi-dev shared-mime-info libssl-dev python3-venv
    ```
    
    ```commandline
    apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev libmysqlclient-dev
    ```

4. git 설치

    ```commandline
    apt-get instll git
    ```

5. Nginx 설치 및 구동 확인

    ```commandline
    sudo apt-get install -y nginx
    sudo systemctl status nginx
    ```

6. MySQL 서버 클라이언트 설치

    ```commandline
    sudo apt-get install -y mysql-server mysql-client libmysqlclient-dev
    ```

7. 배포용 계정 만들기

    ```commandline
    sudo groupadd djangogroup
    sudo useradd –g djangogroup –b /home –m –s /bin/bash deployer
    sudo passwd deployer
    ```

8. 질문

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
