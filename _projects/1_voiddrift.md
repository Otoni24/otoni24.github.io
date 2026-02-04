---
layout: post
title: "Void Drifter"
description: "A SFML C++ project that uses a custom Level Editor"
tags: [C++, SFML, Box2D]
github_link: "https://github.com/Otoni24/VoidDrift"
---

# Description

`VoidDrift` is a simple 2D game developed as a personal educational project. The primary goal was to learn C++ and understand the fundamentals of game development without relying on a commercial engine.

The game is a basic but complete arcade experience, featuring 3 levels, built entirely from scratch.

-----

## Features

  * **Custom Framework:** Built from the ground up using C++17 and [SFML](https://github.com/SFML/SFML) for rendering, window management, audio, and input.
  * **Physics-Based Gameplay:** Uses [Box2D](https://github.com/erincatto/box2d) for all physics simulations and collision handling.
  * **Custom Levels:** Includes 3 unique levels created with a dedicated editor.
  * **Level Loading:** Levels are loaded from external `.json` files, parsed via the `VoidLevelLoader` library.

-----

## Project Context

This game is an executable and serves as a personal portfolio piece. The goal is not distribution, but rather to demonstrate the skills acquired in "engine-less" development.

### Dedicated Level Editor

All levels in `VoidDrift` were created using a dedicated, standalone 2D editor also developed for this project: **[VoidLevelEditor](https://github.com/Otoni24/VoidLevelEditor)**.

This editor (built with ImGui and SFML) handles asset placement and hitbox generation, exporting the data into a `.json` format that this game consumes.

To load the exported `.json` levels, `VoidDrift` uses the companion library `VoidLevelLoader`.