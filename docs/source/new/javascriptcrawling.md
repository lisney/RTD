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

# 박스 설치 (username	root, password	vagrant)
vagrant up

# 박스 제거
vagrant box remove centos/7
```
![image](https://user-images.githubusercontent.com/30430227/175857825-1e7b781a-398b-4184-80c1-702f6bfe38c9.png)

`가상머신 접근 - vagrant ssh `

![image](https://user-images.githubusercontent.com/30430227/175857962-b676aea6-9b3e-4ef7-be83-33199d3d0cdc.png)

```
# 가상머신 실행
> vagrant up --provider virtualbox //--provider vir...부분 없이도 실행 되는지?

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
# 다음 설정 시 Vagrant ssh 가 실행되지 않는다...해결안됨!!
  # 가상머신의 80포트를 호스트머신의 8080 포트에 할당함
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # 가상머신의 IP를 아래 설정한 IP주소에 할당함
  config.vm.network "private_network", ip: "192.168.33.10"
```


NodeJS설치
------------

1. nvm 설치 - nodejs 설치(여러버전을 관리할 수 있다. nvm activate, deactivate

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`

`로그아웃>로그인`

`mkdir ~/.nvm // nvm이 사용할 디렉토리 생성, ~ 홈디렉토리`

`nvm ls 혹은 nvm list //설치된 노드 버전 리스트 보기 *표가 있는 것이 현재 사용하는 버전이다`

`nvm use 버전 //사용하기, 숫자 정수부분`


```
# nvm 제거
vi ~/.bashrc 로 들어가 아래 내용 삭제 후 저장

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

rm -rf ~/.nvm 

후 재시동
```

2. nvm install node 16 //안정화 버전

3. 환경변수 수정 - sudoers 파일 수정

`sudo visudo`

```
간단한 vi 명령어
  편집 : 수정할 위치에서 i키 입력 후 수정
  저장하고 빠져나오기 : 편집이 완료되면 esc키를 누른 후 :wq를 누름 
  저장없이 빠저나오기 : esc키를 클릭 후 :q를 누름

# 수정내용
#######################################
## env_reset를 무효화 처리  
######################################
# Defaults   env_reset
Defaults    !env_reset


######################################
## HOME을 사용할 수 있게 주석 제거 처리
######################################
# Defaults   env_keep += "HOME"
Defaults   env_keep += "HOME"

```

 VSCode 설치
 --------------
 
 ```
 # 슈퍼 유저로 들어가 (sudo -i//바로들어감)
 [be-jerry@localhost ~]$ su
 -암호 : 
 
 # Nano Editor 설치
 nano /etc/yum.repos.d/vscode.repo
 
 # Start by importing the Microsoft GPG key
 rpm --import https://packages.microsoft.com/keys/microsoft.asc
 
 # create the following repo file to enable the Visual Studio Code repository
 nano /etc/yum.repos.d/vscode.repo
 
 # Paste the following content into the file:
 [code]
name=Visual Studio Code
baseurl=https://packages.microsoft.com/yumrepos/vscode
enabled=1
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc

# install the latest version of Visual Studio Code
yum install code

# super에서 나온exit 후 실행
exit

code

* Yum은 Yellow dog - Update RPM 설치를 개선하기 위해 개발한 패키지 관리자

 ```
