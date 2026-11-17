---
layout: post
title: "Stone & Spikes"
order: 2
description: "A turn-based tactical game developed in C++20 with raylib, featuring procedural boards, shared combat rules, and simulated enemy action planning."
tags: [C++20, Raylib, Gameplay Programming, Tactical AI, CMake]
role: "Solo Developer"
engine: "C++20 / Raylib"
date: 2026-11-17
github_link: "https://github.com/Otoni24/StoneAndSpikes"
thumbnail: "/assets/images/cover_stoneandspikes.jpg"
header_video: "/assets/videos/stoneandspikes.mp4"
youtube_id: "00vg3wsTJpI"
---

Stone & Spikes is a grid-based tactical game developed in C++20 using raylib. The player controls a team of knights against enemy skeletons, spending action points to move, attack, and push opponents onto damaging spike tiles.

The project focuses on gameplay architecture and tactical AI in standalone C++. Its main technical challenge was building an enemy planner that can simulate different action sequences using the same rules as the actual battle.

## Technical Highlights

- **Turn-Based Combat:** Each unit has an individual turn and action-point budget. Movement, attacks, and pushes create tactical choices around positioning and environmental damage.
- **Tactical Enemy Planning:** Skeletons explore legal action sequences within their remaining action points and compare the resulting states before committing to a plan.
- **Shared Combat Rules:** Live gameplay and AI simulations use the same movement, attack, and push functions, keeping action validation and outcomes consistent.
- **Procedural Board Generation:** Walls and spikes are placed randomly, with BFS connectivity checks preserving routes between ordinary floor tiles. Weighted spawning favors greater separation between opposing teams.
- **Mouse-Driven Interface:** Highlighted movement tiles, contextual attack and push buttons, health and action-point displays, and a turn-order panel make the battle playable entirely with the mouse.
- **Visual Feedback:** Attack effects, death animations, and an active-unit indicator help communicate actions and turn progression.

## Tactical Planning & State Evaluation

At the beginning of an enemy turn, the planner copies the current units into a separate planning state. It uses breadth-first search to explore legal sequences of movement, attacks, and pushes, applying each action to a copy of its parent state.

The planner compares states in priority order: victory, the number of knights eliminated, damage dealt minus damage received by the active skeleton, and distance to a position from which a living knight can be attacked. Damage and distance calculations account for multiple knights.

A separate BFS over the board measures the distance to an attack position while accounting for walls and occupied tiles. This lets enemies navigate around obstacles and consider sequences such as repositioning before pushing a knight onto spikes.

States are evaluated throughout the search, so an enemy can finish its turn early if further actions would produce a worse outcome. Planning covers the active skeleton's current turn; opponent responses and future turns are outside the search horizon.

## Gameplay Architecture

The architecture separates battle flow, combat rules, planning, and presentation:

- **`Board` and `Unit`:** Store terrain and character state, including position, faction, health, attack power, and action points.
- **`CombatRules`:** Validates and applies actions to supplied state, allowing real and simulated battles to share their gameplay logic.
- **`Battle`:** Owns the board and units, manages turn progression and victory conditions, and produces gameplay events for presentation.
- **`EnemyPlanner` and `EnemyAI`:** Separate action-sequence search from execution. The selected plan is played one action at a time, with short delays to keep enemy turns readable.
- **`BattleHud` and `AnimationPlayer`:** Handle rendering, mouse interactions, contextual menus, and visual effects.

## Reproducibility & Assets

Board generation and unit spawning use a seeded random engine. Recording the battle seed allows the initial layout to be reproduced with the same build for debugging.

Character sprites, interface artwork, and visual effects were created with AI-assisted image generation and prepared for their runtime dimensions. Gameplay systems, tactical planning, UI integration, and rendering are implemented in C++.

> **Project Goal:** Stone & Spikes demonstrates standalone C++ gameplay programming, reusable combat rules, procedural generation, and tactical planning through simulated action sequences.
