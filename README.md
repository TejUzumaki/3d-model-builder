# 🌲 3D Model Builder Pro

**Live App:** [https://3d-model-builder-one.vercel.app/](https://3d-model-builder-one.vercel.app/)

A lightweight, touch-optimized 3D modeling tool built specifically for AI-assisted game development. Instead of fighting with AI text prompts to describe 3D shapes, you build them visually, copy the generated Three.js code, and paste it directly into your AI prompt. The AI then perfectly replicates your custom asset in your game.

---

## 💡 The Journey: Why We Built This

The idea was born out of pure frustration. When building 3D games using AI (like ChatGPT or Claude), getting the AI to generate custom 3D assets is a massive bottleneck. 

1. **The Text Prompt Problem:** If you ask an AI to "make a low-poly jagged rock tree," it guesses the math, usually resulting in spiky urchins or broken geometry. 
2. **The Asset Problem:** Downloading `.glb` files from asset sites bogs down games and doesn't teach the AI how to place objects in code.
3. **The "Aha!" Moment:** We realized we needed a "Visual Prompter for 3D Space." What if we could just drag, scale, and chop shapes visually, and the app translates that into clean, human-readable Three.js code?

We started with a basic prototype—just a box and a sphere. But through rapid iteration, we added a Convex Hull "Rockify" algorithm, smart code compression, tablet touch support, and a professional UI. This app bridges the gap between human imagination and AI code generation.

---

## ✨ Features & How They Were Thought About

* **🖋️ Rockify (Flat Cuts):** Originally, adding "noise" just pushed vertices outward, creating spiky sea urchins. We rewrote the math to use Three.js `ConvexGeometry`. Now, it chops chunks out of the shape, pulling vertices inward to create authentic, asymmetric flat-faced rocks.
* **🗜️ Smart Code Minimizer:** A single rock tree used to output 300+ lines of `Vector3` coordinates. We implemented a **Flat Array Helper** `V([x,y,z, x,y,z...])` and **Geometry/Material Caching**. If you duplicate a rock 5 times, the code only generates the points *once* and reuses them. This cuts the code size by 80%, making it incredibly easy for your AI to process.
* **📱 Touch-First UI:** Designed entirely for Android tablets. The main toolbar is at the bottom center for easy thumb reach. The Properties (left) and Transform (right) panels are fully draggable, resizable, and feature large touch-target sliders.
* **⏪ Smart Undo/Redo & Auto-Save:** We built a custom history tracker that saves your scene to LocalStorage automatically. If your browser crashes, your 3D model is waiting for you when you return. 
* **📁 JSON Import/Export:** Build a scene on your tablet, export the JSON, and import it on your PC to continue working.
* **🔗 Grouping & Auto-Grouping:** Group individual shapes into a single `THREE.Group()`. Even if you forget to group your objects, the code exporter wraps ungrouped meshes into an `auto_group` so your AI treats the tree as one single asset.

---

## 📖 How to Use It

### 1. Build Your Asset
1. Open the [Live App](https://3d-model-builder-one.vercel.app/).
2. Select a shape (Box, Sphere, Cylinder, etc.) from the dropdown and click **Add**.
3. Use the **Move/Rotate/Scale** tools (top left) or the Transform Sliders (right panel) to position it.
4. Select the object and use the **Properties Panel** (left) to change its color, polycount, or apply the **Rockify** slider.
5. Click **Duplicate** to clone parts, then click **Group** to merge them into a single object (like a tree).

### 2. Copy the Code
1. Click the bright white `</>` button in the top right to open the Code Panel.
2. Click **Copy**. The code is now on your clipboard.

### 3. Prompt Your AI
Go to ChatGPT, Claude, or your AI coding assistant and say:
> *"I am building a 3D game. Here is the Three.js code for a custom tree I designed. Please add this exact model to my game scene: [Paste Code Here]"*

The AI will read the clean, minimized code and generate the exact same 3D model in your game!

---

## 🛠️ Tech Stack
* **Three.js:** WebGL rendering and geometry generation.
* **Vanilla JS:** No heavy frameworks, just fast, raw logic.
* **CSS:** Custom flat-design 2026 UI with no gradients, just clean matte panels.

## 🚀 Deployment
This app is deployed on Vercel and hosted on GitHub. It runs entirely client-side, meaning it works completely offline once loaded!

