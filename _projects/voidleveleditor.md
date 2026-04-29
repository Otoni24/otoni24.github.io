---
layout: post
title: "Void Level Editor"
order: 4
description: "A custom 2D level editor written in C++ with automated hitbox generation."
tags: [C++, SFML, ImGui, Tool Dev]
role: "Solo Developer"
engine: "C++ / SFML / ImGui"
date: 2025-06-01
github_link: "https://github.com/Otoni24/VoidLevelEditor"
thumbnail: "/assets/images/cover_voidleveleditor.jpg"
header_video: "/assets/videos/voidleveleditor.mp4"
youtube_id: "E6CmuVR_3yI"
---

VoidLevelEditor is a simple and visual 2D level editor, written in C++, designed to create levels and export hitbox data directly into JSON format.

It allows for the visual placement of assets onto a background image and features a highly efficient, automated collision generation system to streamline the level design workflow.

## Core Features

- **Visual Layout:** Place, move, scale, and rotate game assets directly on your level's background image for an intuitive, WYSIWYG workflow.
- **Modern C++ Stack:** Built with standard C++17, utilizing [SFML](https://github.com/SFML/SFML) for fast rendering and a simple, dockable user interface created with [Dear ImGui](https://github.com/ocornut/imgui).
- **Project & Level Management:** Save the entire workspace—including asset definitions and local paths—into a project file for later editing. When the design is ready, export the finalized level data into a clean `.json` format optimized for game consumption.

## Automated Collision Generation

One of the biggest challenges in custom engine development is defining complex physical boundaries. To solve this, I developed a separate library called **[VectorizerLib](https://github.com/Otoni24/VectorizerLib)** and integrated it directly into the editor.

This system allows the user to simply upload a visual texture and a binary (black & white) mask. The editor then automatically generates the optimized Box2D collision chains required for gameplay using two key algorithms:
- **Marching Squares:** Traces the exact contours from the black-and-white collision mask image.
- **Ramer-Douglas-Peucker (RDP):** Simplifies the resulting geometry, reducing unnecessary vertices and outputting highly efficient vector chains.

## Game Integration

To load the exported `.json` levels into a C++ game, VoidLevelEditor is designed to be paired with its companion library, **[VoidLevelLoader](https://github.com/Otoni24/VoidLevelLoader.git)**.

This lightweight, standalone library parses the exported JSON and converts it into a simple C++ data structure, ready to instantiate game objects. It is designed for seamless integration into any C++ project via CMake `FetchContent`.