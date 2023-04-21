# STAG SPRINGDALE TEXT ADVENTURE GAME
# created 4/6/23

# 47 large M's fill entire input area. for future reference.
# still need icon

# PORT
import pygame, sys
from pygame.locals import QUIT
import pgzrun
import random
from blah import img

# --- CONSTANTS ---
# measurements
WIDTH = 400
HEIGHT = 250

# colours
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
GREY = (36, 36, 36)
RED = (255, 0, 0)
GREEN = (0, 255, 0)
BLUE = (0, 0, 255)

# images
#img = ['terro_img.png', 'other term', 'other other term']
icon = ['save_icon.png', 'inven_icon.png']
loc = ['terro_loc.png']

text = ['TERRO: Am I bugged? Haha…']

userIn = ''
font = pygame.font.SysFont('dejavusansmono', 11)
fontLarge = pygame.font.SysFont('dejavusansmono', 25)
fontSubscript = pygame.font.SysFont('dejavusansmono', 9)
print(pygame.font.get_fonts())

rectIn = pygame.Rect(50, 190, 140, 25)

scene = 0

# bool
done = False
typing = False

# text

# --SETUP--
pygame.init()
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption('STAG V0')
clock = pygame.time.Clock()
userColour = GREEN

# --- FUNCTIONS ---


# text funct
def drawText(text, font, textColour, x, y):
  txt = font.render(text, True, textColour)
  screen.blit(txt, (x, y))


# enemy load draw
def drawVil(i, x, y):
  vil = pygame.image.load('images/' + img[i])
  vil = pygame.transform.rotozoom(vil, 0, .5)
  screen.blit(vil, (x, y))


# background draw funct
def drawLoc(i, x, y):
  bg = pygame.image.load('images/' + loc[i])
  screen.blit(bg, (x, y))


def drawIcon(i, x, y):
  global icon
  box = pygame.image.load('images/' + icon[i])
  if (i == 0):
    box = pygame.transform.rotozoom(box, 0, .128)
  elif (i == 1):
    box = pygame.transform.rotozoom(box, 0, .2)
    #box = pygame.transform.threshold(255)
  screen.blit(box, (x, y))


def title():
  screen.fill(BLACK)
  drawText('STAG', fontLarge, (WHITE), 25, 170)
  drawText('v0', fontSubscript, (WHITE), 25, 195)


def gameplay():
  screen.fill(BLACK)
  drawLoc(0, 70, 50)
  drawVil(0, 125, 50)

  drawIcon(0, 340, 100)
  drawIcon(1, 333, 61)

  pygame.draw.rect(screen, userColour, rectIn)

  textSurf = font.render(userIn, True, (GREEN))

  screen.blit(textSurf, (rectIn.x + 5, rectIn.y + 5))

  rectIn.w = max(20, textSurf.get_width() + 10)
  #pygame.blit(currentText, (23, 23)) pygame.display.update()
  drawText(text[0], font, (WHITE), 25, 170)


# ~--- GAME LOOP ---~
while not done:

  clock.tick(60)  #fps

  for event in pygame.event.get():
    if event.type == QUIT:
      pygame.quit()
      sys.exit()

    if event.type == pygame.MOUSEBUTTONDOWN:
      if rectIn.collidepoint(event.pos):
        typing = True
      else:
        typing = False
        # the loop for checking typing bool

    if event.type == pygame.KEYDOWN:

      # delete characters from userIn string
      if event.key == pygame.K_BACKSPACE:
        userIn = userIn[:-1]

      # send user input
      if event.key == pygame.K_RETURN:
        print("\nuser pressed enter")
        print("last text inputted: " + userIn)
        userIn = ''

      else:
        userIn += event.unicode

    #screen.blit(userText, ())

  if (scene == 1):

    gameplay()
    #drawVil(0, 150, 50)

  elif (scene == 0):
    title()

  if typing:
    userColour = BLACK
  else:
    userColour = BLACK

  pygame.display.flip()

pygame.quit()
