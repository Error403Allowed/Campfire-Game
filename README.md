## 2-Day Hackathon Plan

### Day 1 — Core Gameplay Loop (Must Ship)

**Hour 1–2**
- Project setup
- Player movement
- Camera follow
- Basic room layout

**Hour 3–5**
- Depth tracking
- Simple zone switching (just change background colour + visibility)
- Oxygen system (working + visible on HUD)

**Hour 6–8**
- One enemy type (simple patrol → chase)
- Basic collision damage
- Hull system

End of Day 1 goal:
You can move, descend, lose oxygen, take damage, and die. If that works, you have a game.

---

### Day 2 — Make It Feel Good

**Hour 1–3**
- Light system (simple version first, no fancy shader if time dies)
- Sound effects + one ambient loop

**Hour 4–6**
- Collectibles (oxygen tank + repair kit)
- Basic score / artefact counter

**Hour 7–8**
- One “boss” or big enemy variant
- Game over screen polish
- Screen shake + minimal particles

If time remains:
- Zone-specific enemy tweak
- Minor visual polish

If time does NOT remain:
Cut features. Ship the core. Judges reward finished games, not dreams.

---

Scope discipline wins hackathons. Depth of polish > number of mechanics.
# Beneath the Surface — 2 Day Hackathon Plan (GameMaker)

---

# 1. Pitch and Intro

You pilot a deep-sea submarine descending into unknown waters.  
The deeper you go, the darker it gets. Oxygen drains. Pressure builds.  
Hostile creatures emerge from the abyss.  

Your mission: descend as far as possible, uncover ancient ruins, and survive long enough to tell the story.

It’s a minimalist survival descent game focused on tension, atmosphere, and tight core mechanics — built entirely in GameMaker.

---

# 2. Game Vision

Core Pillars:
- Simple but tense survival loop
- Strong atmosphere through lighting + sound
- Clear risk vs reward (go deeper = more danger)
- Clean, polished execution over feature bloat

This is not a story-heavy RPG.  
It is an arcade survival descent experience.

---

# 3. Core Gameplay Loop

1. Player descends.
2. Oxygen slowly drains.
3. Pressure damages hull at deeper levels.
4. Enemies appear and chase.
5. Player collects oxygen tanks and repair kits.
6. Player either dies… or reaches deeper zones.

Loop repeats with increasing difficulty.

---

# 4. Game Structure (GameMaker)

## Rooms

- rm_boot
- rm_menu
- rm_game
- rm_gameover

Flow:
rm_boot → rm_menu → rm_game → rm_gameover → rm_menu

---

## Core Objects

- obj_controller (global state)
- obj_player
- obj_enemy_parent
- obj_basic_enemy
- obj_boss_enemy
- obj_collectible_oxygen
- obj_collectible_repair
- obj_depth_manager
- obj_light_controller
- obj_hud_controller

---

# 5. Player Design

## Player Stats

- speed
- oxygen (max 100)
- hull (max 100)
- depth (calculated from y position)

---

## Player Controls (Top-Down)

Movement:
- W / Up → Move up
- S / Down → Move down
- A / Left → Move left
- D / Right → Move right

Optional:
- Left Click → Fire torpedo

Movement Logic:
- Normalize diagonal movement
- Apply constant speed
- Clamp to room bounds

---

## Player Systems

### Oxygen
- Drains every step
- Refilled by oxygen tanks
- If <= 0 → Game Over

### Pressure
- Based on depth
- Deeper = faster hull decay
- Repair kits restore hull

### Combat
- Enemies deal collision damage
- Optional torpedo projectile

---

# 6. Depth & Zone System

Depth = abs(y position)

Zones:
- Sunlit (0–200)
- Twilight (200–1000)
- Midnight (1000–4000)
- Ruins (4000+)

Each zone:
- Changes background colour
- Reduces light radius
- Increases enemy spawn rate
- Increases pressure damage

Depth Manager Responsibilities:
- Track depth
- Detect zone changes
- Trigger audio + lighting adjustments

---

# 7. Enemy Design

## Basic Enemy
- Patrol state
- Chase if player in range
- Damage on contact

## Boss Variant
- Larger sprite
- Higher health
- Aggressive chase pattern
- Appears after certain depth

State Machine:
- patrol
- chase
- attack

Keep AI simple but responsive.

---

# 8. Lighting & Atmosphere

Simple Implementation:
- Draw black overlay
- Cut circular gradient around player
- Reduce radius per zone

Goal:
Make depth FEEL dangerous.

No complex shader required if time is tight.

---

# 9. HUD Design

Draw GUI Event (obj_hud_controller):

Display:
- Depth counter
- Oxygen bar
- Hull bar
- Zone name (briefly when entering)

Keep it minimal and readable.

---

# 10. Audio Plan

- Ambient loop per zone
- Engine hum when moving
- Damage sound
- Pickup sound
- Boss music (optional stretch)

Use GameMaker built-in audio system.

---

# 11. Setup & Planning Before Coding

Before touching code:

1. Create all objects in GameMaker.
2. Create all rooms.
3. Import placeholder sprites.
4. Set up room size and camera.
5. Create a simple task board:

Day 1:
- Player movement
- Depth tracking
- Oxygen + hull
- One enemy

Day 2:
- Lighting
- Collectibles
- Boss
- Polish

Do not build everything at once.
Build vertical slices.

---

# 12. 2-Day Execution Plan

## Day 1 Goal:
Playable survival prototype.

Must include:
- Movement
- Depth increases
- Oxygen drain
- Hull damage
- One enemy
- Death state

If this works, you have a complete core game.

---

## Day 2 Goal:
Make it feel intentional.

Add:
- Lighting
- Audio
- Collectibles
- Boss variant
- Screen shake
- UI polish

Cut anything that risks breaking stability.

---

# 13. Stretch Goals (Only If Ahead)

- Procedural enemy spawn scaling
- Subtle particle effects
- Animated background elements
- Mini sonar pulse effect

These are luxuries. Not requirements.

---

# 14. Judge-Focused Selling Points

When presenting:

- Emphasize atmosphere.
- Emphasize risk vs reward depth system.
- Emphasize that everything scales with depth.
- Show how lighting shrinks as tension rises.

Judges remember feeling, not code structure.

---

Scope discipline wins hackathons.  
A finished small game beats a half-built epic.
