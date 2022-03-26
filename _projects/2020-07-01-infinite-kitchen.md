---
title: Infinite Kitchen
tags: [Lowe's, Unreal 4, Raytracing, Web, React, ]
cover: /assets/projects/infinite_kitchen/infinite_kitchen_thumbnail.png
article_header:
  type: overlay
  theme: dark
  background_color: LightSlateGray
  background_image: false
---

Lowe’s Infinite Kitchen is a kitchen visualization experience built using Unreal 4.

<!--more-->

![image](/assets/projects/infinite_kitchen/hero.png)

The goal of the project was to replace the physical kitchen “vignettes” in Lowe’s stores to show a wide range of kitchen options on a massive 3x3 array of 4k screens. The user interacts with a touchscreen to customize the 3D kitchen, and there is an arcade-style joystick to navigate the scene.

I took point on the rendering, touchscreen display, email takeaway, and analytics. Infinite Kitchen took advantage of real time raytracing for reflections, ambient occlusion, and cast shadows. I worked with the artist to create optimized materials and post processing settings to maintain a consistent framerate at 4k resolution. I implemented a React based touchscreen interface that uses a socket server to communicate changes to the Unreal application. Additionally, I created an email generator which produced a hero render of the final kitchen alongside product information and thumbnails for all of the user’s selections.