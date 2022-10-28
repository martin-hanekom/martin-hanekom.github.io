---
layout: code
permalink: /code/bubbler+sfml
title: Bubbler C++/SFML game
author: Martin Hanekom
githublink: https://github.com/martin-hanekom/bubbler
#img: "peanut-butter-oats.jpg"
---

This tutorial will walk through the design and implementation of a simple 2D zombie shooter game called Bubbler,
written in [C++](https://en.cppreference.com/w/) with [SFML](https://www.sfml-dev.org/index.php). However, instead
of Zombies we will be popping bubbles. Before continuing, install a suitable C++ compiler (GCC, CMake) and the
SFML library.

SFML is an extremely powerful, yet easy to use game engine, with native 2D shape rendering and OpenGL support.
We will use the builtin shapes to quickly and easily get the game going.

## Game concept

Before we jump into the code, let's take a moment to discuss what we want to do. The game will consist of a single
player with a gun, shooting and running away from and endless swarm of "bubbles" that slowly move closer to the player.
The player shoots with a limited amount of bullets that can be restocked from spoils obtained from popping bubbles,
as well as by expensive, but devastating grenades. Everything is viewed from a top-down 2D plane.

<img src="/code/lib/bubbler.png" alt="Bubbler game screenshot" width="100%">

Trying to implement all the functionality at once will make it too complex, so we will progressively add features as follows:

* [Create the game loop](#game-loop)
* [Create the player with key movements](#player-with-key-movements)
* [Add player weapon with mouse movements](#weapon-with-mouse-movements)
* [Populate the field with bubbles](#bubbles)
* [Use and buy ammo](#ammo-shop)
* [Add waves and grenades](#waves-and-grenades)

## Game Loop

The core mechanic of every game is a game loop. In this section we will learn how to run an SFML game loop. Create a new
C++ file called `main.cpp` in an empty folder with the following initialization code:

```
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

First we include the SFML graphics library. If this file is not found, it probably means SFML is not correctly installed or
not added to your PATH variable. In that case find the SFML install location and add it to the shell PATH.
On Linux this can be done with.

```
whereis SFML
export PATH=<SFML location>:PATH
```

However to add SFML permanently to your shell path, add the export line to `$HOME/.bashrc`.

Next we define the window size and framerate as constants. The window size will be used to check bounds later, so it is important
not to hardcode the value everywhere in the file, but only once at the start.

Next we define the `main` function, which is the program execution entrypoint in C++.
First we define the window, with the appropriate size, title and titlebar, then we enable vertical synchronization and set the framerate.
If the monitor refresh rate is out of sync with the game refresh, we might see glitches on the screen as a half updated gamestate is drawn.
Enabling vertical sync sets the game refresh rate to the monitor's and prevent the potential flicker.

`while (window.isOpen())` is the typical start of an application's game loop.
It will continuously execute the code in this block until the window closes, at the specified frame rate.
There are three main tasks which should be completed on each iteration of the game loop.

- process events
- update the game state
- draw all objects to the screen

## Player with Key Movements

## Weapon with Mouse Movements

## Bubbles

## Ammo Shop

## Waves and Grenades
