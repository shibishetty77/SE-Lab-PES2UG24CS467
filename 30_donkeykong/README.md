# Donkey Kong Repair Lab

This project is a single-file Donkey Kong-lite clone using **Pygame**. It introduces students to sloped-platform physics, ladder climbing, and gravity using a small, readable object-oriented codebase.

---

## What's Provided

A working Donkey Kong-lite game with:

- A player-controlled climber with jumping and gravity that follows sloped platforms
- Ladders connecting each platform level that the player can climb
- Barrels that roll down sloped platforms and occasionally descend a ladder to the level below
- Lives, scoring, and a win condition for reaching the princess

It has **one deliberate bug** and **three optional features** left as empty functions. You are expected to **analyze**, **interact with an AI assistant**, and **complete/fix** the game to make it fully functional and more interesting.

### **Use an LLM (e.g. ChatGPT or Claude) as your debugging and pair-programming partner for this lab.**

---

## Getting Started

### Setup

1. Make sure you have Python 3.10+ installed.
2. Install dependencies:

```bash
pip install pygame
```

3. Run the game:

```bash
python game.py
```

**Controls:** Left/Right to move, Space to jump, Up/Down to grab a ladder while standing near it, `R` to reset.

---

## Tasks to Complete

Each task must be completed using an iterative process involving LLM suggestions and your critical code review.

### Task 1: Fix the ladder-descent bug

> Barrels are supposed to take a ladder down to the next platform only occasionally, so a few keep rolling across the top platform while others trickle down toward the player. In the current build, almost every barrel immediately takes the first ladder it reaches, so the lower platforms flood with barrels and the top platform empties out fast. Find the probability check that controls this in the `Barrel` class and correct it so barrels descend roughly 3 times out of 10, not roughly 7 times out of 10.

### Task 2: Implement `theme_color(score)`

> Called once per frame in `draw_scene` as `screen.fill(theme_color(score) or BG)`, where `BG` is the default navy background `(15, 15, 25)`. It receives the player's current integer score and should return an `(r, g, b)` tuple to use as the background color, or `None` to keep the default. Idea: shift toward a warmer color as the score climbs, or briefly flash a color right after a big score gain.

### Task 3: Implement `on_barrel_jumped(player, barrel)`

> Called from the main loop exactly once, on the first frame the player is airborne directly above a barrel — right after the 100-point jump bonus is awarded for that barrel. It receives the `Player` and the `Barrel` that was jumped. Its return value is ignored; it exists purely for side effects. Idea: spawn a short-lived floating "+100" label at the barrel's position, or play a sound.

### Task 4: Implement `score_multiplier(score)`

> Called right before the barrel-jump bonus is added, as `score += int(100 * (score_multiplier(score) or 1))`. It receives the score *before* the bonus is added and should return a numeric multiplier, or `None` for the default 1x. Idea: return `2` once the score passes some threshold, to reward late-game play.

---

## Expected Behavior

- The player follows the slope of each platform instead of floating above it or sinking into it
- The player can only climb a ladder while standing near that ladder's x-position, on the platform range it connects
- Barrels roll down slopes and occasionally (about 30% of the time) descend a ladder instead of continuing to roll along the platform
- Barrels never fall through platforms
- Reaching the princess ends the game with a win message; running out of lives (from barrel collisions) ends it with a game-over message

---

## Folder Structure

```
donkey_kong/
├── game.py
└── README.md
```

---

## Submission Checklist

Submission is only the following three things:

- [] A 10-second video of gameplay **before** your changes, showing the bug/broken behavior
- [] A 10-second video of gameplay **after** your changes, showing the bug fixed and the new features working
- [] The Chat/LLM used page link, with the complete chat history
