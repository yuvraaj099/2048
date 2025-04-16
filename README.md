# 🎓 2048 Game - Open Source Project Analysis & Presentation

## 👨‍🎓 Student Submission  
This document is part of our submission for the Open Source Project Exploration assignment. We have selected the open-source **2048 Game** as our project. The repository was explored, analyzed, and understood using modern tooling such as GitHub and LLMs (like ChatGPT).

---

## 📌 Project Overview

**2048** is a sliding tile puzzle game where the player uses arrow keys to combine tiles with the same number, aiming to reach the number 2048. The game logic is simple but involves thoughtful design in handling inputs, grid manipulation, and game state updates.

- **Original Creator**: Gabriele Cirulli  
- **Technologies Used**: HTML, CSS, JavaScript  
- **Repository Type**: Client-side Web App  
- **License**: MIT  

This project provided a suitable balance between simplicity and complexity — ideal for individual analysis and understanding.

---

## 🎯 Objectives Fulfilled

- Cloned and understood the project (`2048-master`)
- Investigated game logic with help from LLM tools
- Performed **breadth-wise and depth-wise analysis**
- Documented findings in this README and markdown presentation
<!-- - (Optional) Attempted bug/PR contribution (if applicable) -->

---

## 📚 Evaluation Criteria Breakdown

### 1.  Breadth-wise Understanding of the Project

- The project is structured into HTML, CSS, and JavaScript files.
- Core game logic resides in `game_manager.js`, which handles user input, tile merging, game state, and rendering.
- Code is modular, separating UI and logic cleanly.
- External libraries (e.g., `classlist.js`) are used to enhance cross-browser compatibility.

---

### 2.  Depth-wise Analysis

### - Approaches Taken

- **MVC-like Separation**: Logic (`game_manager.js`), view (`html/css`), and control (event listeners in `keyboard_input_manager.js`) are separated.
- **Event-driven input**: Arrow keys are captured via `KeyboardInputManager` and processed to update the board.
- **Tile merging** is handled in a loop, checking for matches and applying logic accordingly.

### - Data Structures Used

- **Grid**: Represented as a 2D array, initialized with zeros or tile objects.
- **Tile**: A JavaScript object with properties like `value`, `position`, and `mergedFrom`.
- **LocalStorageManager**: Used to persist high scores using local browser storage.

### - Trade-offs Made

- **Performance vs Simplicity**: Logic is written in a readable and modular way rather than overly optimized.
- **In-browser storage** chosen over backend storage to keep things simple and fast.
- UI rendering uses simple DOM manipulation, avoiding complex frameworks to maintain portability.

---

## Project Structure

```
2048-master/
├── index.html                   # Main HTML file
├── style/
│   └── main.css                 # CSS for UI and animation
├── js/
│   ├── game_manager.js          # Core logic (grid state, movements)
│   ├── grid.js                  # Grid object and manipulation
│   ├── tile.js                  # Tile creation and merge tracking
│   ├── keyboard_input_manager.js # Handles user input
│   ├── html_actuator.js         # Updates DOM with game state
│   └── local_storage_manager.js # Stores high score in browser
```

- **Modular design**: Every file has a clear, single responsibility.
- **Separation of Concerns**: Logic, input handling, UI updates, and storage are separated cleanly.

---

## ⚙️ Core Logic Breakdown

### -> Game Flow

1. Game initializes with two tiles.
2. User presses arrow key → movement is captured.
3. Grid is updated → tiles move/merge.
4. New tile is spawned randomly.
5. Game checks for win/loss.

---

### -> Important Modules

#### `game_manager.js`
- Controls game state
- Handles keypress logic and tile movements
- Invokes grid, tile, and actuator functions

#### `grid.js`
- 4x4 matrix logic
- Keeps track of cell states
- Provides available cell calculations

#### `tile.js`
- Object for tile with:
  - Position
  - Value
  - Merge history

#### `keyboard_input_manager.js`
- Binds arrow key events
- Converts keycodes to movement commands

#### `html_actuator.js`
- DOM manipulation
- Adds CSS classes to animate tiles
- Updates score and game messages

---

## 💻 Key Code Snippets

### -> Merging Tiles

```js
if (target && target.value === tile.value && !target.mergedFrom) {
  var merged = new Tile(targetPosition, tile.value * 2);
  merged.mergedFrom = [tile, target];

  this.grid.insertTile(merged);
  this.grid.removeTile(tile);
}
```

> Logic that merges two matching tiles and creates a new one with double the value.

---

### -> Handling Arrow Keys

```js
var map = {
  38: 0, // Up
  39: 1, // Right
  40: 2, // Down
  37: 3  // Left
};

window.addEventListener("keydown", function (event) {
  var mapped = map[event.which];
  if (mapped !== undefined) self.emit("move", mapped);
});
```

> Maps arrow key presses to direction codes, emitting a move event.

---

## ❓ Key Questions Asked (and Answered)

### -> How is a move processed?
- Captured via `keyboard_input_manager.js`
- Passed to `game_manager.js` which calculates new tile positions

### -> How is the grid updated?
- The `grid.js` file contains functions like `moveTile`, `withinBounds`, and `availableCells` to update positions.

### -> How are merges tracked?
- Each `Tile` object has a `mergedFrom` field to track which tiles merged into it — important for animations and scoring.

### -> What makes the game visually responsive?
- Animations and UI updates are managed in `html_actuator.js` using class-based DOM manipulation.

---

## 🔍 Learnings & Reflections

- **LLMs** helped explain complex logic quickly (e.g., grid movement and tile merging).
- Modular JS files made it easier to understand each part in isolation.
- The project is a great example of **clean front-end architecture**.
- Areas for improvement:
  - Could add TypeScript for better type safety
  - Backend-based leaderboard with Firebase

---

<!-- ## ✅ Summary Table

| Aspect         | Understanding |
|----------------|---------------|
| Code Structure | ✅             |
| Logic Flow     | ✅             |
| UI Interaction | ✅             |
| Trade-offs     | ✅             |
| QnA Prepared   | ✅             |

--- -->

## 🧾 Credits

- Original 2048 by [Gabriele Cirulli](https://github.com/gabrielecirulli/2048)
