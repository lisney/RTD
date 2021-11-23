PYGAME
==========

> // 연산 - 나눈 후 소수점 이하 버림

<br>


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
<br>

사기리 클릭 게임 
-------------------

![image](https://user-images.githubusercontent.com/30430227/142984277-28211742-f1ea-49df-acc2-5a57dc874871.png)

1. 랜덤 위치 클릭 - 마우스 호버

```
import pygame
import random

pygame.init()
screen = pygame.display.set_mode((600, 800))
clock = pygame.time.Clock()

BLACK = 0,0,0

image_load = pygame.image.load('python/4g2.jpg')
image_scale = pygame.transform.scale(image_load,(94,94))
images =[]

rand_x = [0,1,2,3,4,5]
rand_y = [0,1,2,3,4,5,6,7]

for i in range(7):
    image = image_scale.get_rect()
    image.left = (image_scale.get_width()+6) * random.choice(rand_x)
    image.top = (image_scale.get_height()+6) * random.choice(rand_y)
    images.append(image)


while True:
    screen.fill(BLACK)

    event = pygame.event.poll()
    if event.type == pygame.QUIT:
        break
    elif event.type == pygame.MOUSEBUTTONDOWN:
        print(event.pos)
        for i,image in enumerate(images):
            if image.collidepoint(event.pos):
                print(f"{i}번 사기리")
                print(image)
                
    elif event.type == pygame.MOUSEMOTION:
        pygame.mouse.set_system_cursor(pygame.SYSTEM_CURSOR_ARROW)
        for image in images:
            if image.collidepoint(event.pos):
                pygame.mouse.set_system_cursor(pygame.SYSTEM_CURSOR_HAND)
        
    
    for image in images:
        screen.blit(image_scale, image)
        
        
    pygame.display.update()
    clock.tick(30)

pygame.quit()
```

<br>

2. 


참고 
------

1. 이미지 드랙 

```
# Python program to move the image
# with the mouse

# Import the library pygame
import pygame
from pygame.locals import *

# Take colors input
YELLOW = (255, 255, 0)
BLUE = (0, 0, 255)

# Construct the GUI game
pygame.init()

# Set dimensions of game GUI
w, h = 640, 350
screen = pygame.display.set_mode((w, h))

# Take image as input
img = pygame.image.load('geek.jpg')
img.convert()

# Draw rectangle around the image
rect = img.get_rect()
rect.center = w//2, h//2

# Set running and moving values
running = True
moving = False

# Setting what happens when game
# is in running sate
while running:
	
	for event in pygame.event.get():

		# Close if the user quits the
		# game
		if event.type == QUIT:
			running = False

		# Making the image move
		elif event.type == MOUSEBUTTONDOWN:
			if rect.collidepoint(event.pos):
				moving = True

		# Set moving as False if you want
		# to move the image only with the
		# mouse click
		# Set moving as True if you want
		# to move the image without the
		# mouse click
		elif event.type == MOUSEBUTTONUP:
			moving = False

		# Make your image move continuously
		elif event.type == MOUSEMOTION and moving:
			rect.move_ip(event.rel)

	# Set screen color and image on screen
	screen.fill(YELLOW)
	screen.blit(img, rect)

	# Construct the border to the image
	pygame.draw.rect(screen, BLUE, rect, 2)

	# Update the GUI pygame
	pygame.display.update()

# Quit the GUI game
pygame.quit()

```

<br>

2. 텍스트상자 

```
import pygame as pg


pg.init()
screen = pg.display.set_mode((640, 480))
COLOR_INACTIVE = pg.Color('lightskyblue3')
COLOR_ACTIVE = pg.Color('dodgerblue2')
FONT = pg.font.Font(None, 32)


class InputBox:

    def __init__(self, x, y, w, h, text=''):
        self.rect = pg.Rect(x, y, w, h)
        self.color = COLOR_INACTIVE
        self.text = text
        self.txt_surface = FONT.render(text, True, self.color)
        self.active = False

    def handle_event(self, event):
        if event.type == pg.MOUSEBUTTONDOWN:
            # If the user clicked on the input_box rect.
            if self.rect.collidepoint(event.pos):
                # Toggle the active variable.
                self.active = not self.active
            else:
                self.active = False
            # Change the current color of the input box.
            self.color = COLOR_ACTIVE if self.active else COLOR_INACTIVE
        if event.type == pg.KEYDOWN:
            if self.active:
                if event.key == pg.K_RETURN:
                    print(self.text)
                    self.text = ''
                elif event.key == pg.K_BACKSPACE:
                    self.text = self.text[:-1]
                else:
                    self.text += event.unicode
                # Re-render the text.
                self.txt_surface = FONT.render(self.text, True, self.color)

    def update(self):
        # Resize the box if the text is too long.
        width = max(200, self.txt_surface.get_width()+10)
        self.rect.w = width

    def draw(self, screen):
        # Blit the text.
        screen.blit(self.txt_surface, (self.rect.x+5, self.rect.y+5))
        # Blit the rect.
        pg.draw.rect(screen, self.color, self.rect, 2)



def main():
    clock = pg.time.Clock()
    input_box1 = InputBox(100, 100, 140, 32)
    input_box2 = InputBox(100, 300, 140, 32)
    input_boxes = [input_box1, input_box2]
    done = False

    while not done:
        for event in pg.event.get():
            if event.type == pg.QUIT:
                done = True
            for box in input_boxes:
                box.handle_event(event)

        for box in input_boxes:
            box.update()

        screen.fill((30, 30, 30))
        for box in input_boxes:
            box.draw(screen)

        pg.display.flip()
        clock.tick(30)


if __name__ == '__main__':
    main()
    pg.quit()
```

<

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

