PYGAME
==========

> // 연산 - 나눈 후 소수점 이하 버림

1. 방향키로 이미지 제어하기

```
import pygame

pygame.init()

screen = pygame.display.set_mode((600,800))
clock = pygame.time.Clock()

girl_image = pygame.image.load("python/4g2.jpg")
girl_scale = pygame.transform.scale(girl_image, (100,100))

girl = girl_scale.get_rect()  #girl 객체
# girl = girl_scale.get_rect(centerx=300, bottom=800)  #키워드 인수
girl.centerx = 300
girl.bottom = 800

while True:
    screen.fill((0,0,0))

    event = pygame.event.poll()

    if event.type == pygame.QUIT:
        break
    elif event.type == pygame.KEYDOWN:
        if event.key ==pygame.K_LEFT:
            girl.left -= 5
        elif event.key ==pygame.K_RIGHT:
            girl.left += 5
            
    screen.blit(girl_scale, girl)

    pygame.display.update()
    clock.tick(30)

pygame.quit()
```

