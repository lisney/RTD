PygameGUI
============

버튼 
-----

![image](https://user-images.githubusercontent.com/30430227/142989741-30eb8d67-1daa-4166-87c9-54044ca9ac79.png)

```
import pygame
import pygame_gui

pygame.init()

pygame.display.set_caption('Quick Start')
screen = pygame.display.set_mode((800,600))

cbox = pygame.Surface((100,200))
cbox.fill(pygame.Color('#ff0000'))

manager = pygame_gui.UIManager((800, 600))

hello_button = pygame_gui.elements.UIButton(relative_rect=pygame.Rect((350,275),(100,50)), text='Say Hello', manager=manager)

clock = pygame.time.Clock()

is_running = True

while is_running:
    time_delta = clock.tick(60)/1000.0
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            is_running = False
            
        if event.type ==pygame.USEREVENT:
            if event.user_type == pygame_gui.UI_BUTTON_PRESSED:
                if event.ui_element == hello_button:
                    print('Hello World!')
        manager.process_events(event)
        
    manager.update(time_delta)

    screen.fill(pygame.Color("#000000"))
        
    # screen.blit(cbox, (100,100))
    manager.draw_ui(screen)

    pygame.display.update()
        
pygame.quit()
```
