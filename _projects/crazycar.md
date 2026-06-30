---
layout: post
title: "Crazy Car"
order: -1
description: "A physics-based arcade driving tech demo developed in Unreal Engine 5."
tags: [Unreal Engine 5, C++, Gameplay Programming, Physics]
role: "Solo Developer"
engine: "Unreal Engine 5 / C++"
date: 2026-06-30
github_link: "https://github.com/Otoni24/CrazyCar"
thumbnail: "/assets/images/cover_crazycar.jpg"
header_video: "/assets/videos/crazycar.mp4"
youtube_id: "z2WF-6OH4No"
---

Crazy Car is a physics-based arcade driving tech demo developed in Unreal Engine 5. The project focuses on custom vehicle control, manual drift behavior, camera stabilization, and physical interaction inside a compact low-poly urban sandbox.

The goal was not to build a full racing game, but to create a playable technical prototype centered around car feel, collisions, and clean Unreal Engine C++ architecture.

## Technical Highlights

* **Custom Arcade Car Controller:** Implemented a C++ movement component that drives the car using physics forces, steering logic, lateral grip, and velocity control instead of relying on Unreal's built-in vehicle system.
* **Dedicated Drift Mode:** Drift is activated by player input. During drift, the normal driving simulation is replaced by a separate arcade handling mode designed for controlled and readable sliding.
* **Camera Stabilization:** Built a follow camera setup that remains readable during fast movement, impacts, and small physics-driven body jitters.
* **Physics Interaction:** The player car can collide with and push props and parked vehicles, creating a small sandbox for testing physical reactions and chaotic interactions.

## Movement & Game Feel

The main programming challenge was creating a car controller that felt responsive and arcade-like while still being driven by Unreal's physics system.

Normal driving uses force-based acceleration, steering, and lateral grip to keep the vehicle readable and stable. When the player activates drift, the controller switches to a different handling model, giving direct control over the slide without depending on a fully realistic tire simulation.

This separation made the system easier to tune and helped preserve the arcade feel even during sharp turns, collisions, and high-speed movement.

> **Project Goal:** Crazy Car is a gameplay programming tech demo focused on Unreal Engine C++, custom physics-based movement, arcade drift behavior, and readable car feel.