# Ubuntu Nginx uWSGI Django MySQL

## 목표

- 회사 내부 파이프 라인을 웹과 데이터 베이스로 구성 한다.
  
- 다음과 같은 네트워크 구조를 같는다.
  
![Local Image](/img/introduction/introuduction05.png)

- Virtual Box(가상 머신)으로 네트워크 구조와 서버 구성을 시뮬레이션 해본다.

- 윈도우와 리눅스가 같은 스토리지 사용시 경로 문제가 어떻게 생기는지 파악하고 솔루션을 찾는다.

## Client

- 작업자(Client)는 다음과 같은 두가지 방법으로 DB에 접속 할수 있다.

![Local Image](/img/introduction/introuduction04.png)

- OS: Window, Linux, (iOS, Android)

- Application: Maya, Houdin, Nuke, Photoshop

## Web Server

![Local Image](/img/introduction/introuduction06.png)

- OS: Linux

- Backhand: Django, REST, UWSGI

- Fronthand: Bootstrap4, JavaScript, jQurey, Vue

- Server: Nginx
  
## DB Server

- OS: Linux

- Data Base: MySQL

## Storage Server

- OS: Window
