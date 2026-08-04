---
layout: post
title: "Platformer Demo"
order: -0.5
description: "An Unreal Engine 5 tech demo focused on C++ gameplay programming, animation integration, UI, and audio."
tags: [Unreal Engine 5, C++, Gameplay Programming, Animation, UI]
role: "Solo Developer"
engine: "Unreal Engine 5 / C++"
date: 2026-08-04
github_link: "https://github.com/Otoni24/Platformer.git"
thumbnail: "/assets/images/cover_platformer.jpg"
header_video: "/assets/videos/platformer.mp4"
youtube_id: "-CB5Db7SBuQ"
---

Platformer Demo is an educational third-person prototype developed in Unreal Engine 5, primarily in C++.

The project was built to practise the integration of character movement, animation, boss logic, UI, audio, and Unreal Engine's gameplay framework. The focus was on technical implementation rather than level design or creating a complete game.

## Technical Highlights

* **Character Movement:** Implemented variable-height jumping, coyote time, an aerial dash, a root-motion ground roll, knockback reactions, and custom movement transitions.
* **Animation Integration:** Coordinated C++ gameplay logic with Animation Blueprints, Blend Spaces, Montages, root motion, and animation notifies.
* **Boss Encounter:** Created a mechanical boss with attack, recovery, damage reaction, and death states, including animation-driven hitboxes.
* **Camera System:** Developed a custom camera component that gradually realigns with the character's movement direction after manual input stops.
* **Persistent UI:** Built a HUD and pause menu supporting both mouse and controller input, with player data preserved across respawns through a custom PlayerState.
* **Gameplay Audio:** Added spatialized world sounds, animation-driven effects, looping Audio Components, attenuation settings, and 2D UI feedback.

## Animation & Asset Pipeline

Several animations required manual creation or revision before being integrated into the project.

This involved working with Blender and Unreal Engine to manage rigs, bones, root motion, animation timing, export and import settings, and engine-side asset configuration. UI graphics and other supporting assets were also prepared externally and imported into Unreal.

> **Project Goal:** This project was created as a practical study of Unreal Engine gameplay programming, with particular attention to the interaction between C++, animation, UI, audio, and externally produced assets.