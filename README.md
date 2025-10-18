import pygame
pygame.init()

WHITE = (0, 0, 0)
RED = (0, 0, 255)
BLUE = (0, 255, 0)
GREEN = (255, 0, 0)
window = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Cat_dance")

clock = pygame.time.Clock()

class Cat:
    def __init__(self, x, y, width, height, images):
        self.images = [pygame.transform.scale(pygame.images.load(img), (width, height)) for img in images]
        self.speed = 0.05
        self.block = self.images[0].get_rect(topleft=(x, y))
        self.index = 0
        self.current_image = self.images[0]

    def show(self):
        window.blit(self.current_image, (self.block.x, self.block.y))

images = [f"dance-cat-(i).png" for i in range(1, 3)]
cat = Cat(300, 200, 100, 200, images)



game = True
while game:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game = False
    window.fill(WHITE)
    cat.show()

    pygame.quit()
    clock.tick(60)

pygame.quit()
