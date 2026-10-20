---
layout: post
title: "Build_Failed"
order: -10
description: "A two-player cooperative platformer developed in Unreal Engine 5, focused on networked character movement and cooperative mechanics."
tags: [Unreal Engine 5, C++, Gameplay Programming, Network Programming, Multiplayer, Group Project]
role: "Gameplay Programmer"
engine: "Unreal Engine 5 / C++"
date: 2026-09-01
thumbnail: "/assets/images/cover_buildfailed.jpg"
header_video: "/assets/videos/buildfailed.mp4"
youtube_id: "Nl76pShJbm8"
---

Build_Failed is a two-player cooperative platformer developed by a team of 7 as the final project of the **Master in Game Development** program at the University of Verona. Main development began in September 2026.

The game combines platforming with cooperative challenges, including changing character scale and sharing control of a single character. Online play uses Steam connectivity with one player acting as the host.

My primary responsibility was **C++ character and movement programming**, alongside cooperative mechanics, camera and animation integration. I also contributed to the overall game design and to the design, environment assembly, and gameplay integration of the **Scale Calibration** level.

## Technical Highlights

* **Custom Character Movement:** Extended Unreal's `UCharacterMovementComponent` with jumping, coyote time, input buffering, dash, and roll, coordinating movement logic with character animation and camera behavior.
* **Network Prediction Integration:** Co-developed the movement networking implementation with **Riccardo Conforti**, responsible for networking. Custom movement features extend Unreal's existing prediction and correction systems, allowing the remote player to receive immediate local movement feedback while remaining synchronized with the host.
* **Character Scaling:** Implemented character scale changes and their integration with movement, collision, and network state, supporting the cooperative interactions in Scale Calibration.
* **Shared Character Control:** Developed a cooperative mechanic in which two players control a single character through distributed movement and action inputs, while retaining independent cameras.
* **Respawn & Checkpoints:** Implemented checkpoint and respawn logic for both players, including restoration of character scale after respawning.

## Movement Architecture & Network Prediction

The main technical challenge was learning how Unreal's Character Movement Component handles client prediction, server corrections, and the replay of saved movement. This shaped the architecture of both the Character and its movement component.

Input handlers set flags that express the player's requested actions. Movement transitions are then processed within the `PerformMovement` cycle, specifically I worked in `UpdateCharacterStateBeforeMovement`, so the relevant logic runs as part of the movement simulation.

Custom movement state also had to be structured so it could be restored and replayed after a correction. I worked on integrating these additional features into Unreal's movement networking pipeline. This required considering prediction and replay throughout the gameplay code, including how actions begin, how state changes are stored, and how movement resumes after reconciliation.

The result is a movement system designed to respond locally to player input while allowing the host to validate and correct the simulation. The project's Steam connection and session framework was handled by the teammate responsible for the multiplayer framework.

## Scale Calibration & Team Integration

I contributed to the game's overall design and co-designed the **Scale Calibration** level with two other designers. For this level, I also assembled the environment using the project's asset packs and integrated the character-scaling mechanic with the level's interactions.

A substantial part of this work involved testing and debugging features that had been developed independently by different team members. Bringing them together required checking their behavior in the actual level, identifying conflicting assumptions, and fixing issues across movement, cooperative interactions, and respawn state.

This connected my programming responsibilities with level design and environment composition: implementing the mechanic, placing the assets used to build its challenges, and iterating on the combined result through playtesting.

> **Project Goal:** Build_Failed brings together Unreal Engine C++ gameplay programming, network-aware movement architecture, cooperative mechanics, and collaborative production. My focus was on responsive character control and on integrating custom gameplay systems into a shared multiplayer project.
