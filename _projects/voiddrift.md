---
layout: post
title: "VoidDrift"
order: 3
description: "A custom C++ arcade game built from scratch without commercial engines."
tags: [C++, SFML, Box2D, Engine Architecture]
role: "Solo Developer"
engine: "Custom C++ / SFML"
date: 2025-06-01
github_link: "https://github.com/Otoni24/VoidDrift"
thumbnail: "/assets/images/cover_voiddrift.jpg"
header_video: "/assets/videos/voiddrift.mp4"
---

VoidDrift is a 2D arcade game developed as an educational project. The primary goal was to master Modern C++ and understand the low-level fundamentals of game architecture without relying on a commercial engine like Unity or Unreal.

To maintain a strict focus on engine programming and technical development, all 2D sprites and visual assets were sourced from external graphic packs. This allowed me to dedicate my time entirely to building the custom C++ framework, physics integration, and data pipelines.

The game delivers a complete arcade experience, featuring 3 levels, physics-based movement and a highly customized content pipeline.

## Technical Highlights

- **Custom Framework:** Built from the ground up using C++17 and [SFML](https://github.com/SFML/SFML) for rendering, window management, audio, and input handling.
- **Physics-Based Gameplay:** Integrated [Box2D](https://github.com/erincatto/box2d) directly into the game loop for precise physics simulations and dynamic collision resolution.
- **Data-Driven Design:** Levels are not hardcoded but loaded dynamically from external `.json` files, parsed via a custom [VoidLevelLoader](https://github.com/Otoni24/VoidLevelLoader) library.

## Dedicated Tooling & Pipeline

Instead of relying on generic third-party software like Tiled, I developed a complete custom pipeline to design levels efficiently.

All entity properties and physics colliders for VoidDrift were generated using my own standalone C++ tool: **[VoidLevelEditor](https://otoni24.github.io/projects/0_voidleveleditor/)**. A standout feature of this custom pipeline is its **automated collision generation**. By simply feeding the editor a black-and-white PNG mask of the level environment, the tool mathematically traces the contours and automatically generates the optimized Box2D collision chains required for the game.

> **Project Goal:** This game is an executable portfolio piece. The focus is not on commercial distribution, but rather to demonstrate "engine-less" development skills, memory management, and engine architecture.