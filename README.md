# 🐍 Snake Game

<p align="center">
  A classic Snake Game developed in C++ using SDL2.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%2B%2B-17%2B-blue?style=for-the-badge&logo=cplusplus" alt="C++">
  <img src="https://img.shields.io/badge/SDL2-Game%20Development-green?style=for-the-badge" alt="SDL2">
  <img src="https://img.shields.io/badge/Platform-Desktop-orange?style=for-the-badge" alt="Platform">
</p>

---

## 📌 Overview

**Snake Game** is a simple desktop-based arcade game developed using **C++** and the **SDL2 (Simple DirectMedia Layer)** library.

The player controls a continuously moving snake using the keyboard arrow keys. The objective is to collect food, increase the snake's length, and achieve the highest possible score without colliding with the snake's body or the game window boundaries.

The project demonstrates fundamental concepts of **C++ programming, game loops, event handling, collision detection, dynamic data structures, and 2D rendering**.

---

## 🎮 Features

* 🐍 Real-time snake movement
* ⌨️ Arrow-key controls
* 🍎 Food generation
* 📈 Dynamic score tracking
* 📏 Snake growth after eating food
* 💥 Self-collision detection
* 🧱 Boundary collision detection
* 🖥️ SDL2-based graphical interface
* ⚡ Real-time game loop
* 🚫 Prevents immediate movement in the opposite direction

---

## 🛠️ Technology Stack

| Technology       | Purpose                                |
| ---------------- | -------------------------------------- |
| **C++**          | Core game logic                        |
| **SDL2**         | Graphics, window management, and input |
| **STL Vector**   | Dynamic snake segment storage          |
| **SDL_Event**    | Keyboard and window event handling     |
| **SDL_Renderer** | 2D game rendering                      |

---

## 🧩 Game Architecture

The game is organized around three main functions:

```text
                    ┌─────────────────┐
                    │    Main Loop    │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              ↓              ↓              ↓
        Event Handling    Game Update     Rendering
              │              │              │
              ↓              ↓              ↓
         Keyboard Input   Movement &       Snake
                          Collision        + Food
                             │
                             ↓
                       Score & Growth
```

### Main Components

#### `main()`

Responsible for:

* Initializing SDL2
* Creating the game window
* Creating the renderer
* Processing game events
* Running the main game loop
* Updating game state
* Rendering game objects
* Cleaning up SDL resources

#### `render()`

Responsible for drawing:

* Snake segments
* Food
* Current score

#### `update()`

Responsible for:

* Updating the snake's position
* Detecting food consumption
* Increasing the snake length
* Generating new food
* Updating the score
* Checking collisions

#### `checkCollision()`

Checks whether the snake:

* Hits its own body
* Moves outside the game boundaries

---

## 🎯 Gameplay

The game starts with a single snake segment.

```text
        🐍
        ↓
    Move with
   Arrow Keys
        ↓
     Find Food
        ↓
    Eat Food
        ↓
   Snake Grows
        ↓
   Score +1
```

### Controls

| Key | Action     |
| --- | ---------- |
| `↑` | Move Up    |
| `↓` | Move Down  |
| `←` | Move Left  |
| `→` | Move Right |

The game prevents the snake from immediately reversing direction.

For example:

```text
Moving Right → Cannot immediately move Left
Moving Up    → Cannot immediately move Down
```

---

## 📊 Scoring System

The score increases by **1 point** every time the snake successfully eats food.

```cpp
score++;
```

The current score is displayed during gameplay, and the final score is printed when the game ends.

```text
Game Over! Score: 10
```

---

## 💥 Collision Detection

The game implements two types of collision detection.

### 1. Self Collision

The program checks whether the new snake head position overlaps with any existing body segment.

```cpp
if (snake[i].x == x && snake[i].y == y)
```

If a collision occurs, the game ends.

### 2. Boundary Collision

The snake cannot move outside the game window.

```cpp
return (x >= SCREEN_WIDTH / BLOCK_SIZE ||
        x < 0 ||
        y >= SCREEN_HEIGHT / BLOCK_SIZE ||
        y < 0);
```

---

## 🍎 Food Generation

When the snake eats the food, a new food position is generated randomly within the game area.

```cpp
food.x = rand() % (SCREEN_WIDTH / BLOCK_SIZE);
food.y = rand() % (SCREEN_HEIGHT / BLOCK_SIZE);
```

This allows the food to appear at different locations during gameplay.

---

## 🧱 Game Configuration

The game uses the following configuration:

```cpp
const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
const int BLOCK_SIZE = 20;
```

This creates a grid-based game area of:

```text
32 columns × 24 rows
```

The snake and food are rendered using `20 × 20` pixel blocks.

---

## 🔄 Game Loop

The game continuously executes the following cycle:

```text
┌───────────────────────┐
│     Start Game        │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Process User Events   │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Update Game State     │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Check Collisions      │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Render Snake & Food   │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Display Updated Frame │
└───────────┬───────────┘
            ↓
        Repeat
```

A small delay is used to control the movement speed:

```cpp
SDL_Delay(100);
```

---

## 📂 Project Structure

```text
Snake-Game/
│
├── main.cpp
└── README.md
```

> If your source file has a different name, replace `main.cpp` with the actual filename.

---

## ⚙️ Requirements

Before running the project, install:

* C++ compiler
* SDL2 development library
* Standard C++ library

The project can be compiled using compilers such as:

* GCC / MinGW
* Clang
* Visual Studio

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
```

### 2. Navigate to the Project

```bash
cd Snake-Game
```

### 3. Configure SDL2

Make sure the SDL2 development libraries are correctly installed and configured for your compiler.

### 4. Compile

For a MinGW-based setup, a typical command is:

```bash
g++ main.cpp -o SnakeGame -lmingw32 -lSDL2main -lSDL2
```

### 5. Run

```bash
./SnakeGame
```

On Windows:

```bash
SnakeGame.exe
```

> The exact compilation command may vary depending on your SDL2 installation and compiler configuration.

---

## 🧠 Concepts Demonstrated

This project provides practical implementation of:

* C++ fundamentals
* Structures
* STL `vector`
* Functions and function prototypes
* References
* Loops
* Conditional statements
* `switch` statements
* Event-driven programming
* Game loops
* 2D coordinate systems
* Collision detection
* Random number generation
* Real-time rendering
* Keyboard input handling
* SDL2 window and renderer management
* Resource cleanup

---

## 🔮 Future Enhancements

The project can be extended with:

* 🎵 Background music and sound effects
* 🏆 High-score system
* ⏱️ Increasing difficulty and speed
* ⏸️ Pause and resume functionality
* 🔄 Restart button
* 🎨 Improved graphics and animations
* 🧱 Obstacles and multiple levels
* 🥇 Persistent leaderboard
* 🎮 Additional keyboard controls
* 📱 Improved cross-platform support

---

## 📈 Learning Outcomes

This project strengthened practical understanding of **C++ game development** and **SDL2-based graphical programming**.

Key areas include:

```text
C++
 ↓
SDL2
 ↓
Event Handling
 ↓
Game Loop
 ↓
Rendering
 ↓
Collision Detection
 ↓
Game State Management
```

---

## 👩‍💻 Author

**Israt Jahan Chadni**

GitHub: [@ichadni](https://github.com/ichadni)

---

<p align="center">
  ⭐ If you found this project useful, consider giving the repository a star.
</p>
