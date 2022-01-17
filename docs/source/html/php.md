PHP
====

1. bitnami WAMP 설치 

`윈도우 환경 Path 에 등록`

![image](https://user-images.githubusercontent.com/30430227/149702592-dd000f72-e6e5-4a6c-8354-21e0042def11.png)

`VSCode Extensions`

![image](https://user-images.githubusercontent.com/30430227/149688036-983b3dc8-d59a-4164-8b25-50b95c670cc0.png)

<br>

2. 실행

![image](https://user-images.githubusercontent.com/30430227/149687744-2737f0e4-ece1-45de-92c5-9ce4f4b3b05f.png)

`VSCode > XAMPP/htdocs 내 폴더 생성 > Setting 'F1', 'user setting'검색, 'php'검색 >Edit Setting Json`

![image](https://user-images.githubusercontent.com/30430227/149702200-969d0d62-6bb6-4ddb-a3fa-0e8192646077.png)

![image](https://user-images.githubusercontent.com/30430227/149702318-eb79c18f-7069-488c-99b9-a974bf0764a1.png)

```
    ],
    "php.debug.executablePath":"C:\\php\\php.exe",
    "window.zoomLevel": 1
}
```

<br>

`tasks.json 생성`

```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "command": "chrome",

    "windows": {

    "command": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"

    },

 

    "args": ["localhost\\${workspaceRootFolderName}\\${fileBasename}"]

}
```

`서버 실행 > VSCode 'Ctrl-Shift-B'`

![image](https://user-images.githubusercontent.com/30430227/149702733-18a83a85-cf32-44d4-b4c5-c0fa39ae7a9b.png)

`서버 주소 바꾸기 > Config 버튼 > Listen 주소 입력-포트는 80으로 하면 주소창에 안보이게된다 > 서버 재시동 `

![image](https://user-images.githubusercontent.com/30430227/149762552-d7b3141c-8ddd-4ed7-abc7-eb4369045b0f.png)

![image](https://user-images.githubusercontent.com/30430227/149762572-52b00526-2451-429d-b60d-2c398a1455c6.png)



