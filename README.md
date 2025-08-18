# TFL_Symbol_Tetris
A tetris-like game for intro logic students to memorize TFL Symbols and characteristic truth tables

# 🧠 Intro Logic Memorization Game — Design + Implementation Notes

## 🎯 Goal

Create a simple and fun web-based game to help intro symbolic logic students memorize:

- The mapping between **logical symbols** and their **English connective names**  
- The **characteristic truth tables** for the TFL connectives

The game uses a Tetris-like mechanic to provide spaced repetition under mild time pressure.

---

## 🕹️ Core Gameplay (all levels)

- A **piece** falls from the top of the screen into one of five columns.
- The **bottom slots** represent logical categories (either English names or truth-table rows).
- **Player controls:**  
  - `← / →` arrow keys to move the falling piece  
  - `Spacebar` to drop it
- **Correct drop →** slot turns from grayscale → color (activated)
- **Incorrect drop →** a grey **stone block** grows in that column, and that slot’s activation is reset
- **Combo rule:**  
  When **all 5 slots are activated at once**, the **lowest row of stone blocks crumbles**, all activations reset

**Lose condition:** stone column in any slot reaches the top  
**Win condition:** all pieces in the level have been handled (see progress bar)

---

## 🔄 Fall Speed / Difficulty Ramp

Each level starts with a **slow fall speed** (e.g. 1.5s/block) and increases by **+3% per handled block**.

---

## 📈 Progress Tracking (Weighted Progress Bar)

Each level has **30 pieces**.

Let:
- `baseFallTime = 1.5s`
- `speedRamp = 1.03` (3% increase)

**Before level starts:**

```js
totalDropTime = 0;
for (let i = 0; i < totalPieces; i++) {
  let dropTime = baseFallTime * Math.pow(speedRamp, i);
  totalDropTime += dropTime;
}
handledDropTime = 0;


# Sound Assets

| File         | Source                  | License |
|--------------|--------------------------|--------|
| chime-95842.mp3   | pixabay.com    | CC0    |
| cinematic-thud-fx-379991.mp3     | pixabay.com     | CC0    |
| rocks-6129.mp3  | pixabay.com    | CC0    |





