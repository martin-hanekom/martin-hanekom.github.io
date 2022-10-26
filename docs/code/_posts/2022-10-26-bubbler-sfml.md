---
layout: code
permalink: /code/bubbler+sfml
title: Bubbler C++/SFML game
author: Martin Hanekom
githublink: https://github.com/martin-hanekom/bubbler
#img: "peanut-butter-oats.jpg"
---

This tutorial will walk through the design and implementation of a simple 2D 2D zombie shooter game called Bubbler, written in [C++](https://en.cppreference.com/w/) with [SFML](https://www.sfml-dev.org/index.php). Before continuing, install a suitable C++ compiler (GCC, CMake) and the SFML library.

## Game concept

Before we jump into the code, let's take a moment to discuss what we want to do. The game will consist of a single player with a gun, shooting and running away from and endless swarm of "bubbles" that slowly move closer to the player. The player shoots with a limited amount of bullets that can be restocked from spoils obtained from popping bubbles, as well as by expensive, but devastating grenades. Everything is viewed from a top-down 2D plane.

<img src="/code/lib/bubbler.png" alt="Bubbler game screenshot" width="100%">

Trying to implement all the functionality at once will make it too complex, so we will progressively add features as follows:

* [Create the game loop](#game-loop)
* [Create the player with key movements](#player-with-key-movements)
* [Add player weapon with mouse movements](#weapon-with-mouse-movements)
* [Populate the field with bubbles](#bubbles)
* [Use and buy ammo](#ammo-shop)
* [Add waves and grenades](#waves-and-grenades)

## Game Loop

The core mechanic of every game is a game loop. In this section we will learn how to run an SFML game loop. Create a new C++ file called `main.cpp` in an empty folder with the following initialization code:

```cpp
#include <SFML/Graphics.hpp>

#define WIN_W 1600
#define WIN_H 900
#define FS 60

int main() {
  sf::RenderWindow window(sf::VideoMode(WIN_W, WIN_H), "Bubbler", sf::Style::Titlebar | sf::Style::Close);
  window.setVerticalSyncEnabled(true);
  window.setFramerateLimit(FS);

  while (window.isOpen()) {
    sf::Event event;
    while (window.pollEvent(event)) {
      switch (event.type) {
        case sf::Event::Closed:
          window.close();
          break;
        default:
          break;
      }
    }
    window.clear();
    window.display();
  }
  return 0;
}
```

## Player with Key Movements

## Weapon with Mouse Movements

## Bubbles

## Ammo Shop

## Waves and Grenades
