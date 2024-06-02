# joga-bola-en-ruby-e-python
promt4eks
_________________________________
RUBY

require 'gosu'

class GameWindow < Gosu::Window def initialize super 640, 480 self.caption = "Top Down Soccer Game"

 
@player = Player.new
@ball = Ball.new
@monsters = []
@rewards = []
@gate = Gate.new

@level = 1
end

def update @player.move @ball.move

 
if @player.collecting?(@ball)
  @ball.reset
end

@monsters.each do |monster|
  monster.move
  if @player.colliding?(monster)
    # Game over logic
  end
end

@rewards.each do |reward|
  if @player.collecting?(reward)
    @rewards.delete(reward)
  end
end

if @player.pass_through_gate?(@gate)
  @level += 1
  # Reset player position and generate new monsters, rewards, gate
end
end

def draw @player.draw @ball.draw @monsters.each { |monster| monster.draw } @rewards.each { |reward| reward.draw } @gate.draw end end

class Player def initialize @x = 320 @y = 240 end

def move # Implement movement logic end

def collecting?(object) # Implement collision detection logic end

def pass_through_gate?(gate) # Implement gate pass logic end

def draw # Draw player object end end

class Ball def initialize @x = rand(640) @y = rand(480) end

def reset @x = rand(640) @y = rand(480) end

def move # Implement random movement logic end

def draw # Draw ball object end end

class Monster def initialize @x = rand(640) @y = rand(480) end

def move # Implement monster movement logic end

def draw # Draw monster object end end

class Reward def initialize @x = rand(640) @y = rand(480) end

def draw # Draw reward object end end

class Gate def initialize @x = rand(640) @y = rand(480) end

def draw # Draw gate object end end

window = GameWindow.new window.show

______________________________________________

запитонировали мля....

import pygame import random

Инициализация pygame
pygame.init()

Создание окна
screen = pygame.display.set_mode((800, 600)) pygame.display.set_caption("Супер игра")

Цвета
WHITE = (255, 255, 255) RED = (255, 0, 0) YELLOW = (255, 255, 0)

Персонаж
player_image = pygame.image.load("player.png") player_x = 370 player_y = 480 player_x_change = 0 player_y_change = 0

def player(x, y): screen.blit(player_image, (x, y))

Мяч
ball_image = pygame.image.load("ball.png") ball_x = random.randint(0, 736) ball_y = random.randint(50, 150)

def ball(x, y): screen.blit(ball_image, (x, y))

Монстры
monster_image = pygame.image.load("monster.png") monster_x = random.randint(0, 736) monster_y = random.randint(50, 150)

def monster(x, y): screen.blit(monster_image, (x, y))

Награды
reward_image = pygame.image.load("reward.png") reward_x = random.randint(0, 736) reward_y = random.randint(50, 150)

def reward(x, y): screen.blit(reward_image, (x, y))

Игровой цикл
running = True while running: screen.fill(WHITE)

 
Копировать
for event in pygame.event.get():
    if event.type == pygame.QUIT:
        running = False

    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LEFT:
            player_x_change = -0.1
        if event.key == pygame.K_RIGHT:
            player_x_change = 0.1
        if event.key == pygame.K_UP:
            player_y_change = -0.1
        if event.key == pygame.K_DOWN:
            player_y_change = 0.1

    if event.type == pygame.KEYUP:
        if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
            player_x_change = 0
        if event.key == pygame.K_UP or event.key == pygame.K_DOWN:
            player_y_change = 0

player_x += player_x_change
player_y += player_y_change

# Ограничение игрового поля
if player_x < 0:
    player_x = 0
elif player_x > 736:
    player_x = 736
if player_y < 0:
    player_y = 0
elif player_y > 536:
    player_y = 536

player(player_x, player_y)
ball(ball_x, ball_y)
monster(monster_x, monster_y)
reward(reward_x, reward_y)

pygame.display.update()
