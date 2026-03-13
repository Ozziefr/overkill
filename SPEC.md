# OVERKILL CLONE - Game Specification

## 1. Project Overview

**Project Name:** CHAOS TRIGGER  
**Type:** Arcade Action Shooter (Overkill-style)  
**Core Functionality:** Fast-paced top-down shooter where the player fights waves of enemies using various weapons, collecting power-ups and upgrades.  
**Target Users:** Casual gamers who enjoy retro arcade action

---

## 2. UI/UX Specification

### Layout Structure

- **Canvas:** Full viewport game canvas (100vw x 100vh)
- **HUD Overlay:** Fixed position UI elements
  - Top-left: Health bar, Wave counter
  - Top-right: Score, Combo multiplier
  - Bottom: Ammo indicator, Current weapon icon
- **Start Screen:** Centered title, "PRESS ENTER TO START" prompt
- **Game Over Screen:** Final score, "PRESS ENTER TO RESTART"

### Visual Design

**Color Palette:**

- Background: `#0a0a0f` (deep black)
- Grid lines: `#1a1a2e` (dark blue-purple)
- Player: `#00ff88` (neon green)
- Player glow: `#00ff8855` (green glow)
- Enemies (basic): `#ff3366` (hot pink)
- Enemies (fast): `#ff6600` (orange)
- Enemies (tank): `#9933ff` (purple)
- Bullets (player): `#00ffff` (cyan)
- Bullets (enemy): `#ff0044` (red)
- Explosions: `#ffff00` → `#ff6600` → `#ff0000` (yellow to red gradient)
- Power-ups: `#ffdd00` (gold)
- Health bar: `#00ff88` (green) → `#ff0000` (red gradient based on health)
- UI Text: `#ffffff` (white)
- Score/Combo: `#ffcc00` (gold)

**Typography:**

- Primary font: `"Orbitron", sans-serif` (Google Font - futuristic)
- Score display: 32px bold
- HUD labels: 18px
- Title: 72px bold with glow effect

**Visual Effects:**

- Screen shake on player damage
- Particle explosions on enemy death
- Bullet trails with fade effect
- Scanline overlay for retro CRT feel
- Pulsing glow on player
- Enemy spawn flash

### Components

**Player Ship:**

- Triangle/arrow shape pointing in movement direction
- Size: 30px
- Glowing outline effect
- Thruster flame animation when moving

**Enemies:**

- Basic (circle): 20px, moves toward player, 1 HP
- Fast (diamond): 15px, faster movement, 1 HP, worth more points
- Tank (hexagon): 40px, slower, 5 HP, shoots back

**Power-ups:**

- Health恢复: Green cross icon
- Rapid Fire: Red lightning bolt
- Spread Shot: Blue triple-bullet
- Shield: Cyan bubble

**Bullets:**

- Player bullets: 8px cyan rectangles with trail
- Enemy bullets: 6px red circles

---

## 3. Functionality Specification

### Core Features

**Player Controls:**

- WASD or Arrow Keys: Movement (8-directional)
- Mouse: Aim direction
- Left Click / Space: Fire weapon
- 1-3 Keys: Weapon switching (when upgraded)

**Movement:**

- Player speed: 5 pixels/frame
- Smooth acceleration/deceleration
- Bounded to canvas edges

**Shooting:**

- Base fire rate: 150ms between shots
- Bullets travel at 12 pixels/frame
- Bullets despawn off-screen

**Enemy Waves:**

- Wave 1-3: Basic enemies only (5, 8, 12)
- Wave 4-6: Add fast enemies (mix)
- Wave 7+: Add tanks, increase spawn rate
- 3-second delay between waves
- Enemies spawn from screen edges

**Scoring:**

- Basic enemy: 100 points
- Fast enemy: 200 points
- Tank enemy: 500 points
- Combo multiplier: Increases with kills in quick succession (max 8x)
- Combo decays after 2 seconds without kill

**Power-up System:**

- 10% chance to drop on enemy death
- Types rotate: Health, Rapid Fire, Spread, Shield
- Duration: 10 seconds for timed power-ups

**Health System:**

- Player starts with 100 HP
- Basic enemy collision: -20 HP
- Enemy bullet: -15 HP
- Tank bullet: -25 HP
- No health regeneration (except power-up)

**Weapons (unlock through gameplay):**

1. **Pistol:** Single shot, base fire rate
2. **Machine Gun:** Fast fire rate (50ms), 30% damage
3. **Shotgun:** 5 bullets in spread, 200ms fire rate

**Game States:**

- START: Title screen, waiting for input
- PLAYING: Active gameplay
- GAME_OVER: Final score display

### User Interactions

- Immediate response to input
- Visual feedback on hits (flash, screen shake)
- Audio-visual feedback on kills (explosion particles)
- Clear UI feedback for power-ups and combos

### Edge Cases

- Player cannot leave screen bounds
- Bullets cleaned up when off-screen
- Enemies removed when killed
- Game pauses if window loses focus

---

## 4. Acceptance Criteria

1. ✓ Game loads without errors
2. ✓ Player can move in 8 directions with WASD/Arrows
3. ✓ Player aims toward mouse cursor
4. ✓ Shooting works with click/space
5. ✓ Enemies spawn in waves from screen edges
6. ✓ Enemies move toward player
7. ✓ Collision detection works (bullets-enemies, enemies-player)
8. ✓ Score increases on kills
9. ✓ Combo system works with visual feedback
10. ✓ Power-ups drop and can be collected
11. ✓ Health bar updates on damage
12. ✓ Game over triggers when health reaches 0
13. ✓ Restart works from game over screen
14. ✓ Visual effects: particles, screen shake, glow effects
15. ✓ HUD displays all required information
16. ✓ Smooth 60fps gameplay
