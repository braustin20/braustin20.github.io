---
title: Product Renderer Evolution
tags: [3D, TypeScript, JavaScript, Web Development, Babylon.js]
cover: /assets/blog/product_viewer/Closeup.gif
show_edit_on_github: false
show_subscribe: false
sharing: true
license: CC-BY-ND-4.0
article_header:
  type: overlay
  theme: dark
  background_image:
    src: /assets/blog/product_viewer/bottle.png
---

The way consumers buy products is constantly evolving. One of the recent evolutions in e-commerce is the growing use of 3D products and mixed-reality applications.

<!--more-->

## Product Rendering Overview

[A survey from Nielson](https://nielseniq.com/global/en/insights/analysis/2019/augmented-retail-the-new-consumer-reality-2/) from December 2019 found that 51% of respondents are willing to use augmented or virtual reality (AR/VR) to assess products, and [60% of online shoppers](https://www.globenewswire.com/news-release/2020/09/01/2087088/0/en/Survey-60-of-Online-Shoppers-Say-They-re-More-Likely-to-Buy-a-Product-If-It-s-Shown-in-3D-or-Augmented-Reality.html) say they are more likely to buy a product if it is shown in 3D or AR. These rendering methods provide more detail and interactivity than 2D images, allowing the user to make more informed purchasing decisions.

![A GE Electric Range rendered in Lowe's 3D Showroom ([https://www.lowes.com/pd/GE-Smooth-Surface-4-Elements-5-3-cu-ft-Self-Cleaning-Slide-in-Electric-Range-Stainless-Steel-Common-30-in-Actual-29-875-in/1000309761](https://www.lowes.com/pd/GE-Smooth-Surface-4-Elements-5-3-cu-ft-Self-Cleaning-Slide-in-Electric-Range-Stainless-Steel-Common-30-in-Actual-29-875-in/1000309761) ](/assets/blog/product_viewer/Closeup.gif)

<p align="center">A GE Electric Range rendered in Lowe's 3D Showroom (<a>https://www.lowes.com/pd/GE-Smooth-Surface-4-Elements-5-3-cu-ft-Self-Cleaning-Slide-in-Electric-Range-Stainless-Steel-Common-30-in-Actual-29-875-in/1000309761</a>)</p>

Our web based 3D rendering solution has gone through several major evolutions as we've strived for the highest quality and widest feature set possible. I will be walking you through the various iterations and design decisions made along the way.

## v1 - Three.js based viewer

As our 3D scanning process was maturing, we had a need for a quick way to preview and validate the assets via a web browser. At this point we did not yet have 3D content on [Lowes.com](http://lowes.com) but were building out our backend tooling and asset conversion service. A major part of this UI needed to include a 3D viewport for viewing assets in multiple quality levels and platforms and determining if the asset met our quality standards or if there was an art issue that required modification. Three.js was chosen as the framework due to it's popularity at the time, and because it offered the basic rendering features we needed.

### The Good

Three.js was great for getting us started, it has good documentation and is a widely used open source project. It is easy to find answers and support from the community. It is powered by WebGL and written in Javascript. The UI framework [dat.gui](https://github.com/dataarts/dat.gui) is included in the Three.js install and allowed us to build basic debug controls for render quality analysis. Out of the box, a Three.js project has minimal functionality and basic controls, but the build size is small.

![Three.js examples (source: [https://threejs.org/](https://threejs.org/))](/assets/blog/product_viewer/three.png)

<p align="center">Three.js examples (source: <a>https://threejs.org/</a>)</p>


### The Not so Good

The rendering engine's quality was found to be a bit lacking, and Physically Based Rendering (PBR) support lags behind similar renderers. We also found that Three.js often had breaking changes between releases, and had a number of long outstanding bugs that remained unresolved. Finally, while JavaScript is a mature and widely used language, lack of type safety and debugging support left much to be desired.

![Comparison between Three.js and Babylon.js PBR support (source: [https://modelviewer.dev/fidelity/](https://modelviewer.dev/fidelity/))](/assets/blog/product_viewer/compare.png)

<p align="center">Comparison between Three.js and Babylon.js PBR support (source: <a>https://modelviewer.dev/fidelity/</a>)</p>

## v2 - Babylon.js 3D Showroom

When it was decided that a 3D viewer should be added into the [Lowes.com](http://lowes.com) product detail page media galleries, we took the opportunity to re-evaluate 3D frameworks to find the best solution with the highest rendering quality. Babylon.js fulfilled all of our requirements by being fast, fully-featured, and easy to develop with.

Benefits of Babylon is a project created by developers at Microsoft and is open source. It is built using Typescript and can be used as an npm package in JavaScript or TypeScript projects. It has full support for [The Khronos Group's gltf 2.0](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0) specification and it's PBR extensions demonstrated above. Babylon has many built in features for camera control, scene layout, and mixed reality, which speed up development but result in a larger build size. It is well supported with frequent updates and a [sandbox](https://sandbox.babylonjs.com/) for learning and prototyping.

### Our Custom Setup

We had two main objectives with this version of the viewer -

1. Give developers an easy way to embed the viewer in Lowe's web pages for teams that do not have 3D experience
2. Provide a high quality lighting and render set up which properly showcases our products

In order to make the development process as easy as possible, we created an SDK which exposes functions to initialize the viewer, check for WebGL and augmented reality support, and even inject a "View in Your Space" button which launches the native augmented reality apps on iOS and Android.

To reach the quality level we desired, we configured a number of Babylon's advanced rendering features. The specific configuration was determined in collaboration with our art team and includes realtime shadows, image-based lighting (IBL) and tone mapping.

![Image-Based Lighting comparison. No IBL (left) is too flat, Babylon (center) has too much color cast, Lowe's IBL (right) is our optimized neutral lighting environment.](/assets/blog/product_viewer/IBL_comparison.png)

<p align="center">Image-Based Lighting comparison. No IBL (left) is too flat, Babylon (center) has too much color cast, Lowe's IBL (right) is our optimized neutral lighting environment.</p>

The realtime shadows help ground the object and accentuate detail. Our IBL setup is a compressed HDR image with a neutral lighting scenario which provides highlights and environment lighting. We use ACES tone mapping to improve the dynamic range of the model's colors and prevent white highlights from being lost against the background.

Today the Lowe's 3D Showroom is live on over 5,500 product pages with high resolution 3D models and View in Your Space functionality. New 3D product assets are continuously being added to the catalog and we have expanded functionality on our roadmap.

![A 3D model of an accent table set on [Lowes.com](http://lowes.com) ([https://www.lowes.com/pd/Cheyenne-Products-2-Piece-Walnut-Wood-Accent-Table-Set/1000832542](https://www.lowes.com/pd/Cheyenne-Products-2-Piece-Walnut-Wood-Accent-Table-Set/1000832542))](/assets/blog/product_viewer/tables.gif)

<p align="center">A 3D model of an accent table set on Lowes.com <a>https://www.lowes.com/pd/Cheyenne-Products-2-Piece-Walnut-Wood-Accent-Table-Set/1000832542</a>)</p>

## v3 - Open Source Product Viewer

The next step for our 3D technology is centered around building an open community and sharing common standards for product rendering and display of advanced features like annotations, product configuration, custom lighting, and scene layout. While commercial 3D product rendering solutions support these features, they are typically configured on the viewer when it is added to the page, not on a per asset basis. Creating a standardized metadata format will be a boon to manufacturers and retailers alike.

The latest Product Viewer is a [custom Web Component](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements) that can be included a webpage using a custom HTML tag (e.g. `<product-viewer />`). It can be added to a web project as an npm package dependency. It utilizes [shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM) to keep the viewer encapsulated within the webpage, and prevents conflict when using multiple instances.

![Untitled](/assets/blog/product_viewer/bottle.png)

The Product Viewer project contains a metadata editor to embed the lighting, annotations, and other features into the 3D assets or as a side car file. There will also be a rendering quality validation tool, which will compare and debug screenshots taken across different versions of the viewer and between 3D asset versions.

All of the above projects will be open to developer feedback and contributions. Working together will help spread the use of 3D assets in e-commerce by lowering the barrier to entry. Our goal is that companies will be able to create a single product asset that can be rendered consistently on any website using the Product Viewer. We hope you join us on our journey.
