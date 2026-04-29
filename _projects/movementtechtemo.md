---
layout: post
title: "Movement Tech Demo"
order: 0
description: "A technical showcase in Unreal Engine 5 focusing on C++ integration and custom movement physics."
tags: [Unreal Engine 5, C++, Gameplay Programming, Combat System, Physics]
role: "Solo Developer"
engine: "Unreal Engine 5 / C++"
date: 2026-04-20
github_link: "https://github.com/Otoni24/MovementTechDemo"
thumbnail: "/assets/images/cover_mtd.jpg"
header_video: "/assets/videos/movementtechdemo.mp4"
youtube_id: "hn0gscf9EUg"
---

MovementTechDemo is a personal technical project developed in Unreal Engine 5 to explore the integration between C++ logic, custom physics, and the animation pipeline. The goal was to extend core engine components to create a responsive, arcade-style movement system.

Rather than relying on default behaviors, the project focuses on overriding base classes to implement custom mechanics driven by mathematical foundations like Quaternions.

## Technical Highlights

- **Custom Gliding System:** Implemented by overriding the `UCharacterMovementComponent`. It features a new movement state integrated into the engine's physics loop. To ensure stability and avoid gimbal lock during 360-degree aerial maneuvers, all rotation logic is handled via **Quaternions**.
- **Foot IK Rig:** A system designed to ensure realistic character interaction with uneven terrain. It utilizes Line Tracing to detect surface normals and adjusts foot orientation and position using Quaternions for seamless alignment on sloped surfaces.
- **C++ Driven Animation:** Logic is centralized in a custom `UAnimInstance` class. This includes a **Lean System** based on the character's angular velocity, providing dynamic visual feedback during turns.

## Combat & Camera Logic

The project also explores the communication between gameplay code and visual assets through:
- **Combat Framework:** A base combo system that manages input buffering and chained Animation Montages, ensuring precise timing between C++ logic and animation frames.
- **Lock-On Mechanic:** A dedicated system for managing actor orientation and camera focus during combat encounters.
- **Lazy Follow Camera:** An extension of the `USpringArmComponent` that implements a custom follow logic. It is highly tweakable via the editor, allowing for cinematic movement that reacts to the player's current speed and direction.

> **Project Goal:** This demo serves as a technical showcase of proficiency in Unreal Engine C++, specifically in extending core components (`CharacterMovement`, `SpringArm`), implementing mathematical solutions for 3D space, and bridging procedural systems with traditional Animation Blueprints.