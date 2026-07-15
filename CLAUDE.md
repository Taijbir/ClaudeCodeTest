# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Battleship — Naval Combat Sim** is a single-file implementation of the classic Battleship game, playable directly in a web browser. The game features a deployment phase where the player arranges ships, followed by a battle phase against an AI opponent.

## Running the Game

- Open `battleship.html` directly in a web browser to play.
- No build step, server, or dependencies required — it's a self-contained HTML file.

## Architecture

The entire game is implemented in a single HTML file with three main sections:

1. **HTML Structure** — Game UI elements:
   - Deployment phase: ship placement interface with grid, ship roster, and rotation controls
   - Battle phase: player and enemy grids for attacking
   - Game over overlay with results and restart button

2. **CSS** — Styling with:
   - CSS custom properties (theme variables) for light/dark mode support
   - Responsive grid-based layout using `clamp()` for scaling
   - Visual states for cells: water, hits, misses, sunk ships
   - Naval/tactical design aesthetic

3. **JavaScript** — Game logic (wrapped in IIFE):
   - Board/ship state management
   - Ship placement and validation
   - Turn-based combat and AI opponent logic
   - Sound effects (basic beep-style audio generation)
   - Event handling for grid clicks and button interactions

## Key Game Logic

- **Ship Placement**: Players drag/click to position ships on the grid; validation ensures no overlaps
- **Combat**: Players click enemy grid cells to attack; hits/misses are tracked and displayed
- **AI**: Enemy uses basic targeting strategy (random + adjacent search after a hit)
- **Win Condition**: First player to sink all opponent ships wins

## Theme Support

The game respects `prefers-color-scheme` media query and also supports manual theme toggle via `data-theme` attribute on the root element.

## Modifying the Game

If adding features or fixing bugs:
- Ship types/sizes are defined in the ship roster (adjust `makeShipsStatus()` to change)
- Grid size is hardcoded as 10x10; changing it requires updates to cell dimensions and board logic
- Sound effects are generated with Web Audio API; modify `sfx` object for different sounds
- CSS variables control the entire color scheme — update `:root` to change aesthetics
