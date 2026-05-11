# Computer Graphics Rendering Techniques

This repository contains a collection of computer graphics assignments demonstrating the implementation of fundamental rendering algorithms and shader programming. Developed in C++ and GLSL, these projects span both real-time rasterization techniques and offline global illumination models.

## Repository Overview

This repository showcases four major assignments:
1. Environment Mapping & Procedural Texturing
2. Projective Texturing & Shadow Mapping
3. Ray Tracing (Whitted & Distribution)
4. Progressive Refinement Radiosity

---

## Assignment 1: Environment Mapping & Procedural Texturing

### Introduction
This project implements advanced texturing and reflection techniques on 3D geometric primitives using OpenGL shaders. The scene consists of a skybox representing an infinitely far environment, alongside two focal objects: a brick cube utilizing normal mapping for surface details, and a wooden cube featuring procedurally generated hemispherical mirrors that dynamically reflect the surrounding skybox.

### Demo
https://github.com/user-attachments/assets/a7439462-9a99-46ac-ab57-6c726a52d760

### Technologies & Algorithms
* **Languages & APIs:** C++, OpenGL, GLSL (Fragment/Vertex Shaders)
* **Algorithms & Techniques:**
    * Normal Mapping (Tangent Space calculations)
    * Procedural Bump Mapping
    * Reflection Mapping using Cubemaps
    * Phong Illumination Model

### How to Run
1. Open the provided Xcode project (`main.xcodeproj`).
2. Build the project. The application loads the vertex and fragment shaders (`shader.vert` and `shader.frag`) at runtime.
3. Run the executable to view the rendered scene. Use the mouse/keyboard to rotate the camera and observe the view-dependent reflections.

---

## Assignment 2: Projective Texturing & Shadow Mapping

### Introduction
This assignment focuses on real-time shadow generation and light projection. The program renders a scene as if it is illuminated by a projector casting an image. It implements a multi-pass rendering pipeline to generate shadows and filter them to produce smooth, realistic edges rather than hard, pixelated boundaries.

### Demo
https://github.com/user-attachments/assets/f3750147-54a4-467f-aee7-0457eaea25a1

### Technologies & Algorithms
* **Languages & APIs:** C++, OpenGL, GLSL
* **Algorithms & Techniques:**
    * Shadow Mapping (Multi-pass rendering via Framebuffer Objects - FBOs)
    * Percentage-Closer Filtering (PCF) for anti-aliasing shadow edges
    * Image Projection / Projective Texture Mapping

### How to Run
1. Open the Xcode project (`main.xcodeproj`).
2. Ensure the required shaders (`shader.vert`, `shader.frag`) are in the working directory.
3. Build and execute the program to see the dynamically shadowed scene.

---

## Assignment 3: Ray Tracing (Whitted & Distribution)

### Introduction
Implemented entirely within a fragment shader, this assignment builds a complete ray tracer from scratch. The initial task implements Whitted Ray Tracing to support perfect reflections and refractions. It is then extended into a Distribution Ray Tracer to simulate physical camera lens effects, creating depth-of-field and spatial anti-aliasing. The project also features custom perpetual animations and bonus implementations for glossy surfaces and area lights.

### Technologies & Algorithms
* **Languages & APIs:** GLSL (Shadertoy environment)
* **Algorithms & Techniques:**
    * Whitted Ray Tracing (Recursive ray generation)
    * Distribution Ray Tracing (Stochastic sampling)
    * Depth-of-Field (DoF) and Anti-Aliasing (Jittering/Pixel sampling)
    * Area Lights (Soft shadows) and Glossy Reflections (Perturbed reflection rays)
    * Procedural Animation

### How to Run
1. Navigate to [Shadertoy](https://www.shadertoy.com/new) in a web browser.
2. Copy the contents of the completed `.frag` files (e.g., `task1.frag`, `task2.frag`, `task3.frag`).
3. Paste the code into the Shadertoy source editor.
4. Click the compile/run button (the black triangle at the bottom-left of the editor) to view the real-time ray-traced animation.

---

## Assignment 4: Progressive Refinement Radiosity

### Introduction
This project implements an offline global illumination solver based on the Progressive Refinement Radiosity algorithm. Unlike local illumination models, radiosity computes the transfer of diffuse light energy between all surfaces in a scene, naturally simulating effects like color bleeding and soft area shadows. The provided software reads a scene model (like the Cornell Box), subdivides it into "shooter" and "gatherer" patches, and progressively distributes light until convergence.

### Demo
![cornell_box_1](./assign4_(win-vs2017)/cornell_box_1.png)
![cornell_box_2](./assign4_(win-vs2017)/cornell_box_2.png)
![cornell_box_3](./assign4_(win-vs2017)/cornell_box_3.png)

### Technologies & Algorithms
* **Languages & APIs:** C/C++, Legacy OpenGL (1.1), GLU/GLUT
* **Algorithms & Techniques:**
    * Progressive Refinement Radiosity
    * Hemicube Algorithm (for Form Factor estimation and Delta Form Factors)
    * Item Buffering (for patch visibility determination)
    * Tone Mapping

### How to Run
This assignment contains three separate build targets within the `assign4.sln` (VS2017):
1.  **QuadsViewer:** Run this to preview the input scene geometry (`model.in`) and verify the subdivision of quads.
2.  **RadiositySolver:** Ensure your target scene is named `model.in`. Run this target to compute the radiosity solution. Warning: Depending on patch density, this may take a while. It will output a solved scene file named `model.out`.
3.  **RadiosityViewer:** Run this target to load `model.out` and visualize the final globally illuminated scene.
