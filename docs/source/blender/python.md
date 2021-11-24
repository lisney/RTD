Python
==========

VSCode
-----------------------

1. 개발자 Extension 설치 

![image](https://user-images.githubusercontent.com/30430227/143177111-c9d7668f-26ae-4932-96b4-cf51fb679de7.png)

2. Ctrl - Shift - P

`Blender: New Addon 실행`

![image](https://user-images.githubusercontent.com/30430227/143177427-37f0aef2-babf-4d45-bc3e-4479abd1da35.png)

`블렌더 Addon/Script 폴더에 새폴더를 생성하고 선택한다`

3. VSCode 에서 생성한 폴더를 연다

![image](https://user-images.githubusercontent.com/30430227/143178015-b7293fca-e93f-4ab6-9fdd-11df9df93d2e.png)

`__init__.py`

![image](https://user-images.githubusercontent.com/30430227/143178095-5b29430d-8f22-49d8-bd78-e97a6b1aa092.png)

4. Blender Start

![image](https://user-images.githubusercontent.com/30430227/143178232-c0eddc37-3f5d-4240-b084-213a6062ffd2.png)

---------

5. 그냥 블렌더 실행시키고 .py파일 연다

`VSCode에서 편집하고 블렌더에서 파일 갱신하면 된다`

<br>

자동완성 세팅 
-------------

`blender_autocomplete-master.zip 다운`

![image](https://user-images.githubusercontent.com/30430227/143220970-d00f75ca-2ba7-4aee-af20-517c394d0e1e.png)

`작업 폴더 생성 > 라이브러리 풀기 > VSCode 에서 Open Folder`

![image](https://user-images.githubusercontent.com/30430227/143221230-38deef53-99f6-4aa1-bcf0-b9dce1303404.png)
![image](https://user-images.githubusercontent.com/30430227/143221196-739b449e-6e88-4bd8-a474-597eece0de0d.png)

`.Vscode 폴더(닫았다 열면 자동생성?) setting.json`

![image](https://user-images.githubusercontent.com/30430227/143221398-c7b95e44-a405-4e23-894f-8fa0e300e31c.png)

![image](https://user-images.githubusercontent.com/30430227/143221654-f4b0cc43-2b37-418d-a4d1-c05b4a11b2a7.png)

```
"python.autoComplete.extraPaths": [
     "d:\\my_project\\blender_autocomplete\\2.90",
     "_PATH_TO_BLENDER_\\2.90\\scripts\\modules",
]

_PATH_TO_BLENDER_ 블렌더 설치 패스
```

`추가 - 파이썬 맞춤법 검사기? > Shift - Ctrl - P > Pyline 선택`

![image](https://user-images.githubusercontent.com/30430227/143222173-f50c90af-b4b3-44b7-8ff5-9b2b63c6959f.png)







