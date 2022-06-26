---
title: Lowe's 3D Product Viewer
tags: [TypeScript, 3D Rendering, Babylon.js, AR, Analytics]
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
### Overview

This viewer is used to validate and approve photogrammetry scans of Lowe’s products and display them on Lowe’s websites. It is built upon Babylon.js and includes tools for inspecting model quality and adding product metadata. It is written in TypeScript and I led the effort to open source the technology, available at [https://github.com/lowes/product-viewer](https://github.com/lowes/product-viewer).

<img class="image image--xl" src="/assets/projects/product_viewer/approvalviewer2.png"/>

### Role

I was tasked with replacing the older ThreeJS based viewer with a new web app built from the ground up to be more modular and extensible. We used webpack and npm to create modules and mixins for each use case. I extended the inspector panel with new debug features for testing shadow filtering methods and lighting scenarios so that artists could validate their work. I also open-sourced the project which has since been incorporated into the [Lowe's Open Builder Initiative](https://www.lowesinnovationlabs.com/projects/lowes-open-builder).

You may read more about this project's evolution in my [blog post](/blog/2021/11/03/product-renderer-evolution.html)

### Images
<img class="image image--xl" src="/assets/projects/product_viewer/product_viewer_screenshot.png"/>
<img class="image image--xl" src="/assets/projects/product_viewer/product_viewer_screenshot_2.png"/>
<img class="image image--xl" src="/assets/projects/product_viewer/webviewer3.jpg"/>
<img class="image image--xl" src="/assets/projects/product_viewer/webviewer2.png"/>
