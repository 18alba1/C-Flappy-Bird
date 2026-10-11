
# 🐦 Flappy Bird on ChipKIT Uno32

A playable Flappy Bird-inspired game implemented in C for the **ChipKIT Uno32** microcontroller with the **Basic I/O Shield**.

The game recreates the core Flappy Bird mechanics on embedded hardware: control the player, navigate between obstacles, avoid collisions, and keep track of your score using the board's LEDs.

<img width="600" height="491" alt="image" src="https://github.com/user-attachments/assets/7fb4394c-bb26-4130-87e6-95c3b914f234" />


## 🎮 Game Overview

The game runs directly on the microcontroller and uses the Basic I/O Shield display and physical buttons for interaction.

### Features

- **Player movement:** Control the player character using the board's physical buttons.
- **Obstacle generation:** Navigate through pipes with gaps at different heights.
- **Collision detection:** Detect collisions between the player and obstacles.
- **Score tracking:** Earn points by passing obstacles, with the score displayed using the onboard LEDs.
- **Game states:** Includes a startup screen, gameplay, and a game-over screen.
- **Restart functionality:** Restart the game after a collision without resetting the board manually.
- **Embedded display rendering:** Draw the player, obstacles, and game elements on the Basic I/O Shield display.

## 🛠️ Hardware & Technologies

| Component | Purpose |
|---|---|
| ChipKIT Uno32 | Microcontroller platform |
| Basic I/O Shield | Display, buttons, and LEDs |
| C | Game logic and hardware interaction |
| MIPS32 assembly | Low-level routines and interrupt support |
| PIC32MX320F128H | Target microcontroller |
| Hardware timers and interrupts | Timing and interrupt-driven event handling |
| SPI | Communication with the display |

## 🕹️ How to Play

1. Power on the ChipKIT Uno32 with the Basic I/O Shield attached.
2. Press **Button 4** to start the game.
3. Press **Button 2** to make the player fly upward.
4. Navigate through the gaps between the pipes without colliding.
5. Watch the LEDs to track your score.
6. After a collision, press **Button 4** to restart.

## 🧠 Implementation Highlights

### Game Logic

The game is organized around a continuously running game loop that updates the player position, moves obstacles across the display, renders the game state, and checks for collisions.

### Collision Detection

The game checks the player's position against the obstacle positions and their gaps. A collision ends the current run and transitions the game into its game-over state.

### Hardware-Level Programming

The project interacts directly with the PIC32 microcontroller's registers to configure input/output pins, initialize the display interface, control LEDs, and configure timer interrupts.

### Timing and Interrupts

Hardware timer configuration and interrupt handling support the embedded execution environment. The game loop also uses delays to control the pace of gameplay.

### Display and Score

The game uses the Basic I/O Shield's display to render the player and obstacles. The LEDs provide visual score feedback as the player passes obstacles.

## 🏗️ Project Structure

The source code is located in `projektis1200/`.

| File | Responsibility |
|---|---|
| `mipslabmain.c` | System initialization and main execution loop |
| `mipslabwork.c` | Main game loop, player movement, obstacles, collision detection, and game states |
| `mipslabfunc.c` | Display and game-related helper functions |
| `mipslabdata.c` | Display data and graphical assets |
| `mipslab.h` | Shared declarations and function interfaces |
| `time4io.c` | Timer-related support |
| `labwork.S` | Assembly routines |
| `vectors.S` | Interrupt vector support |
| `pic32mx.h` | PIC32 register definitions |
| `Makefile` | Build and installation targets |

## 🚀 Building and Running

This project targets the ChipKIT Uno32 and requires a compatible PIC32 MIPS cross-compilation toolchain.

### Prerequisites

- ChipKIT Uno32 board
- Basic I/O Shield
- Compatible PIC32 MIPS compiler and toolchain
- Appropriate programmer and device connection

### Build

Open a terminal and navigate to the project directory:

```bash
cd projektis1200
make
```

The Makefile is configured to build the firmware for the PIC32MX320F128H. The build produces firmware artifacts, including `outfile.hex`.

The provided Makefile also includes an installation target:

```bash
make install
```

**Note:** The compiler, programmer utilities, and course-specific cross-compilation environment must be installed and configured before building or flashing the firmware. Review the Makefile's environment checks and adjust the serial device setting if necessary.

## 🎯 What I Learned

This project provided practical experience with:

- Embedded C programming on a microcontroller
- Direct register access and hardware configuration
- Bitwise operations and memory-mapped I/O
- Timer configuration and interrupt handling
- Display rendering and graphical state updates
- Game loops, state management, and collision detection
- Integrating software logic with physical hardware
