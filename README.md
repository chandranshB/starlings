# Nature's Cycle: Boids Flocking Simulation

A beautiful art experiment simulating the complex, emergent behavior of starling murmurations. This project demonstrates how simple, local interaction rules can give rise to sophisticated global group behavior, implemented entirely in vanilla JavaScript without external physics or rendering engines.

**[View Live Demo](https://chandranshB.github.io/starlings)**

-----

## 🚀 Technical Highlights

This project showcases proficiency in **Canvas API**, **Vector Mathematics**, and **Algorithmic Design**.

  * **Zero Dependencies:** Built purely with HTML5 Canvas and Vanilla ES6+ JavaScript. No frameworks or libraries were used, ensuring a lightweight and highly performant footprint.
  * **Custom Physics Engine:** Implemented a scratch-built physics system handling velocity, acceleration, and steering forces to create fluid, organic movement.
  * **Emergent Behavior Algorithms:** Applied the **Boids algorithm** (Reynolds, 1986) to simulate flocking. The logic computes three key vectors for every frame:
    1.  **Separation:** Steer to avoid crowding local flockmates.
    2.  **Alignment:** Steer towards the average heading of local flockmates.
    3.  **Cohesion:** Steer to move toward the average position (center of mass) of local flockmates.
  * **Procedural Animation:** Bird wing flapping is procedurally generated using sine waves relative to the frame time, independent of the physics calculations.

## 🛠️ Technologies

  * **Core:** HTML5, CSS3
  * **Rendering:** HTML5 Canvas API (2D Context)
  * **Language:** JavaScript (ES6 Classes)

## ⚙️ How It Works

### The Physics Loop

The simulation runs on a custom `update()` loop that calculates forces for every entity ("boid") based on its perception radius.

```javascript
// Excerpt from the steering logic
steer(target) {
    // Calculate vector to target
    let d = Math.sqrt(target.x**2 + target.y**2);
    
    // Normalize and scale to max speed
    target.x = (target.x / d) * CONFIG.maxSpeed;
    target.y = (target.y / d) * CONFIG.maxSpeed;

    // Reynolds' steering formula: Steering = Desired - Velocity
    let steer = { x: target.x - this.vel.x, y: target.y - this.vel.y };
    
    // Limit force to ensure realistic turning radius
    // ... (clamping logic)
    return steer;
}
```

### Configuration

The simulation is data-driven and easily tweakable via the `CONFIG` object, allowing for rapid prototyping of different physics behaviors (e.g., tighter flocks vs. chaotic swarms).

```javascript
const CONFIG = {
    count: 100,           // Population size
    perception: 100,      // Vision radius
    separation: 30,       // Personal space bubble
    maxSpeed: 3.5,        // Velocity cap
    alignW: 1.2,          // Weight for alignment rule
    cohesionW: 0.01,      // Weight for cohesion rule
    separationW: 1.5      // Weight for separation rule
};
```

## 🎨 Visual Design

  * **Atmosphere:** A responsive radial gradient background (`#1e293b` to `#020617`) creates depth and mimics a twilight sky.
  * **Rendering:** Birds are drawn using `quadraticCurveTo` for smooth Bezier curves, creating a stylized, organic shape rather than simple primitives.
  * **Responsive UI:** The canvas resizes dynamically with the window, and the UI layer uses Flexbox for perfect centering across devices.

## 📦 Getting Started

1.  Clone the repository:
    ```bash
    git clone https://github.com/chandranshb/starlings.git
    ```
2.  Navigate to the directory and open `index.html` in any modern web browser. No build step or server is required.

## 📄 License

[MIT License](https://www.google.com/search?q=LICENSE)

-----

*Created by [Shandran](https://www.google.com/search?q=https://github.com/chandranshb)*
