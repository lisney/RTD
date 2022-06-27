Javascript Crawling
========================

`HTML 페이지를 가져와서, HTML/CSS등을 파싱하고, 필요한 데이터만 추출하는 기법`


가상머신 설치
-------------

1. VirtualBox - 컴퓨터 하드웨어 애뮬, 여기서 직접 만들 필요는 없었다. vagrant에서 자동으로 생성해줌

![image](https://user-images.githubusercontent.com/30430227/175845316-75e4bf33-6b27-4ba0-b636-150bf0c2b381.png)

![image](https://user-images.githubusercontent.com/30430227/175849420-0872a740-ccfc-4fbe-bc2c-3236f74979d0.png)

2. Vagrant - OS와 필수 소프트웨어를 미리 설치해서 백업해둔 이미지 제공, BOX라 함, CentoOS를 설치할 예정

[Box사이트](https://app.vagrantup.com/boxes/search)

![image](https://user-images.githubusercontent.com/30430227/175850878-25e0be8b-3d91-4f4e-82f1-5e1b98dc7779.png)

`박스 다운로드`

![image](https://user-images.githubusercontent.com/30430227/175852571-eed906f0-f40a-45ee-9ff5-4d2c1ce79455.png)

```
# 가상머신 설정 생성
vagrant init centos/7

# 박스 설치
vagrant up

# 박스 제거
vagrant box remove centos/7
```
![image](https://user-images.githubusercontent.com/30430227/175857825-1e7b781a-398b-4184-80c1-702f6bfe38c9.png)

`가상머신 접근 - vagrant ssh `

![image](https://user-images.githubusercontent.com/30430227/175857962-b676aea6-9b3e-4ef7-be83-33199d3d0cdc.png)

```
# 가상머신 실행
> vagrant up --provider virtualbox

# 접속
> vagrant ssh

# 나오기
> exit

# 가상머신 정지
> vagrant halt

# 가상머신 제거
> vagrant destory

vagrant suspend	가상머신 휴면
vagrant resume	가상머신 휴면에서 복원
vagrant reload	가상머신 재시동

# SSH 클라이언트(윈도우에서)에서 접근하기위해 Vagrnatfile 설정값 수정
  # 가상머신의 80포트를 호스트머신의 8080 포트에 할당함
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # 가상머신의 IP를 아래 설정한 IP주소에 할당함
  config.vm.network "private_network", ip: "192.168.33.10"
```



