# Virtualbox

로컬 머신에 각자의 OS에 맞는 Virtual Box가 설치한다.
> <https://www.virtualbox.org/wiki/Downloads>

Virtual Box를 이용하여 Ubuntu 서버를 설치한다.
> <http://releases.ubuntu.com/16.04/>에 방문하여 우분투 서버 버전(ubuntu-16.04.5-server-amd64.iso)을 다운로드 한다.

## 가상머신 생성

- Virtual Box 를 실행 하고 새로 만들기(N) 클릭하여 새로운 가상머신을 생성한다.

![Local Image](/img/virtualbox/virtualbox01.png)

- 가상 머신의 이름을 입력한다. 종류는 `Linux` 버전은 `Ubuntu (64-bit)`를 선택 한다.

![Local Image](/img/virtualbox/virtualbox02.png)

- 메모리는 `1024`로 설정 한다.

![Local Image](/img/virtualbox/virtualbox03.png)

- `지금 새 가상 하드 디스크 만들기(C)`를 선택한다.
  
![Local Image](/img/virtualbox/virtualbox04.png)

- `VDI`를 선택한다.

![Local Image](/img/virtualbox/virtualbox05.png)

- `동적 할당(D)`를 선택한다.

![Local Image](/img/virtualbox/virtualbox06.png)

- 기본 값으로 한다.
  
![Local Image](/img/virtualbox/virtualbox07.png)

- 만들어진 가상 머신 아이콘에서 마우스 오르쪽을 클릭 하면 메뉴가 나온다. 설정 메뉴를 선택한다.

![Local Image](/img/virtualbox/virtualbox08.png)

- `저장소` 텝을 선택 하고 `CD/DVD` 아이콘을 선택해 다운 받은 `ubuntu-16.04.5-server-amd64.ios` 파일을 선택한다.
  
![Local Image](/img/virtualbox/virtualbox09.png)

- 가상 머신 아이콘에서 마우스 오르쪽을 클릭 하면 메뉴가 나온다. 설정 메뉴를 선택 하고 네트워크를 선택 한다. `어댑터에 브리지`를 선택한다.
  
![Local Image](/img/virtualbox/virtualbox10.png)

- 메인 메뉴에 `보이기(H)` 클릭 한다.

![Local Image](/img/virtualbox/virtualbox11.png)
