# SolarSystem3D

🪐 JARVIS Solar System Explorer
An Interactive 3D WebGL Simulation built with Three.js

📖 Overview
The JARVIS Solar System Explorer is a real-time, interactive 3D visualization of our solar system running directly in the browser. Inspired by the Iron Man HUD (Heads Up Display) aesthetic and the atmosphere of Interstellar, this project bridges the gap between raw scientific data and cinematic user experience.
It leverages Three.js to render high-fidelity textures, orbital mechanics, and lighting effects, while ensuring optimal performance on both desktop and mobile devices.

✨ Key Features
 * 🚀 Immersive 3D Environment: Full 360° orbit controls with zoom and pan capabilities.
 * 💻 Sci-Fi HUD Interface: A "JARVIS"-inspired UI using neon cyan typography (Orbitron & Rajdhani fonts) and glass-morphism effects.
 * ☀️ "Bulletproof" Rendering: Utilizes MeshBasicMaterial for the Sun to guarantee visibility and vibrant yellow emission regardless of lighting conditions or texture loading failures.
 * 👆 Raycasting Interaction: Interact with planets via click/tap. The camera smoothly interpolates (Lerps) to focus on the selected celestial body.
 * 📊 Dynamic Bio-Data: Real-time informational overlays displaying mass, gravity, temperature, and orbital period for every planet.
 * 🎵 Atmospheric Audio: Integrated background ambient music ("Cornfield Chase" vibes) with a user-interaction trigger to bypass browser autoplay policies.
 * 📱 Mobile Optimized: Responsive canvas resizing, touch controls, and optimized geometry for smooth frame rates on smartphones.
   
🛠️ Technical Architecture
1. The Rendering Pipeline
 * Engine: Three.js (r160) via ES Modules.
 * Camera: PerspectiveCamera with a 60° field of view, starting at a high-angle offset (0, 60, 90).
 * Lighting: A complex lighting rig comprising:
   * PointLight (at Center): Simulates the Sun's emission.
   * AmbientLight: High intensity to ensure visibility of outer planets (Uranus/Neptune).
   * DirectionalLight (Rim Light): Adds depth and a sci-fi blue contour to objects.
     
2. Materials & Textures
 * The Sun: Uses a MeshBasicMaterial with a hex color of #FFD700 (Gold). This bypasses the lighting calculation to ensure the Sun is always the brightest object in the scene, fixing common "black texture" bugs on mobile networks.
 * Planets: Use MeshStandardMaterial with Roughness 0.4 and Metalness 0.2 to react realistically to the sun's light. Textures are loaded asynchronously via TextureLoader.
   
3. Orbital Mechanics
The simulation uses a render loop (requestAnimationFrame) to update planetary positions based on trigonometric functions:
// Simplified logic
planet.angle += planet.speed;
planet.x = Math.cos(planet.angle) * planet.distance;
planet.z = Math.sin(planet.angle) * planet.distance;

This creates mathematically perfect circular orbits.

4. Interaction Logic (Raycasting)
Instead of simple DOM events, interaction is handled via 3D Raycasting:
 * Mouse/Touch coordinates are normalized to a (-1 to +1) vector.
 * A ray is cast from the camera through the mouse position.
 * If the ray intersects a planet mesh, the focusTarget is updated.
 * The camera uses Linear Interpolation (Lerp) to smoothly glide to the new target.
   
🚀 How to Run Locally
This project is built as a Single File Application for simplicity. You do not need Node.js or a build step.
 * Clone the repository:
   git clone https://github.com/YOUR_USERNAME/jarvis-solar-system.git

 * Open the file:
   Simply double-click index.html to open it in your browser.
 * Preferred Method (VS Code):
   For texture security policies (CORS), it is best to run it via a local server.
   * Install the Live Server extension in VS Code.
   * Right-click index.html -> "Open with Live Server".
     
📂 Project Structure
.
├── SolarSystem3D.html       # Contains HTML, CSS (in <style>), and JS (in <script>)
├── assets/          # (Optional) If you choose to download textures locally
└── README.md        # This file

🔮 Future Improvements
 * [ ] Add elliptical orbits (Keplerian physics).
 * [ ] Implement texture mapping for the Moon.
 * [ ] Add asteroid belts using InstancedMesh for performance.

🤝 Credits
 * Textures: Three.js Planet Textures
 * Audio: Interstellar Theme (Hans Zimmer) / Pixabay
Created by Syed Ismail N.
Master's in Data Science and AI Student | AI Enthusiast | Creative Developer



