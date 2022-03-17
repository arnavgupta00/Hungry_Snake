from turtle import circle, width
import pygame
import random
pygame.init()

#Colors
White = (255,255,255)
Gray = (163, 154, 153)
Reddish = (222, 152, 144)

# Screen Size
screen_size = (1280,720)
(s_width,s_height) = screen_size

#Variables

pos_c = (70,70)
(x_cor,y_cor) = pos_c
radius_c = 30
fps = 30 
d_move = 20 
v_move = (0,0)
(v_x ,v_y) = v_move
clock = pygame.time.Clock()
my_list = []
total_length = 1


score = 0 
food_x= random.randint(0,s_width)
food_y= random.randint(0,s_height)
font_score = pygame.font.SysFont(None,30 )
font_credits = pygame.font.SysFont(None,100 )

def screen_text(text,color,x,y):
    text_on_screen = font_score.render(text,True,color)
    gamewindow.blit(text_on_screen,[x,y])

def screen_text_credits(text,color,x,y):
    text_on_screen = font_credits.render(text,True,color)
    gamewindow.blit(text_on_screen,[x,y])




gamewindow = pygame.display.set_mode(screen_size)
pygame.display.set_caption("Hungry Snake")
pygame.display.update()


#game specific varible

exit_game = False
game_over = False


#Functions

def circle_placer(gamewindow,Reddish,my_list,radius_c):
    for x,y in my_list:

        pygame.draw.circle(gamewindow,Reddish,[x,y],radius_c)

    


#game loop 

while not exit_game:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            exit_game = True

        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_d:
                v_x =  d_move
                v_y = 0
            if event.key == pygame.K_a:
                v_x = -d_move
                v_y = 0 
            if event.key == pygame.K_s:
                v_y = d_move
                v_x = 0
            if event.key == pygame.K_w:
                v_y = -d_move
                v_x = 0 
            if event.key == pygame.K_SPACE:
                v_y= 0 
                v_x = 0
            if event.key == pygame.K_l:
                total_length = 1
                my_list = []
                x_cor = 70
                y_cor = 70 
                v_y= 0 
                v_x = 0
                score = 0
            
    
    x_cor += v_x
    y_cor += v_y

    if x_cor > 1300 or x_cor < -20 or y_cor > 740 or y_cor < -20:
        total_length = 1
        my_list = []
        x_cor = 70
        y_cor = 70 
        v_y= 0 
        v_x = 0
        score = 0

    if abs(x_cor - food_x)<20 and abs(y_cor - food_y) <20:
        score += 10
        food_x= random.randint(0,s_width)
        food_y= random.randint(0,s_height)
        total_length += 1
   
    initial_circle = [] 
    initial_circle.append(x_cor)
    initial_circle.append(y_cor)     
    my_list.append(initial_circle)    


    gamewindow.fill(Gray)
    screen_text(f'Score: {score}',Reddish,5,5)
    screen_text('Reset: L',Reddish,1140,5)
    screen_text('Pause: Space',Reddish,1140,40)
    screen_text('Credits: Ctrl',Reddish,1140,700)
    pygame.draw.circle(gamewindow,White,[food_x,food_y],5)

    if len(my_list)>total_length:
        del my_list[0]
    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LCTRL or event.key == pygame.K_RCTRL:
            screen_text_credits('By: Arnav Gupta',Reddish,70,460)
            screen_text_credits('Contact: arnavguptagg@gmail.com',Reddish,70,600)
        
    #pygame.draw.circle(gamewindow,Reddish,[x_cor,y_cor],radius_c)
    circle_placer(gamewindow,Reddish,my_list,radius_c)
    
    pygame.display.update()
    clock.tick(fps)


pygame.quit()
