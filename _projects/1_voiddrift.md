---
layout: post
title: "Void Drifter"
description: "A custom C++ arcade game with a dedicated Level Editor."
tags: [C++, SFML, Box2D, Tool Dev]
role: "Solo Developer"
engine: "Custom C++ / SFML"
date: 2025-06-01
github_link: "https://github.com/Otoni24/VoidDrift"
thumbnail: "/assets/images/cover_voiddrift.jpg"
header_video: "/assets/videos/sample.mp4"
youtube_id: "xfh6DdWcqMM"
---

VoidDrift is a 2D arcade game developed as a high-performance educational project. The primary goal was to master Modern C++ and understand the low-level fundamentals of game architecture without relying on a commercial engine like Unity or Unreal.

The game delivers a complete arcade experience, featuring 3 unique levels, physics-based movement, and a custom content pipeline.

## Technical Highlights

- **Custom Framework:** Built from the ground up using C++17 and [SFML](https://github.com/SFML/SFML) for rendering, window management, audio, and input handling.
- **Physics-Based Gameplay:** Integrated [Box2D](https://github.com/erincatto/box2d) directly into the game loop for precise physics simulations and dynamic collision resolution.
- **Data-Driven Design:** Levels are not hardcoded but loaded from external `.json` files, parsed via a custom `VoidLevelLoader` library.
- **Entity Component System:** Utilizes a lightweight architecture to manage game objects, separating logic from data for better scalability.

## Dedicated Level Editor

One of the biggest challenges of this project was creating a workflow to design levels efficiently. Instead of using Tiled, I developed a standalone tool: **[VoidLevelEditor](https://github.com/Otoni24/VoidLevelEditor)**.

This editor handles asset placement, collision box generation, and entity properties. It exports data directly to the JSON format consumed by the game engine.

> **Project Goal:** This game is an executable portfolio piece. The focus is not on commercial distribution, but rather to demonstrate "engine-less" development skills, memory management, and tool creation.