# 🎮 3D Tank Battle - Python OpenGL Game

A fully-featured 3D tank combat game built from scratch using **Python** and **PyOpenGL**, featuring real-time physics, advanced AI, and immersive graphics. Created as a Computer Graphics course project at BRAC University (CSE423).

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![OpenGL](https://img.shields.io/badge/OpenGL-3.0+-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

---

## 📋 Overview

**3D Tank Battle** is an engaging real-time strategy game where players control a blue tank to engage in combat against an AI-controlled red tank. The game demonstrates advanced computer graphics concepts including 3D transformations, physics simulation, collision detection, and AI behavior systems—all implemented without relying on a traditional game engine.

### Key Highlights
- **Real-time 3D Graphics** rendered using OpenGL
- **Physics-based Projectiles** with realistic trajectory and collision
- **Intelligent AI System** using Finite State Machines
- **Dynamic Explosion Effects** with particle systems
- **Health Management** with visual feedback
- **Smooth Camera System** for optimal gameplay viewing

---

## 🎮 Gameplay Features

| Feature | Description |
|---------|-------------|
| **Player-Controlled Blue Tank** | WASD movement, mouse-controlled turret aiming, spacebar for firing |
| **AI Red Tank Opponent** | Smart enemy with state-based decision making and strategic positioning |
| **Real-time Projectiles** | Physics-based projectiles with gravity simulation and collision detection |
| **Health System** | Visual health bars for both player and AI tanks; game ends when health reaches zero |
| **Explosion Effects** | Dynamic particle effects triggered on projectile impacts |
| **3D Terrain & Objects** | Fully rendered 3D battle environment with tanks, projectiles, and visual elements |
| **Smooth Camera System** | Third-person or customizable camera view for enhanced gameplay experience |
| **Finite State Machine AI** | Intelligent enemy behavior with patrol, chase, and attack modes |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| ![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white) | Core game logic and scripting |
| ![OpenGL](https://img.shields.io/badge/-OpenGL-ED8936?logo=opengl&logoColor=white) | 3D graphics rendering |
| ![PyOpenGL](https://img.shields.io/badge/-PyOpenGL-4A90E2?logoColor=white) | Python OpenGL bindings |
| ![NumPy](https://img.shields.io/badge/-NumPy-013243?logo=numpy&logoColor=white) | Mathematical computations and matrix operations |

---

## 📁 Project Structure

```
3D-Tank-Battle-in-Python-OpenGL-Player-vs-AI-with-projectiles-explosions-and-smart-enemy-AI/
│
├── README.md                 # Project documentation (this file)
├── main.py                  # Main game loop and initialization
├── tank.py                  # Tank class and player tank logic
├── ai_enemy.py              # AI tank implementation with FSM
├── projectile.py            # Projectile physics and collision
├── camera.py                # Camera system and view management
├── explosion.py             # Particle effects and explosions
├── terrain.py               # 3D terrain and world objects
├── physics.py               # Physics engine and collision detection
├── utils.py                 # Utility functions and helpers
├── shaders/                 # GLSL shader files
│   ├── vertex_shader.glsl
│   ├── fragment_shader.glsl
│   └── particle_shader.glsl
├── assets/                  # Game assets (textures, models)
│   └── models/
└── requirements.txt         # Python dependencies
```

---

## 🚀 Installation & Setup

### Prerequisites
- **Python 3.8+** installed on your system
- **pip** (Python package manager)
- A graphics card with **OpenGL 3.0+** support

### Step 1: Clone the Repository
```bash
git clone https://github.com/OmorChowdhury/3D-Tank-Battle-in-Python-OpenGL-Player-vs-AI-with-projectiles-explosions-and-smart-enemy-AI.git
cd 3D-Tank-Battle-in-Python-OpenGL-Player-vs-AI-with-projectiles-explosions-and-smart-enemy-AI
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

Or manually install required packages:
```bash
pip install PyOpenGL NumPy PyGame
```

### Step 3: Run the Game
```bash
python main.py
```

The game window should launch, and you can begin playing immediately.

---

## 🎮 Keyboard Controls

| Key | Action |
|-----|--------|
| **W** | Move tank forward |
| **A** | Rotate tank left |
| **S** | Move tank backward |
| **D** | Rotate tank right |
| **Mouse Movement** | Aim turret up/down and rotate left/right |
| **Left Click** / **Spacebar** | Fire projectile |
| **C** | Switch camera mode |
| **ESC** | Pause game / Exit |
| **R** | Restart game |
| **V** | Toggle velocity vectors (debug) |

---

## 🤖 AI Behavior System

The AI tank employs a **Finite State Machine (FSM)** architecture with three primary states:

### 1. **Patrol State** 🚶
- **Activation**: When the player tank is not visible or far away
- **Behavior**: AI moves randomly around the map in predefined patterns
- **Purpose**: Creates natural, non-static enemy presence
- **Transition**: Switches to **Chase State** when player enters detection radius

### 2. **Chase State** 🏃
- **Activation**: Player tank enters AI's vision range (e.g., within 50 units)
- **Behavior**: AI pursues the player using pathfinding and direct approach
- **Purpose**: Aggressive engagement phase with strategic positioning
- **Transition**: Switches to **Attack State** when within firing range; returns to **Patrol** if player escapes

### 3. **Attack State** 💥
- **Activation**: Player tank enters firing range (e.g., within 20 units)
- **Behavior**: AI calculates optimal firing angle accounting for:
  - Distance to target
  - Projectile physics and gravity
  - Lead prediction for moving targets
  - Environmental obstacles
- **Purpose**: Maximizes hit probability through intelligent targeting
- **Transition**: Returns to **Chase State** if target moves out of range; **Patrol** if contact is lost

### AI Decision Logic
```
IF distance_to_player < detection_radius:
    ENTER Chase State
    IF distance_to_player < firing_range:
        ENTER Attack State
        Calculate optimal firing angle with physics prediction
        Fire when confidence > threshold
ELSE:
    ENTER Patrol State
    Execute random movement pattern
```

### Advanced AI Features
- **Predictive Targeting**: Calculates lead angle for moving targets
- **Collision Avoidance**: Navigates around terrain and obstacles
- **Energy Management**: Considers ammunition and health status
- **Adaptive Difficulty**: Behavior adjusts based on player actions

---

## 🎯 How to Play

1. **Start the Game**: Run `python main.py` to launch the game
2. **Control Your Tank**: Use WASD keys to move and mouse to aim your turret
3. **Fire Projectiles**: Press Spacebar or Left Click to shoot at the enemy tank
4. **Monitor Health**: Watch the health bars at the top of the screen
5. **Survive & Defeat**: Reduce the AI tank's health to zero while protecting your own
6. **Victory**: Win the game by being the last tank standing

### Winning Strategy Tips
- Use terrain as cover from enemy fire
- Anticipate AI movement patterns and predict firing angles
- Lead your shots to hit the moving AI tank
- Maintain distance when low on health
- Circle the AI tank to find optimal firing positions

---

## 💡 Technical Highlights

### Graphics Rendering
- **Custom OpenGL Pipeline**: Built without game engines for maximum control
- **3D Model Rendering**: Tank models, terrain, and environmental objects
- **Shader Programs**: Vertex and fragment shaders for advanced visual effects
- **Particle System**: Real-time particle effects for explosions and visual feedback

### Physics Engine
- **Projectile Trajectory**: Accurate gravity and air resistance simulation
- **Collision Detection**: AABB (Axis-Aligned Bounding Box) and sphere collision
- **Movement Physics**: Realistic tank acceleration and rotation

### AI System
- **State Machine Architecture**: Clean separation of AI behaviors
- **Pathfinding**: Efficient route calculation avoiding obstacles
- **Predictive Targeting**: Advanced ballistics calculations for accurate firing

---

## 📊 Performance Metrics

- **Target Frame Rate**: 60 FPS (1280x720 resolution)
- **Physics Updates**: 60 physics ticks per second
- **AI Update Frequency**: 30 AI decisions per second
- **Average Memory Usage**: ~150-200 MB

---

## 🎓 Educational Context

This project was developed for **CSE423 Computer Graphics** at BRAC University, demonstrating:
- 3D coordinate transformations and projections
- OpenGL graphics pipeline understanding
- Physics simulation principles
- Game AI design patterns
- Real-time performance optimization
- Software architecture and design patterns

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs and issues
- Suggest new features
- Submit pull requests with improvements
- Fork the repository and create your own enhancements

### Areas for Enhancement
- Multiplayer networking support
- Additional tank models and customization
- Enhanced particle effects and shaders
- Sound effects and background music
- Level design with multiple arenas
- Difficulty settings and game modes

---

## 📝 License

This project is licensed under the **MIT License** - see the LICENSE file for details.

---

## 📧 Author & Contact

- **Author**: Omor Chowdhury
- **GitHub**: [@OmorChowdhury](https://github.com/OmorChowdhury)
- **Institution**: BRAC University
- **Course**: CSE423 - Computer Graphics

---

## 🙏 Acknowledgments

- BRAC University CSE423 Computer Graphics Course
- PyOpenGL and OpenGL communities
- NumPy and Python scientific computing ecosystem
- All contributors and testers

---

## 🔧 Troubleshooting

### Common Issues

**Issue**: `ImportError: No module named 'OpenGL'`
- **Solution**: Run `pip install PyOpenGL` to install the required package

**Issue**: Game window won't display
- **Solution**: Ensure your graphics drivers are up to date; try updating your GPU drivers

**Issue**: Low frame rate or stuttering
- **Solution**: Try lowering the resolution or reducing particle effect quality in settings

**Issue**: AI not behaving correctly
- **Solution**: Check console for errors; ensure all AI modules are properly imported

For additional support, please open an issue on the GitHub repository.

---

## 📚 Resources & References

- [OpenGL Documentation](https://www.khronos.org/opengl/)
- [PyOpenGL Tutorials](http://pyopengl.sourceforge.net/)
- [Python Documentation](https://docs.python.org/3/)
- [Game AI: Finite State Machines](https://en.wikipedia.org/wiki/Finite-state_machine)
- [3D Graphics Programming Fundamentals](https://learnopengl.com/)

---

**Last Updated**: May 2026  
**Version**: 1.0.0

---

*Made with ❤️ for Computer Graphics enthusiasts*
