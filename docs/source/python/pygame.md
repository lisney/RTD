PYGAME
==========

> // 연산 - 나눈 후 소수점 이하 버림

<br>

웹캠 열기 
-----------

![image](https://user-images.githubusercontent.com/30430227/142824557-d59988dc-c83a-47c9-b5d1-4c16550e4abe.png)

```
import pygame.camera
import pygame.image
import sys

pygame.camera.init()

cameras = pygame.camera.list_cameras()

#  print "Using camera %s ..." % cameras[0]

webcam = pygame.camera.Camera(cameras[0])

webcam.start()

 # grab first frame
img = webcam.get_image()

WIDTH = img.get_width()
HEIGHT = img.get_height()

screen = pygame.display.set_mode( ( WIDTH, HEIGHT ) )
pygame.display.set_caption("pyGame Camera View")

while True :
    for e in pygame.event.get() :
        if e.type == pygame.QUIT :
            sys.exit()

     # draw frame
    screen.blit(img, (0,0))
    pygame.display.flip()
     # grab next frame    
    img = webcam.get_image()
```

사과 피하기 
-----------------

1. 방향키로 사기리 제어하기

```
import pygame

pygame.init()
screen = pygame.display.set_mode((600,800))
clock = pygame.time.Clock()
pygame.key.set_repeat(500,30) #키보드 반복 .5초 후에 시작 .03초 단위로 반복

girl_load = pygame.image.load('python/4g2.jpg')
girl_image = pygame.transform.scale(girl_load,(100,100))

girl_rect = girl_image.get_rect()
girl_rect.centerx = 300
girl_rect.bottom = 800

while True:
    screen.fill((0,25,55))

    event = pygame.event.poll()

    if event.type == pygame.QUIT:
        break
    elif event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LEFT:
            girl_rect.left -= 5
            
        elif event.key == pygame.K_RIGHT:
            girl_rect.left += 5
            
    if girl_rect.left < 0:
        girl_rect.left = 0
    elif girl_rect.right > 600:
        girl_rect.right = 600
            
    screen.blit(girl_image, girl_rect)
    
    pygame.display.update()
    clock.tick(30)

pygame.quit()

```

<br>

2. 사과 떨어트리기

![image](https://user-images.githubusercontent.com/30430227/142822746-3b95d5f0-b0d7-47be-934a-673c47715962.png)

```
import pygame
import random

pygame.init()
screen = pygame.display.set_mode((600,800))
clock = pygame.time.Clock()
pygame.key.set_repeat(500,30)

# 점수
small_font = pygame.font.SysFont('malgungothic', 36)
score =0

# 소녀
girl_load = pygame.image.load('python/4g2.jpg')
girl_scale = pygame.transform.scale(girl_load,(100,100))

girl = girl_scale.get_rect()
girl.centerx = 300
girl.bottom = 800

# 폭탄
apple_load = pygame.image.load('python/apple.png')
apple_scale = pygame.transform.scale(apple_load,(100,100))

apples = []

for i in range(3):
    apple = apple_scale.get_rect(top=-100)
    apple.left = random.randint(0, 600 - apple.width)
    apples.append(apple)

while True:
    screen.fill((0,25,55))

    event = pygame.event.poll()

    if event.type == pygame.QUIT:
        break
    elif event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LEFT:
            girl.left -= 5
            
        elif event.key == pygame.K_RIGHT:
            girl.left += 5
            
    if girl.left < 0:
        girl.left = 0
    elif girl.right > 600:
        girl.right = 600
        
    for apple in apples:
        apple.top += 5
        if apple.top > 800:
            apples.remove(apple)
            apple = apple_scale.get_rect(left=random.randint(0,600-apple.width), top =-100)
            # apple.left = random.randint(0,600-apple.width)
            # apple.top = -100
            apples.append(apple)
            score += 1
            
    screen.blit(girl_scale, girl)
    
    for apple in apples:
        screen.blit(apple_scale, apple)
        
    score_image = small_font.render(f"점수 {score}", True,(255,255,0))
    screen.blit(score_image,(10,10))
    
    pygame.display.update()
    clock.tick(30)

pygame.quit()

```


