Video Editing
===============

Sequencer 
----------------------

1. Split (단축키 지정: 3)  

```
자를 때 마우스 포인트 위치가 타임인디케이터 좌측이면 좌측 클립이 자동 선택됨
Hold Split 절단 위치 이미지 홀드
Tool패널의 Blade면도칼 단축키 해제할 것 (Remove ShortCut)

Ctrl-Wheel(타임라인 이동), Alt - Wheel(PlayHead 이동)
Ctrl-Click(세로 전체 선택), Alt-Click(Mute Toggle)

Image > Scale to Fit(전체가 화면에 맞춤), Scale to Fill(이미지 잘라서 맞춤), Stretch(가로세로비 무시 맞춤)
View > Navigation > Jump to Previous Strip - PageUp 세팅
PlayHead 위치의 클립 선택 - 2(Select>Side of Frame>Current Frame), 3(Strip>Split)
, 4(Erase Strip), 5(Remove All Gap), 1(Add Gap), 스트랩 확장: 스트랩 선택 > 'e'
Effect Strip 복사 -  이팩트 Dup 'D' > 대상 선택, 복사한 이팩트 선택 'R' - Reassign Input: 
정지화면(Hold/Freeze Frame) - Effect Strip > Speed > Frame Number or Multiply => 0

선택한 클립 PlayHead 위치로 이동 - Shift-s(Strip>Transform>Snap Strips to the Current Frame
선택한 클립을 랜더 영역으로 View>Range>Set Frame Range to Strips - 단축키 지정 '\'
선택한 클립의 해상도로 랜더 해상도 맞춤 - Strip>Movie Strip>Set Render Size

Preference > Navigation >Zoom to Mouse Position 체크

Ctrl - M : Render Animation
```

2. Frame Selected (NumpadPeriod)  

3. Frame All (Home - 단축키 안먹힐 때 체크해제 > 다시 체크)  

4. Jump to Previous Strip (PageDown -> Up Key로 바꾼다)  
`Up key 는 기존 keyframe 이동단축키로 설정되어 있는데 이를 끈다`  

5. 작업영역 Range(Frame, Rander)  
`Set Preview Range 단축키 지정 'p'(타임라인 에디터에서도 작동된다)`  
![image](https://user-images.githubusercontent.com/30430227/137090165-cd93dd8a-d48f-4dd6-adb0-1d879dce67af.png)  

6. Show Seconds/frame Toggle (Ctrl-T)  

7. Slip Strip (s 공중 드래그) - 정지화면 생성?
`shift + s Snap Strips to the Current Frame`  

8. Remove Gaps (Backspace)  
`한방에 전체 갭 삭제 Shift - Backspace -> 단축키 바꿈: 5`
`Insert Gap 단축키 지정: 1`

9. 선택한 클립의 해상도를 랜더해상도로 바꿈 Set Render Size 
![image](https://user-images.githubusercontent.com/30430227/137072813-3d788639-7703-4b4c-9959-c3a6d8bee442.png)  

10. Lock Strips (Shift-L)  
`Unlock Alt + Shift - L`  

11. Mute/Unmute Strips H, Alt-H  

12. Add Fade/Clear Fade  
![image](https://user-images.githubusercontent.com/30430227/137073202-9cf68a07-203d-4cff-a1a4-2f4607bfcb2b.png)  

13. Meta Strips(GROUP)  
`Make Meta Strip (Ctrl-G), UnMeta Strip (Ctrl-Alt-G)`  

14. Proxy  
`시퀀스 프리뷰 사이드패널`  
![image](https://user-images.githubusercontent.com/30430227/137074894-9ade0600-7284-4e14-b0e8-1b50cf145ce6.png)  

`Proxy Settings 기본적으로 클립 폴더에 저장되나 별도 폴더에 저장, 파일 사용`  

![image](https://user-images.githubusercontent.com/30430227/137075264-632ca7e7-278e-4fec-ad77-414c1e3fcc5f.png)  


15. Modifier Copy(단축키 설정 Alt - L)  
`대상 먼저 선택 후  선택한다`  
![image](https://user-images.githubusercontent.com/30430227/137083928-c2367dd1-721e-4a9a-a990-0a68d62f2ef9.png)  

16. Mask  
`랜더 해상도로 바꿈 Image Editor > Mask 모드 > Render REsult 선택 `  
![image](https://user-images.githubusercontent.com/30430227/137091324-f54f9fcd-daf9-4979-ba7d-20cfe24c938a.png)  

`랜더 시 별도 창이 안뜨게  Preferences > Interface > Editors > Temporary Editors`  
![image](https://user-images.githubusercontent.com/30430227/137091855-4bc7a7e3-d33b-4cd3-986c-a0b8789e5a8b.png)  

`Add Square > 'B' 포인트 선택, Alt - S 페더, Ctrl -클릭 포인트 추가, 'V' 베지어 핸들`  

![image](https://user-images.githubusercontent.com/30430227/137093521-008e304b-5119-4468-a017-43b575834b81.png)  
![image](https://user-images.githubusercontent.com/30430227/137093881-6633229e-36d0-4af6-8f8b-463039dcb068.png)  

17. Select > Side of Frame > Current Frame

`단축키 지정: 2`
`select > Channel 단축키 지정: ~`

18. Swap Strips -좌/우 클립과 교체

`Alt - L/R Arrow`

19. Transform Mode

`상단 가운데 위치`

![image](https://user-images.githubusercontent.com/30430227/140476168-21d5090d-7a3d-47ff-8c09-47b91a493e0f.png)

20. Playback Jump to Endpoint

`단축키 지정: Shift - Alt - L/R Arrow`

![image](https://user-images.githubusercontent.com/30430227/140483461-de4ac690-b31d-4a1c-8ca0-9af9b5d4d32c.png)

<br>

Power Sequencer
------------------

1. Concatenate - 사슬같이 잇다

`shift - C 한 채널의 모든 갭을 없앤다`

2. Speed

`Space(Play) > Ctrl - 1/2/3/4/5`
`스피드 단축키 , .`
