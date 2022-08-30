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


CNC 제어 프로그램 -GRBL
---------------------

`아두이노 메가2560용 따로 있다. 컨트롤러 Baud Rate 115200 선택`

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


5. fileZilla 로 접속

```
라즈베리파이 기본 포트 : 22

```

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


NodeJS 로 모터 컨트롤 하기 
-------------------------

[사이트](https://github.com/nodesource/distributions}

```
# 노드js 최신버전 설치
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# node.js용 pigpio 라이브러리 설치 
sudo apt-get update //이줄은 이미 설치된거같음
sudo apt-get install pigpio //이줄도 이미 설치된거같음

npm install pigpio // NodeJS기반 pigpio 설치

# 모터 드라이버용 모듈 설치
npm install pigpio-l298n //1이 아니라 L이다

# VSCode 설치
sudo apt install code

# 스크래치3 설치 - 파이 > 기본설정 > Recommended Software에서 설치할 수도있다
sudo apt-get update
sudo apt-get install scratch3

```


VSCode로 원격 프로그래밍 
------------------------

```
# remote SSH 설치
좌측 하단의 연결 버튼(녹색) 클릭 > 상단 메뉴에서 Connect to Host > 사용자이름@아이피

# VSCodd SSH 접속 안될 때
config 파일 열어
    Port 22 추가한다
```


라즈베리파이 안전종료
-------------------

```
# 둘 중 
sudo shutdown -h now
sudo poweroff
```


모터 제어하기 - 파이썬 
------------------------

![image](https://user-images.githubusercontent.com/30430227/178426917-ef5d53e7-8549-44ba-8c65-8b73f622e513.png)

![image](https://user-images.githubusercontent.com/30430227/178651110-1851aab6-2d35-4f9b-b41d-c3aa156b9cef.png)

```
L298N 모터 드라이버의 Enable핀을 점프(5V)시키면 최대속도로 회전한다
Enable, 다음 2쌍의 핀이 A 모터를 제어한다(2쌍의 핀은 방향을 제어)
01 Forward, 10 Backward, 00,11 Stop

# 전원부
외부입력과 외부출력(5V)는 모두 가운데 GND를 공유한다
5V 점퍼를 제거하면 외부출력이 되지 않고 오로지 입력전력을 활용할 수 있게된다.
```

```
# -*- coding: utf-8 -*-

# 라즈베리파이 GPIO 패키지 
import RPi.GPIO as GPIO
from time import sleep

# 모터 상태
STOP  = 0
FORWARD  = 1
BACKWORD = 2

# 모터 채널
CH1 = 0
CH2 = 1

# PIN 입출력 설정
OUTPUT = 1
INPUT = 0

# PIN 설정
HIGH = 1
LOW = 0

# 실제 핀 정의
#PWM PIN
ENA = 17  #37 pin SPEED Control
ENB = 0   #27 pin

#GPIO PIN
IN1 = 27  #37 pin
IN2 = 22  #35 pin
IN3 = 6   #31 pin
IN4 = 5   #29 pin

# 핀 설정 함수
def setPinConfig(EN, INA, INB):        
    GPIO.setup(EN, GPIO.OUT)
    GPIO.setup(INA, GPIO.OUT)
    GPIO.setup(INB, GPIO.OUT)
    # 100khz 로 PWM 동작 시킴 
    pwm = GPIO.PWM(EN, 100) 
    # 우선 PWM 멈춤.   
    pwm.start(0) 
    return pwm

# 모터 제어 함수
def setMotorContorl(pwm, INA, INB, speed, stat):

    #모터 속도 제어 PWM
    pwm.ChangeDutyCycle(speed)  
    
    if stat == FORWARD:
        GPIO.output(INA, HIGH)
        GPIO.output(INB, LOW)
        
    #뒤로
    elif stat == BACKWORD:
        GPIO.output(INA, LOW)
        GPIO.output(INB, HIGH)
        
    #정지
    elif stat == STOP:
        GPIO.output(INA, LOW)
        GPIO.output(INB, LOW)

        
# 모터 제어함수 간단하게 사용하기 위해 한번더 래핑(감쌈)
def setMotor(ch, speed, stat):
    if ch == CH1:
        #pwmA는 핀 설정 후 pwm 핸들을 리턴 받은 값이다.
        setMotorContorl(pwmA, IN1, IN2, speed, stat)
    else:
        #pwmB는 핀 설정 후 pwm 핸들을 리턴 받은 값이다.
        setMotorContorl(pwmB, IN3, IN4, speed, stat)
  

# GPIO 모드 설정 
GPIO.setmode(GPIO.BCM)
      
#모터 핀 설정
#핀 설정후 PWM 핸들 얻어옴 
pwmA = setPinConfig(ENA, IN1, IN2)
pwmB = setPinConfig(ENB, IN3, IN4)

    
#제어 시작

# 앞으로 80프로 속도로
setMotor(CH1, 80, FORWARD)
setMotor(CH2, 80, FORWARD)
#5초 대기
sleep(5)

# 뒤로 40프로 속도로
setMotor(CH1, 40, BACKWORD)
setMotor(CH2, 40, BACKWORD)
sleep(5)

# 뒤로 100프로 속도로
setMotor(CH1, 100, BACKWORD)
setMotor(CH2, 100, BACKWORD)
sleep(5)

#정지 
setMotor(CH1, 80, STOP)
setMotor(CH2, 80, STOP)

# 종료
GPIO.cleanup()
```

![image](https://user-images.githubusercontent.com/30430227/178647935-6b1c81bd-ad20-4e55-ab2a-b9933a13a105.png)

![image](https://user-images.githubusercontent.com/30430227/178647340-0b8717bf-dd79-47be-a220-2e2156b71436.png)

![image](https://user-images.githubusercontent.com/30430227/178651226-e90b5df7-b9fc-400d-a9c9-3d8f62b9abfa.png)
![image](https://user-images.githubusercontent.com/30430227/178651285-31a76dd5-ae9e-4596-a93f-fce01a6d94f3.png)

```
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM) #모듈번호 BCM 모드
GPIO.setwarnings(False) #실행 시  경고 뜨는 경우 이 라인 추가

TRIG = 23
ECHO = 24
print('초음파 거리 측정기')

GPIO.setup(TRIG, GPIO.OUT)
GPIO.setup(ECHO, GPIO.IN) # 라즈베리파이는 입력 전압이 3.3V 이하라야한다

GPIO.output(TRIG,False)
print('초음파 출력 초기화')
time.sleep(2)

try:
    while True:
        GPIO.output(TRIG, True)
        time.sleep(0.0001) # 10uS의 펄스 발생을 위한 딜레이, 초단위(아두이노의 delay는 ms)
        GPIO.output(TRIG, False)

        while GPIO.input(ECHO)==0:
            start = time.time() # Echo핀 상승 시간값 저장

        while GPIO.input(ECHO)==1:
            stop = time.time() # Echo핀 하강 시간값 저장

        check_time = stop - start
        distance = check_time * 34300/2
        print('Distance : %.1f cm'%distance)
        time.sleep(0.4)

except KeyboardInterrupt: # Ctrl-C
    print('거리 측정 완료')
    GPIO.cleanup()
```


```
# 30센티 보다 가까우면 모터 작동

import RPi.GPIO as GPIO
from time import sleep, time

GPIO.setmode(GPIO.BCM) #모듈번호 BCM 모드
GPIO.setwarnings(False) #실행 시  경고 뜨는 경우 이 라인 추가

TRIG = 23
ECHO = 24
print('초음파 거리 측정기')

# 모터 상태
STOP =0
FORWARD =1
BACKWARD =2

HIGH =1
LOW =0

ENA = 17
INA = 27
INB = 22

# 핀 설정
def setPinConfig():
    GPIO.setup(TRIG, GPIO.OUT) # 거리센서 핀 설정
    GPIO.setup(ECHO, GPIO.IN) # 라즈베리파이는 입력 전압이 3.3V 이하라야한다

    GPIO.setup(ENA,GPIO.OUT) # 모터 핀 설정
    GPIO.setup(INA,GPIO.OUT)
    GPIO.setup(INB,GPIO.OUT)
    pwm = GPIO.PWM(ENA, 100)
    pwm.start(0)

    GPIO.output(TRIG,False)
    print('초음파 출력 초기화')
    sleep(2)

    return pwm

# 모터 제어 함수
def setMotorControl(pwm,speed,stat):
    pwm.ChangeDutyCycle(speed)

    if stat == FORWARD:
        GPIO.output(INA,HIGH)
        GPIO.output(INB,LOW)
    elif stat == BACKWARD:
        GPIO.output(INA,LOW)
        GPIO.output(INB,HIGH)
    elif stat == STOP:
        GPIO.output(INA,LOW)
        GPIO.output(INB,LOW)

GPIO.setmode(GPIO.BCM)

pwm = setPinConfig()

try:
    while True:
        GPIO.output(TRIG, True)
        sleep(0.0001) # 10uS의 펄스 발생을 위한 딜레이
        GPIO.output(TRIG, False)

        while GPIO.input(ECHO)==0:
            start = time() # Echo핀 상승 시간값 저장

        while GPIO.input(ECHO)==1:
            stop = time() # Echo핀 하강 시간값 저장

        check_time = stop - start
        distance = check_time * 34300/2

        if distance > 30:
            setMotorControl(pwm, 80, STOP)
        else:
            setMotorControl(pwm, 40,FORWARD)

        print('Distance : %.1f cm'%distance)
        sleep(1)

except KeyboardInterrupt: # Ctrl-C
    print('거리 측정 완료')
    GPIO.cleanup()
```


아두이노 메가 업로드 오류
-----------------------

![image](https://user-images.githubusercontent.com/30430227/187345589-35272285-cc00-4db8-857b-4191a7155696.png)

`보드의 리셋버튼 누름`
