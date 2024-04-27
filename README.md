# labitint
import pygame
win_width = 1200
win_height = 700
window = pygame.display.set_mode((win_width,win_height))
pygame.display.set_caption("Лабіринт")
game = True

FPS =pygame.time.Clock()


class Settings():
    def __init__(self,image,x,y,w,h):
        self.image = pygame.transform.scale(pygame.image.load(image),(w,h))
        self.rect = self.image.get_rect()
        self.rect.x = x
        self.rect.y = y

    def draw(self):
        window.blit(self.image,(self.rect.x,self.rect.y))


fon = Settings("fon.png",0,0,win_width,win_height)
pygame.mixer.init()
pygame.mixer.music.load("music.mp3")
pygame.mixer.music.play(-1)

while game:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game = False

    fon.draw()
    pygame.display.flip()
    FPS.tick(60)
