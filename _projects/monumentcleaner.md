---
layout: post
title: "Monument Cleaner"
order: 6
description: "A photogrammetry-based cleaning simulator using custom Unity shaders."
tags: [Unity, C#, HLSL, Photogrammetry, Tech Art]
role: "Solo Developer"
engine: "Unity"
date: 2026-01-26
github_link: "https://github.com/YourUsername/ArcoRestoration"
thumbnail: "/assets/images/cover_monumentcleaner.jpg"
header_video: "/assets/videos/monumentcleaner.mp4"
youtube_id: "mPJGb6v1HY0"
---

Arco dei Gavi: Virtual Restoration is a technical project designed to bridge the gap between cultural heritage preservation and real-time interactive software. The application places the player in the role of a restorer, tasked with cleaning a digital replica of the famous Roman arch in Verona.

The project required mastering a full production pipeline: capturing real-world data via photography, processing it into 3D assets, and implementing complex shader logic in Unity to allow for real-time texture modification.

## Technical Highlights

- **Photogrammetry Pipeline:** Captured ~50 analog photos and processed them via 3DF Zephyr to generate the mesh. Essential work was done in Blender to retopologize the messy scan data and optimize UV maps for texture painting.
- **Camera Calibration:** Extracted intrinsic parameters (Focal Length, Distortion) and extrinsic parameters (Position, Rotation) from the photogrammetry software and applied them to the Unity Camera. This ensures the 3D model aligns perfectly with the background photograph.
- **Performance Optimization:** Implemented a Double-Buffer system for texture manipulation. This solves the GPU limitation of reading/writing to the same texture by swapping between a source and a destination buffer during the paint cycle.

## Shader & Texture Logic

The core programming challenge was creating a cleaning tool that felt responsive and visually correct, avoiding the common artifacts found in texture-painting applications.

- **World-Space Projection:** Standard texture painting often fails across UV seams, creating jagged edges or disconnected lines. I implemented a shader that calculates the distance between the "brush" (water particle) and the surface in World Space rather than 2D UV space. This ensures that physically adjacent points on the statue are cleaned together, even if they are far apart on the texture map.
- **Real-Time Win Condition:** To detect when the monument is fully clean without causing lag, the system utilizes a compute-efficient approach. Instead of iterating through millions of pixels every frame, the dynamic dirt texture is downscaled to a 64x64 texture. The game allows the GPU to handle this reduction, and the CPU simply checks the average brightness of this small thumbnail to trigger the "Level Complete" state.