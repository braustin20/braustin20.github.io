---
title: 3D Product Viewer
tags: [Lowe's, Typescript, 3D, Web, Babylon.js, AR]
cover: /assets/projects/product-viewer/product_viewer_screenshot.png
article_header:
  type: cover
  image:
    src: /assets/projects/product-viewer/product_viewer_screenshot.png
---

Lowe’s 3D Showroom is a BabylonJS powered 3D asset viewer developed alongside Lowe’s Innovation Labs’ asset pipeline. This viewer is used to validate and approve photogrammetry scans of Lowe’s products and display them on Lowe’s websites.

<!--more-->

I was tasked with replacing the older ThreeJS based viewer with a new web app built from the ground up to be more modular and extensible. We used webpack and npm to create modules and endpoints for each use case. I extended the inspector panel with new debug features for testing shadow filtering methods and lighting scenarios so that artists could validate their work.
