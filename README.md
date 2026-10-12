# Starbie

Starbie is a tiny motion-controlled digital pet — a desktop Tamagotchi-style
companion that lives on a compact PCB. Instead of mashing buttons, you interact
with it mostly by physically moving the board: tilt it, nudge it, and check in
on it to keep it happy.

![Starbie render](Renders/Starbie%20Render.png)

This is my build of the Half-Life Week 1 beginner project. The hardware design
and renders in this repo are based on the original
[Starbie reference project by SharKingStudios](https://github.com/SharKingStudios/Starbie).

## What it is

Starbie sits on your desk, shows its personality on a small OLED display, and
reacts to how you handle it. The board carries a microcontroller, a display, a
motion sensor, and an environmental sensor in a single compact design. It is USB
powered and built around beginner-friendly through-hole soldering for the add-on
components, so it is a good first PCB-assembly project.

## How it works

- The **XIAO ESP32-C3** microcontroller runs the pet logic and talks to the
  peripherals over I²C and GPIO.
- An **OLED display** (0.96" 128×64, on the 4-pin I²C header) shows the pet's
  face, menus, and status.
- A **MPU6050 accelerometer/gyro module** (on the 8-pin header) senses tilt and
  motion, which is the main way you control the pet.
- A **DHT11** reads temperature and humidity so the pet can react to its
  environment.
- **Push buttons** (with a 10k pull-up resistor) provide a couple of direct
  controls, and the whole board is powered over the XIAO's USB-C connector.

Tilting the board drives a radial menu, shaking triggers a reaction, and hidden
stats tick along in the background to give the pet some personality.

## Board renders

| Front | Back |
| --- | --- |
| ![Front of the Starbie board](Renders/Starbie%20Front.png) | ![Back of the Starbie board](Renders/Starbie%20Back.png) |

## Repository contents

- `Starbie/` — KiCad source files for the PCB (`.kicad_pcb`, `.kicad_pro`,
  `.kicad_sch`).
- `Renders/` — 3D renders of the assembled board.
- `Week 1 Care Package/` — imported footprints, symbols, and 3D models for the
  add-on parts (XIAO ESP32-C3, OLED, MPU6050).
- `BOM.md` — bill of materials for the Week 1 build.

## Building it

1. Open `Starbie/Starbie.kicad_pro` in [KiCad](https://www.kicad.org/) to view or
   edit the schematic and PCB layout.
2. Have the PCB fabricated (for example at JLCPCB, see `BOM.md`).
3. Solder the through-hole add-on components (XIAO, display header, sensor
   header, buttons) onto the board.
4. Power it over USB-C and flash the firmware for the XIAO ESP32-C3.

## Credits

Starbie was created as the Half-Life Week 1 beginner tutorial project. Original
design and renders by [SharKingStudios](https://github.com/SharKingStudios/Starbie).
