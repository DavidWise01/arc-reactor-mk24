# ARC REACTOR MK-24
### Plasmatonic Toroid Core — Interactive Visualization

> 24 toroidal containment rings. Chain lightning. Full 3D rotation. No dependencies.

**Author:** David Lee Wise (ROOT0) / TriPod LLC  
**License:** CC-BY-ND-4.0

Open `arc-reactor-mk24.html` in any browser.

---

## Controls

| Input | Action |
|-------|--------|
| Click + drag | Rotate the toroid array in 3D |
| Double-click | Reset rotation to zero |
| SPACE | Toggle UI panel |
| R | Reset view |
| P | Toggle pulse mode |
| A | Toggle auto-rotate |
| O | Overload |

---

## UI Controls

| Control | Description |
|---------|-------------|
| **Color Theme** | Plasma (blue) · Amber (ROOT0) · Solar (red) · Void (green) |
| **Power Output** | Drive intensity of all rings and effects |
| **Rotation Speed** | How fast the rings orbit |
| **Flicker Intensity** | Plasma instability |
| **Containment Field** | Outer dipole field line strength |
| **Chain Lightning** | Frequency of arc events between rings |
| **Outer Housing** | Structural frame visible/hidden |
| **Auto Rotate** | Continuous slow yaw rotation |
| **Pulse Mode** | Power breathes automatically (~1.4 Hz) |
| **Audio System** | 60 Hz electromagnetic hum + arc crackle |
| **Toroid Array** | Toggle any of the 24 rings on/off individually |
| **Overload** | 3.5s overload event — power spikes to 125% |

---

## What Changed (MK-24 improvements)

### 3D Rendering
- **Full rotation matrix** — proper yaw (Y axis) + pitch (X axis) mouse rotation, replacing the approximate 2D trick
- **Perspective projection** — `w = FOV / (FOV + z)` applied per vertex. Rings genuinely near the viewer appear larger
- **Back-face culling** — segments behind the toroid midplane are skipped, not just faded
- **Two-axis toroid tilt** — each ring has independent X and Z random tilt (precomputed trig), giving varied orientations
- **Depth-sorted render order** — toroids sorted back-to-front each frame for correct visual layering

### Performance
- **Segment batching** — 52 segments per ring grouped into 5 depth bands and drawn as 5 paths instead of 52 individual draw calls. Shadow blur applied only on the front 2 bands
- **Proper dt timing** — lightning accumulator uses real frame delta time instead of hardcoded 16ms

### New Visual Features
- **4 color themes** — Plasma, Amber (ROOT0 palette), Solar red, Void green. Toroid colors re-tint when switching
- **Auto-rotate mode** — slow autonomous yaw rotation
- **Pulse mode** — power oscillates sinusoidally instead of being static
- **Inactive ring ghost** — deactivated toroids render at 6% opacity so you can see where they would be
- **Rotating inner core rings** — 3 animated rings inside the core show angular momentum
- **Dipole-style containment field** — curved field lines instead of simple radials
- **Housing bolts** — 8 structural bolts on the outer frame
- **Specular highlight** — off-center radial gradient on the core
- **Rotation readout** — HUD shows current pitch/yaw in degrees
- **Keyboard shortcuts** — SPACE, R, P, A, O

---

## Connection to the Toroid Framework

The 24 rings represent the 24 possible toroidal winding orientations. Each ring:
- Has a random two-axis tilt (its place in the 3D phase space)
- Rotates at a random speed and direction (clockwise or counter-clockwise)
- Can be selectively powered down — watch what happens to the field coherence at 8 active rings vs 24

The containment field is strongest when all 24 are active and the sum stays balanced. Which is the point.

---

*TriPod LLC // Anchor × Bubble × Gravity Well // World = Family*
