# 🌲 3D Model Builder Studio

**Live App:** [https://3d-model-builder-one.vercel.app/](https://3d-model-builder-one.vercel.app/)

A professional, touch-optimized 3D modeling studio built specifically for AI-assisted game development. Instead of fighting with AI text prompts to describe 3D shapes, you build them visually, copy the generated Three.js code, and paste it directly into your AI prompt. 

---

## 💡 The Journey: Why We Built This

The idea was born out of pure frustration. When building 3D games using AI (like ChatGPT or Claude), getting the AI to generate custom 3D assets is a massive bottleneck. 

1. **The Text Prompt Problem:** If you ask an AI to "make a low-poly jagged rock tree," it guesses the math, usually resulting in spiky urchins or broken geometry. 
2. **The Asset Problem:** Downloading `.glb` files from asset sites bogs down games and doesn't teach the AI how to place objects in code.
3. **The "Aha!" Moment:** We realized we needed a "Visual Prompter for 3D Space." What if we could just drag, scale, and chop shapes visually, and the app translates that into clean, human-readable Three.js code?

We started with a basic prototype—just a box and a sphere. But through rapid iteration, we added a Convex Hull "Rockify" algorithm, smart code compression, tablet touch support, and a professional UI. This app bridges the gap between human imagination and AI code generation.

---

## ✨ Studio Features

### 1. Asset Editor (3D Modeling)
*   **Primitives & 2D Planes:** Build models using Boxes, Spheres, Cylinders, etc., as well as 2D Planes (perfect for grass blades or banana leaves).
*   **Rockify (Flat Cuts):** Uses `ConvexGeometry` to chop chunks out of a shape, pulling vertices inward to create authentic, asymmetric flat-faced rocks.
*   **Quick Color Palette:** Saves your last 8 used colors so you can instantly swap between trunk brown and leaf green.
*   **Grouping & Duplication:** Group individual shapes into a single `THREE.Group()` to form complex structures like trees.

### 2. Terrain Editor (Level Design)
*   **3D Volumetric Terrain:** Generates a 3D cuboid terrain (not just a flat cloth), making it perfect for game collisions and adding underground layers.
*   **Noise Generation:** Base Height, Roughness, and Jaggedness sliders create rocky, mountainous layers using custom Value Noise.
*   **Sculpt & Flatten Brushes:** A 4th tool (next to Move/Rotate/Scale). Drag your finger/cursor on the terrain to carve grooves, raise mountains, or use the **Flatten** brush to create flat areas for villages!
*   **Asset Importer:** A dropdown in the terrain editor lets you spawn your saved Asset projects directly onto the map.

### 3. Code Generation (AI Export)
*   **Smart Code Minimizer:** Uses a Flat Array helper `V([x,y,z, x,y,z...])` and **Geometry/Material Caching**. If you duplicate a rock 5 times, the code only generates the points *once* and reuses them. This cuts the code size by 80%, making it incredibly easy for your AI to process.

### 4. Universal UI & UX
*   **Project Dashboard:** A gallery of saved projects with image previews. Auto-saves your work to LocalStorage.
*   **Cross-Platform:** Draggable/Resizable panels, Touch-optimized sliders, and Keyboard shortcuts (G, R, S, F, Ctrl+Z, etc.).

---

## 📖 How to Use It

### 1. Build Your Asset or Terrain
1. Open the [Live App](https://3d-model-builder-one.vercel.app/).
2. Click **New Asset** or **New Terrain**.
3. Use the **Move/Rotate/Scale** tools (top left) or the Transform Sliders (right panel) to position objects.
4. Use the **Properties Panel** (left) to change color, polycount, or apply the **Rockify** slider.
5. In Terrain mode, use the **Sculpt Tool** to paint grooves or flatten areas for villages.

### 2. Copy the Code
1. Click the bright white `</>` button in the top right to open the Code Panel.
2. Click **Copy**. The code is now on your clipboard.

### 3. Prompt Your AI
Go to ChatGPT, Claude, or your AI coding assistant and say:
> *"I am building a 3D game. Here is the Three.js code for a custom asset/terrain I designed. Please add this exact model to my game scene: [Paste Code Here]"*

---

## 🛠️ Tech Stack
*   **Three.js:** WebGL rendering and geometry generation.
*   **Vanilla JS:** No heavy frameworks, just fast, raw logic.
*   **CSS:** Custom flat-design 2026 UI with no gradients, just clean matte panels.

## 🚀 Deployment
This app is deployed on Vercel and hosted on GitHub. It runs entirely client-side, meaning it works completely offline once loaded!
