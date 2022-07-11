Arduino
=========


레귤레이터 교체 - 레귤레이터 7805
----------------------------

`12V 전압을 5V로 떨어트리는 레귤레이터 문제로 전압불안정, 아두이노 레귤레이터는 1번이 그라운드, 2번이 5V출력, 3번이 입력`

![image](https://user-images.githubusercontent.com/30430227/176808473-92dada01-704c-46c3-af73-afbfabf788fa.png)
![image](https://user-images.githubusercontent.com/30430227/176807691-0be12aa2-1d53-4dcc-8076-5fc239123a29.png)
![image](https://user-images.githubusercontent.com/30430227/176807328-512dea41-4de9-484f-8499-85e71f0f5c3b.png)

![image](https://user-images.githubusercontent.com/30430227/176807389-ed632b36-62f0-4ed1-8948-d7e09ad7294d.png)



스탭모터 드라이버 A4988, DRV8825
--------------

![image](https://user-images.githubusercontent.com/30430227/176809240-90413b89-5b2b-450a-b45f-bbae24644486.png)
![image](https://user-images.githubusercontent.com/30430227/176809300-355b0103-cd8f-4b4a-b484-a21bd9183164.png)

![image](https://user-images.githubusercontent.com/30430227/177500282-810cb633-97a0-4ce9-8c64-da08f3f89a2e.png)


CNC 제어 프로그램 -GLBL
---------------------

[GRBL](https://github.com/grbl/grbl)
 
 `보드 라이브러리 설치 > GLBL 폴더 선택`
 
 ![image](https://user-images.githubusercontent.com/30430227/177696088-0a22d6e3-ae70-4973-b9c5-1b76fcff1bf5.png)


`예제에서 선택하고 > 업로드`

![image](https://user-images.githubusercontent.com/30430227/177696414-04b65a0c-8ade-4ef0-8c7c-090643740b05.png)


GLBL 컨트롤러 - JAVA 런타임 필요
--------------------

[유니버설G코드센더](https://winder.github.io/ugs_website/download/)

![image](https://user-images.githubusercontent.com/30430227/177696801-496ae569-d26e-4da8-8fb7-f23a2675ebb4.png)



부품 
-----

![image](https://user-images.githubusercontent.com/30430227/177021322-371d2eb6-c2b1-4f3a-92a9-7e88805fc1e6.png)

![image](https://user-images.githubusercontent.com/30430227/177085941-4d99d9af-3763-4bc3-ad31-84eb1cb7315f.png)


아두이노 보드 매니저 업그레이드
--------------------

![image](https://user-images.githubusercontent.com/30430227/177694462-51075aa6-578a-4c84-a631-cdb61db0a7ea.png)


라즈베리파이 모니터 없이 설치하기
----------------------------------

1. boot 폴더에 'ssh', 'wpa_supplicant.conf' 파일 생성

```
ssh는 비워두고, wpa... ssid 공유기id, psk패스워드

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=GB

network={
	ssid="KT_GiGA_2G"
	psk="123456789"
}
```

2. PuTTY 설치 - 윈도우 원격 접속  프로그램 설치위함

[주소](https://putty.org/)

![image](https://user-images.githubusercontent.com/30430227/177980019-c475d32b-3d1c-4689-a7ab-92e7765c5c30.png)


3. 라즈베리파이 부팅 후 putty로 연결

```
초기 아이디/패스 - pi/raspberry

윈도우 원격 접속 프로그램 설치
sudo apt-get install xrdp
sudo pat-get install tightvncserver
```

4. 윈도우 원격 프로그램 실행 

```
윈도우키 누르고 '원격' > 원격 데스크톱 실행 > 라즈베리파이 원격 접속
```

![image](https://user-images.githubusercontent.com/30430227/178209304-963a5469-2015-44d7-9985-31e9462e4404.png)


라즈베리파이 모니터 
------------------

```
메모리 --> boot 드라이브 --> config.txt

hdmi_force_hotplug=1 앞의 #을 삭제하여 활성화!
hdmi_drive=2 역시 #을 삭제하여 활성화 ! 
그리고 저장합니다 
(hdmi_drive 숫자로 해상도를 조절하기 때문에 모니터에 맞춰서 입력해줘야 화면이 짤리지 않아요!)

# 라즈베리파이 아이피 주소 찾기
ifconfig

# 한글
sudo apt-get install fonts-nanum

sudo apt-get install uim uim-byeoru //한영 전환 Shift-space

# SSH 연결 안될 때
sudo raspi-config
Interfacing Options > SSH

```
