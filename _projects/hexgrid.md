---
layout: post
title: "HexGrid - Energy Rush"
order: 5
description: "A C++ resource management puzzle developed with Raylib."
tags: [C++, Raylib, CMake, Group Project]
role: "Co-Developer"
engine: "C++ / Raylib"
date: 2026-01-20
github_link: "https://github.com/Furcanzo/HexGrid"
thumbnail: "/assets/images/cover_hexgrid.jpg"
header_video: "/assets/videos/hexgrid.mp4"
youtube_id: "QKQzExNvCO4"
---

HexGrid is a strategic resource management game developed as part of the **Master in Game Development** program at the University of Verona. Developed by a team of 4 students, the challenge was to build a fully functional game without using commercial engines like Unity or Unreal, relying instead on the **Raylib** framework.

The game combines factory-building mechanics with puzzle-like constraints. The objective is to build the final Energy Source as fast as possible, requiring precise resource balancing to avoid softlocks.

## Technical Highlights

- **Engine-less Architecture:** Developed entirely in **C++20** using [Raylib](https://github.com/raysan5/raylib) for rendering, window management, and input handling.
- **Modern Build System:** Utilizes **CMake** for dependency management (fetching Raylib and mINI automatically) and cross-platform compilation.
- **Data-Driven Configuration:** Game balance and building stats are parsed from external INI files using [mINI](https://github.com/metayeti/mINI), allowing for rapid iteration without recompiling.
- **Group Collaboration:** Managed via Git, requiring strict code standards to merge gameplay logic, UI, and rendering systems seamlessly.

## Gameplay Logic & Grid System

The core programming challenge was implementing a reactive grid system where building states update dynamically based on their surroundings.

- **Adjacency Algorithms:** Implemented a neighbor-checking system where placing a building triggers immediate updates to adjacent tiles. For example, industrial zones calculate "pollution" logic to debuff nearby residential tiles, while power plants boost connected extractors.
- **Resource State Management:** The game loop handles two distinct resource behaviors:
    - **Hard-Capped Pools:** (Energy/Workers) which require immediate capacity checks before construction.
    - **Accumulators:** (Materials/Oil) which grow over time based on a delta-time flow rate.