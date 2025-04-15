# 🎮 2048 - Open Source Project Exploration

![2048 Gameplay](https://raw.githubusercontent.com/gabrielecirulli/2048/master/meta/og-image.png)

---

## 📌 Overview

This repository contains a comprehensive analysis and presentation of the open source project [2048](https://github.com/gabrielecirulli/2048), a web-based sliding tile puzzle game developed by Gabriele Cirulli.

The goal of this project was to:
- Understand the inner workings of the 2048 codebase.
- Explore its data structures, game logic, and design decisions.
- Contribute or identify potential improvements.
- Prepare a Markdown-based presentation on our findings.

---

## 🔍 Project Objectives

- Clone and investigate the 2048 codebase using modern tools.
- Analyze the breadth and depth of the architecture.
- Optionally raise a bug or contribute a fix/feature via PR.
- Present our findings in a clear and concise format.

---

## 🏗️ Codebase Structure

```plaintext
2048/
│
├── index.html                 → Game layout and entry point
├── style/
│   └── main.css               → Styling for the game grid and tiles
├── js/
│   ├── game_manager.js        → Core logic: movement, merging, game status
│   ├── grid.js                → Grid representation and operations
│   ├── tile.js                → Tile object definition
│   ├── keyboard_input_manager.js → Captures keyboard input
│   ├── html_actuator.js       → Updates DOM to reflect game state
│   └── local_storage_manager.js → Saves and retrieves state from localStorage
