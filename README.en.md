# stream-setups

[🇷🇺 Русский](./README.md) · **🇬🇧 English**

Documentation for my [Belabox](https://belabox.net/)-based streaming rigs — components, power wiring, consumption, hardware links.

## Setups

### [Setup 1](./Setup%201/) — Orange Pi 5 Plus + 2 modems + PiP

Basic mobile rig for streaming over two LTE modems with bonding on a belabox-receiver at home.

**Components:**
- 🍊 Orange Pi 5 Plus — H.265 encoding + SRT output
- 📡 2× modems (Fibocom T77W968 Cat 16 + L850-GL Cat 9) on M.2 → USB 3.0 adapters
- 🔌 USB hub RSHTECH 13 ports (12V/3A)
- 🎬 Sony HDR-AS300 — main camera (HDMI)
- 🔍 USB endoscope / mini camera — PiP in the corner
- 📺 UVC-HDMI converter (USB camera → HDMI)
- 🎥 PiP mixer FEELWORLD CAMKOO H2U (combines 2× HDMI)
- 🔋 Anker 737 (140W) + Wattico Airbank (27000 mAh)

**Stream bitrate:** 12000 kbps (~6 Mbps per modem)

**Form factor:** top-tube bike bag for all electronics + a separate handlebar bag for batteries. The 4 modem antennas stick out through openings in the bag.

| Disassembled | Assembled |
|---|---|
| ![Disassembled](./Setup%201/Несобранно.jpg) | ![Assembled](./Setup%201/Собранно.jpg) |

> The photos show only the electronics bag. The battery bag (Anker + Wattico) is not pictured.

**Signal flow:**
```
Sony AS300 ────────────────────────HDMI──────►┐
                                              ├──► FEELWORLD H2U ──HDMI──► Orange Pi 5 Plus
USB endoscope ──USB──► UVC-HDMI ──HDMI───────►┘    (PiP mixer)          (HDMI IN, encode, SRT)
                                                                              │
                                                                              ▼
                                                                     belabox-receiver (home)
```

**Power consumption (measured under active 12 Mbps stream):**

| Battery | Load | Runtime |
|---|---|---|
| 🔋 Wattico Airbank (~85 Wh) | 6.1–9.9 W (hub + 2 modems + UVC-HDMI + PiP) | **8.5–14 h** |
| 🔋 Anker 737 (~86 Wh, 140 W PD) | 4.7–5.3 W (Orange Pi + Sony AS300) | **16–18 h** |
| **Setup total** | **10.8–15.2 W** | **~8.5–14 h** (Wattico is the bottleneck) |

📄 [Full per-port breakdown, TX-burst dynamics, power diagram and notes →](./Setup%201/Потребление.en.md)

---

## Repository structure

```
stream-setups/
├── README.md                     ← primary (Russian)
├── README.en.md                  ← English mirror
├── Setup 1/
│   ├── Потребление.md            ← consumption & runtime (Russian)
│   ├── Потребление.en.md         ← English mirror
│   ├── <Device>.md/.txt          ← component notes + links
│   └── <Device>.png              ← photo / screenshot
├── Setup 2/                      ← (planned)
└── Setup 3/                      ← (planned)
```

Each `Setup N/` folder is self-contained and includes:
- a description of every component in the rig,
- a power consumption breakdown and wiring diagram,
- links to the specific products.

> Component notes (`.txt` files inside `Setup N/`) are kept in Russian only — they're reference snippets from product pages. The main docs (`README` and `Потребление`) have full English mirrors.
