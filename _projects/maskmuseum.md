--- 
layout: post
title: "Mask Museum"
order: 2
description: "A dimension-shifting puzzle game developed in 48 hours for the Global Game Jam."
tags: [Unity, C#, Game Jam, Group Project]
role: "Co-Developer"
engine: "Unity"
date: 2026-02-15
github_link: "https://github.com/Lord-Platypus/mask_museum"
thumbnail: "/assets/images/cover_maskmuseum.jpg"
header_video: "/assets/videos/maskmuseum.mp4"
youtube_id: "GyXTJwUzWVM"
--- 

*Mask Museum* is a dimension-shifting stealth game created in 48 hours during the **Global Game Jam 2026** at the University of Verona. Developed by a spontaneous team of 7, the game challenges players to survive a Lovecraftian nightmare by constantly switching their perception between two overlapping realities.

As an elderly caretaker who triggers a dimensional split, players must wear an ancient mask to see patrolling monsters, or take it off to see the museum's physical obstacles. Because invisible threats in either dimension can still block or kill you, gameplay relies heavily on memory and rapid context-switching.

While my primary responsibility was engineering the core gameplay systems, the strict 48-hour deadline and a shortage of art personnel required me to step into a hybrid role. I leveraged my academic background in concept art to unblock the asset pipeline, acting as a direct bridge between the technical and artistic needs of the game.

## Technical Highlights

As a developer, I focused on system architecture, enemy logic, and audio management.

- **Component-Based Dimension Switch:** Unity restricts GameObjects to a single Tag, which we were already utilizing for collision and logic tracking. To implement the dimension toggle, I created a custom empty-component filtering system. A central manager script finds all actors containing specific "RealWorld" or "DistortedWorld" empty components, allowing the game to instantly toggle their Renderers while keeping their Hitboxes active in the background.
- **Dynamic Audio Crossfading:** To enhance the shifting atmosphere, I programmed a custom music manager using a dual AudioSource architecture. This allowed for smooth, real-time volume crossfading between three different music tracks as the player progresses through the levels, ensuring the audio transitions never feel abrupt.
- **Enemy Prefab Architecture:** I structured the enemy logic using modular prefabs and programmed distinct AI patterns (static, patrolling, and chasing), making it easy to populate levels quickly. I also acted as a Level Designer, utilizing these prefabs to craft several of the game's puzzles.

## Cross-Discipline Collaboration

Because our sole lead artist was heavily burdened with character animations and primary assets, I stepped in to establish the visual identity of the "Distorted World" and keep the production moving.

- **Streamlining the Art Pipeline:** I designed the initial concepts for the Lovecraftian creatures. By defining readable silhouettes and clear visual guidelines that worked well with the dimension-switching mechanic, I provided a solid foundation for our lead artist, who then efficiently illustrated the final in-game sprites.
- **Environment Production:** To ensure we hit our deadline, I directly illustrated the otherworldly backgrounds for the nightmare dimension, ensuring they integrated seamlessly with the game's rendering layers and overall color palette.

> **Project Goal:** Game Jams are the ultimate test of rapid prototyping and scope management. This project demonstrates my core competency as a programmer, while highlighting my ability to communicate effectively with the art department and step into asset production to prevent bottlenecks under extreme time constraints.