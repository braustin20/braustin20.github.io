---
title: 3D Product Viewer
tags: [Lowe's, TypeScript, 3D, Web, Babylon.js, AR]
cover: /assets/projects/product_viewer/product_viewer_thumbnail.png
show_edit_on_github: false
show_subscribe: false
sharing: true
license: CC-BY-ND-4.0
article_header:
  type: overlay
  theme: dark
  background_image:
    src: /assets/projects/product_viewer/product_viewer_screenshot.png
---

Lowe’s 3D Showroom is a BabylonJS powered 3D asset viewer developed alongside Lowe’s Innovation Labs’ asset pipeline.

<!--more-->

This viewer is used to validate and approve photogrammetry scans of Lowe’s products and display them on Lowe’s websites. I was tasked with replacing the older ThreeJS based viewer with a new web app built from the ground up to be more modular and extensible. We used webpack and npm to create modules and endpoints for each use case. I extended the inspector panel with new debug features for testing shadow filtering methods and lighting scenarios so that artists could validate their work.
