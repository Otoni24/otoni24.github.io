--- 
layout: post
title: "Neon Pinball"
order: 1
description: "A physics-driven arcade pinball game developed in Unreal Engine 5 focusing on C++ backend logic."
tags: [Unreal Engine 5, C++]
role: "Solo Developer"
engine: "Unreal Engine 5 / C++"
date: 2026-03-04
github_link: "https://github.com/Otoni24/NeonFlipper"
thumbnail: "/assets/images/cover_neonflipper.jpg"
header_video: "/assets/videos/neonflipper.mp4"
--- 

Neon Pinball is a classic arcade game developed as a hands-on technical project to deeply explore Unreal Engine 5. The primary goal was to master the integration between C++ backend logic, the Chaos physics engine, and the frontend Blueprint UI system.

Rather than relying on kinematic approximations or fake animations, the game forces the player to adapt to realistic momentum and angles, delivering a fast-paced and physically accurate pinball experience.

## Technical Highlights

- **C++ Driven Architecture:** Over 90% of the core gameplay logic is written in C++. Blueprints are used strictly for their intended strengths: UI layout (UMG), asset assignment, and high-level visual wiring.
- **Advanced Physics Constraints:** The flippers (rackets) are physical bodies attached to the table using Hinge Constraints. They are driven by angular motors and torque within the Chaos physics system, ensuring the force transferred to the ball is dynamically calculated based on mass and velocity.
- **State & Input Management:** Fully integrated Unreal's Enhanced Input System with a custom C++ state controller. This allows for seamless transitions between `Game Only` and `Game And UI` input modes, freezing the 3D physics world while keeping the Pause Menu fully interactive.

## Shaders & Collision Logic

The project required precise physical interactions and performant visual feedback to maintain the fast-paced arcade feel.

- **World Position Offset (WPO):** To handle environmental reactions (such as bumpers physically compressing when hit), I utilized dynamic materials driven by World Position Offset. This handles the visual deformation directly on the GPU via shaders, completely bypassing the CPU overhead of skeletal meshes or Blueprint timelines.
- **Practical Collision Setup:** While standard interactive objects use lightweight primitive colliders, custom and intricate meshes (like curved ramps) utilize the "Use Complex Collision as Simple" setting. This practical choice guarantees pixel-perfect ball trajectories and prevents unpredictable bounces on complex geometry.