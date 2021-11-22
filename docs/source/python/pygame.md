PYGAME
==========

> // 연산 - 나눈 후 소수점 이하 버림

1. 방향키로 이미지 제어하기

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

