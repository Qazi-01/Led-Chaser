# LED Chaser – 12‑LED Wave Board

A classic beginner soldering project using an NE555 timer and a CD4017 decade counter. Instead of a simple chase, the LEDs create a **wave** effect — they start at the outer edges, march to the centre, meet, and pause before repeating.

![Board Render](cad/board_render.png)

## ✨ Features
- 12‑LED "wave" pattern (pairs light up in sequence)
- Adjustable speed via onboard potentiometer (RV1, 50kΩ)
- Runs on 5V DC (USB‑compatible)
- All through‑hole components — easy to solder
- No microcontroller, no code — pure electronics
- Test points (J1, J2) for multimeter or oscilloscope

## 🔧 How It Works
**Heartbeat — NE555 Astable Oscillator**  
The NE555 outputs a square wave whose frequency is controlled by RV1 and C3 (1µF). Turning the knob speeds up or slows down the whole sequence.

**Traffic Controller — CD4017 Decade Counter**  
On each clock pulse from the 555, the 4017 advances its output. Pins Q0–Q5 are connected to LED pairs in a clever pattern:

| Output | LEDs lit   | Visual position |
|--------|------------|-----------------|
| Q0     | D1 + D12   | outer edges     |
| Q1     | D2 + D11   | one step in     |
| Q2     | D3 + D10   | ...             |
| Q3     | D4 + D9    | ...             |
| Q4     | D5 + D8    | ...             |
| Q5     | D6 + D7    | centre meet     |
| Q6‑Q9  | *none*     | all dark (pause) |

**Current Limiting**  
A single 470Ω resistor (R4) protects all LEDs. Only two LEDs are ever on at the same time, so it's perfectly safe.

**Power**  
The board runs on 5V DC via header J1. Connectors J1 and J2 double as test points for debugging.

## 📐 Schematic
![Hand‑drawn schematic](schematic.png)  
*(Matches the platform‑provided kit schematic.)*

## 📝 Full Description
See [`docs/project_description.md`](docs/project_description.md).

## 📜 License
Open‑source under the [MIT License](LICENSE).

---
*Built for a YSWS grant challenge — digital prototype only.*
