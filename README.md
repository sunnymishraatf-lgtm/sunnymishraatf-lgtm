<div align="center">

# 🌌 Neon Topology Visualizer

<p align="center">
  <strong>An interactive WebGL exploration of 4-dimensional space projected into a glowing, neon 3D lattice.</strong>
</p>

<p align="center">
  <img alt="Three.js" src="https://img.shields.io/badge/Three.js-000000?style=for-the-badge&logo=threedotjs&logoColor=white"/>
  <img alt="WebGL" src="https://img.shields.io/badge/WebGL-990000?style=for-the-badge&logo=webgl&logoColor=white"/>
  <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
  <img alt="GLSL" src="https://img.shields.io/badge/GLSL_Shaders-8b00d2?style=for-the-badge&logo=shader&logoColor=white"/>
</p>

---

> Replace this text with a GIF or Screenshot of your visualizer!
> `![Visualizer Demo](https://your-gif-link-here.gif)`

---

</div>

## 📖 Overview

This project is a real-time procedural visualizer built entirely in vanilla JavaScript and Three.js. It renders a mathematical fiber bundle—reminiscent of the **Hopf Fibration**—by generating thousands of interconnected lines that map 4D hyperspheres into 3D space. 

Coupled with a deep-space atmospheric rendering pipeline, the result is an immersive, cyberpunk-inspired topological animation complete with light pulses, stellar drift, chromatic aberration, and custom post-processing effects.

## 🛸 Features

- **APolynomial Generation:** 5 nested geometric levels mapped via stereographic projection to create a flawless spherical lattice.
- **Live Control Panel:** A custom-built, glassmorphic UI with an animated neon border. Tweak density, pulse speeds, and bloom intensity on the fly.
- **3 Distinct Color Themes:**
  - 🔥 **Inferno:** Blazing oranges and deep reds.
  - ❄️ **Spectral:** Electric cyans and purples.
  - 🌿 **Aether:** Bio-luminescent greens and mints.
- **Procedural "Light Pulses":** Cosine-sine mathematical waves travel down the fibers, heating up the lines and triggering dynamic additive color blending.
- **Deep Space Atmospherics:**
  - **Custom Shaders:** Real-time Chromatic Aberration and Film Grain.
  - **Unreal Bloom:** Powered by Three.js's post-processing pipeline.
  - **Particle Systems:** Procedural starfields, viewport-facing nebula sprites, and floating orbital dust.
- **Optimized Rendering:** Uses `Float32Array` typed data and direct buffer attribute updates toPolygon rendering of thousands of segments at 60+ FPS.

## 🕹️ Controls

The visualizer supports full 3D camera controls via Orbit Controls:

| Action | Effect |
| :--- | :--- |
| **Left Click + Drag** | Rotate the camera around the topology. |
| **Right Click + Drag** | Pan the camera horizontally/vertically. |
| **Scroll Wheel** | Zoom in and out of the lattice. |
| **UI Sliders** | Adjust Density, Pulse speed, and Bloom strength. |
| **UI Color Buttons** | Switch between Inferno, Spectral, and Aether palettes. |

## 🧮 The Math Under the Hood

At the heart of this visualizer is a variation of the **Hopf Fibration** ($S^3 \rightarrow S^2$). 

For every point on a 2D sphere ($S^2$), there is a corresponding circle ($S^1$) embedded in a 4D hypersphere ($S^3$). 

The code generates 4D points $(w, x, y, z)$ and applies a series of rotational matrices to them over time. To bring these 4D coordinates into our 3D space, it uses **stereographic projection**:
```javascript
const d = 1.0 / dn; // where dn is the depth in the 4th dimension
px = x2 * d; 
py = y2 * d; 
pz = z2 * d;
