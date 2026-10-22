# Unity 2D Breakout/Arkanoid 

## Executive Summary

This document outlines the complete project plan for my Unity 2D Breakout/Arkanoid clone game designed for a GPE104. Demonstrate proficiency in planning, Unity 6.6, C# programming patterns, UI implementation, audio system, physics, and design patterns.

**Project Status:** Planning Complete
**Unity Version:** 6.6  
**Platform:** Desktop (MacOS)
**Class** GPE104


---

## Project Overview

### Game Concept
A Breakout/Arkanoid-style arcade game where the player controls a paddle to bounce a ball and destroy bricks, scoring points. Bricks have a small chance to drop upgrades that fall at a variable rate(fast/med/slow) that increase movement speed, and or provide extra points.


### Project Requirements/Guidelines

For this milestone, you will need to design and develop a game that meets the following requirements:

**Game Concept**

- Your game must be a NEW project. It is NOT one of the games that we created earlier in the term or a game you have worked on before.
- Your game can be 2D or 3D and must import and use art assets (sprites or meshes). 
- You MUST show planning of your game and how it meets these requirements BEFORE you begin.

**Basic Coding**

- You must show use of at least one if statement with an else clause.
- You must use at least one abstract class with methods and properties that are overridden in a child class.
- You must use at least one for loop. 
- You must use at least one foreach loop.
- You must use at least one List.
- You must use at least one Dictionary.

**User Interface**

- You must have a screen-space canvas that stretches with change in window size on either axis.
- You must have a world-space canvas.
- You must use at least one of each of the following UI types: a text box, an image, a slider, a button

**Audio**

- You must play sounds in world through an AudioSource
- You must use AudioSource.PlayOneShot
- You must use AudioSource.PlayClipAtPoint
- You must use Audio Mixers to control audio volume.

**Patterns, Models, and Paradigms**

- Your code must use a GameManager with the Singleton Pattern
- Your code must use the pawn/controller pattern for moving a pawn.
- Your code must use the Single Purpose Principle. You must explain how you used it in your code.
- Your code must use principles of OOP.
- You must define and explain how your code uses these principles. Abstraction, Encapsulation, Inheritance, Polymorphism
- Nothing in your code should be hard coded. It should all be made available for designers to change.
- You must be able to explain what that means, why it is important, and be able to show what causes your code to meet this requirement.
- Your code must be well commented, readable, and follow all UAT Coding standards
- At least one piece of data changes every frame draw (such as movement, damage-over-time, etc.) and must be framerate independent.
- You must explain what that means and show how the code in your project meets this requirement.

**Input**

- Your Player Controller must read inputs from buttons (or keys).
- Your Player Controller must also read inputs from joystick axes.
- Your player controller must use both GetButton (or GetKey) AND GetButtonDown (or GetKeyDown). 

**Movement**

- You must move at least one object by setting its position. 

**Collision**

- You must use at least one collider.
- You must be able to explain why you used that collider as a trigger or not.

**Physics**

- One or more objects in your game must use Unity physics.
- One or more objects must add force to move.
- One or more objects must use gravity.
- One or more objects must use drag to slow movement.

**Complete Game Project**

- Your game must start with a "Press Any Key to Begin" button that leads to the main menu.

**You our game must contain:**
- A Main Menu
- Credits
- Settings (with working audio sliders for Sound Effects and Music)
- One-or-more game over screens and conditions.
- Your player must be able to return to the main menu after the game over screens. 
- Your player must be able to quit to desktop from the main menu.
- Your game must have some sort of data that persists between game sessions.

**Professionalism**

- Your code must be readable, well commented, and follow UAT coding standards. Evidence of planning must be presented.

**Ship It**

- Your repo must be publicly available on your GitHub
- You must make a build and make a .ZIP file of the build (executable and data folder) available to the public. 



### Project Requirements 
- Game state management (GameManager)
- Brick base class with concrete types (brick.cs)
- Brick arrangement, collection iteration (GameManager, BrickManager)
- Collection processing, UI updates (Score Manager, UI Manager)
- Score tracking, asset management (Score Manager)
- Input tracking, to control paddle movement (PaddleController)
- Physics, ball will use unity's physics system (AddForce, Queartonion etc)

### UI System Requirements
- Score, lives, timer display (UIMainMenu, UIGame, via Screen-space canvas)
- Sliders, Volume control | UISettingsManager |
- Buttons, Start button, quit button, settings button, restart button (MainMenu/EndGame/WinGame)

### Audio System Requirements
- AudioSource.PlayOneShot for Sound effects (AudioManager)
- AudioSource.PlayClipAtPoint for one shot world audio(AudioManager)
- AudioSource.Play(), or select on wake play for music and looping, non ending music or sfx (AudioManager)
- Audio Mixer for Volume control | (AudioMixer w/Main, Music and SFX named groups)

### Design Pattern Requirements
- GameManager Singleton to central game state (GameManager.cs)
- Pawn/Controller Pattern for Paddle movement (PaddleController.cs)
- Single Purpose Principle for each class has one responsibility (All scripts)
- OOP Principles for Abstraction, Encapsulation, Inheritance, Polymorphism (All scripts)

### Input System Requirements
- GetButton/GetKey for Continuous input monitoring (InputManager.cs)
- GetButtonDown/GetKeyDown for input (InputManager.cs)
- Keyboard input for Arrow keys, WASD (InputManager.cs)
- Joystick axes for alternative input (InputManager.cs)

### Physics System Requirements
- Colliders(2D) for physics collision detection (Ball, Paddle GameObjects)
- Ball physics via RigidtBody2d (Ball.cs)
- Ball Movement damping (Ball.cs)
- Ball launch (BallLaunch.cs)
- Ball bounce (BallBounce.cs)

### Game Structure Requirements
- Main Menu w/"Press Any Key to Begin" (MainMenu Scene)
- Credits for Game credits (Credits Scene)
- Settings for Audio sliders (Settings Scene)
- Game Over Screen (GameOver Scene)
- Victory Sceen (Victory Scene)
- Persistent Data for High score, settings (PersistenceManager(playerPrefs))

---

## Detailed Plan

#### 1. Project Setup & Core Game Loop
**Priority:** Highest - Foundation for all other work

**Project Setup Plan:**
- **Unity Project Setup**
  - Create Unity 6.6 2D project
  - Create and Import art assets
  - Import Sound FX and Music
  - Create project folder structure (Scripts, Art folder etc)
  - Git Add ., Git Commit, Git Push (git)
  
-**Basic Game Loop Structure**
  - Implement GameManager Singleton (DontDestroyOnLoad)
  - Create state management (Menu, Playing, GameOver)
  - Implement scene transitions (LoadScene via GameManager)
  - Add persistent data loading/saving via 

#### 2. Player Controller & Input System
**Priority:** High - Core gameplay mechanics

**Player Controller & Input System Plan:**
- **Paddle Controller**
  - Configure Input Manager for keyboard and joystick
  - Create PaddleController with pawn/controller pattern
  - Implement keyboard input (Left right input via Keyboard.current, wasPressedThisFrame, isPressed etc)
  - Implement joystick input (ReadValue<Vector2>(), Gamepad.current / Joystick.current)
  - Add physics to paddle (Rigidbody2D)
  - Implement screen boundary clamping (BoundryManager.cs)
  - Implement power-ups for the paddle that fall from bricks (PowerUpManager)


#### 3. Game Objects & Physics
**Priority:** High - Core gameplay mechanics

**Ball and Bricks**
- **Ball Physics & Movement**
  - Create Ball class (Rigidbody2D)
  - Configure gravity, drag, and force accordingly
  - Implement collision detection
  - Add ball reset and launch functionality
  
- **Bricks & Collision System**
  - Create abstract Brick base class
  - Create concrete brick types with overridden methods
  - Implement brick destruction
  - Create brick arrangement using for loop

#### 4. UI System
**Priority:** Medium - User experience

**ScreenSpace Canvas for main GUI:**
- **Screen-Space Canvas UI**
  - Create screen-space canvas that stretches with window
  - Add text boxes, images, sliders, buttons, etc
  - Implement UI scaling
  
- **World-Space Canvas UI**
  - Create world-space canvas for object indicators etc.
  - Position UI elements in world space

- Finally, hook up UI's to GameManager.

#### 5.Audio System
**Priority:** Medium - User experience

**Audio:**
- **Audio Source & Mixer Setup**
  - Create Audio Mixer with Sound Effects and Music groups
  - Configure Audio Source components accordingly.
  - Set up/hook up volume control sliders
  
- **Audio Playback Implementation**
  - Implement PlayOneShot for SFX
  - Implement PlayClipAtPoint for world audio
  - Play audio on game events
  - Create audio manager

#### 6. Game State & Persistence
**Priority:** Medium - Game completion

**GameState:**
- **Game State Management/Scenes**
  - Implement main menu with "Press Any Key to Begin"
  - Create credits screen
  - Create settings screen with audio sliders
  - Implement game over screens
  - Implement player return to main menu
  
- **Data Persistence**
  - Implement high score persistence
  - Save and load audio settings
  - Create data persistence manager via playerPrefs


#### 7. Documentation & Polish
**Priority:** Low - Final touches

**Comments:**
- **Code Documentation**
  - Add comments to all scripts
  - Document design patterns and OOP principles if needed.
  - Create README
  
- **eFinal Polish & Testing**
  - Test all game features
  - Verify all technical requirements
  - Add FX, 
  - Create final build

### Version Control
**Priority:** high - version control

- Use git for version control
- Commit after every completed step
- Create branches accordingly

## Deliverables

### Code
- GameManager.cs (Singleton pattern)
- PaddleController.cs (pawn/controller pattern)
- Ball.cs (physics implementation)
- Brick.cs (abstract class with overrides)
- InputManager.cs (input handling)
- AudioManager.cs (audio playback)
- PersistenceManager.cs (data persistence)
- UI scripts (all UI components)

### Assets
- Paddle sprite
- Ball sprite
- Brick sprites
- UI elements
- Audio clips

### Documentation
- README.md
- Code comments across all scripts
- Technical architecture documentation to explain program flow.
- Design patterns documentation

### Build
- Mac build
- Upload to github as a release.