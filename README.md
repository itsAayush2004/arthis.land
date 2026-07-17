<div align="center">

<img src="https://arthis.land/assets/LOGO-3Edited.png" alt="ARTHIS.land" width="140" />

# 🌆 ARTHIS.land — The Wall

### A handcrafted, vertical city you explore in the browser. Real-time multiplayer, pulled from the Arthis archive.

[![Enter The Wall](https://img.shields.io/badge/▶%20Enter-arthis.land-7C3AED?style=for-the-badge)](https://arthis.land)
&nbsp;
![Engine](https://img.shields.io/badge/engine-Unity-000000?style=for-the-badge&logo=unity&logoColor=white)
![Runs in](https://img.shields.io/badge/runs%20in-Browser%20(WebGL)-990000?style=for-the-badge&logo=webgl&logoColor=white)

</div>

> _This repository is a project showcase. The source code for the ARTHIS.land client is private — this page explains what it is and how it works. Its multiplayer backend is open: **[arthisland-relay](https://github.com/akversebusiness-beep/arthisland-relay)**._

---

## What is ARTHIS.land?

**ARTHIS.land — "The Wall"** is a handcrafted **vertical city**: an interactive experience you climb and explore, built from pieces of the Arthis archive. It's designed as a place to wander rather than a game to win — atmospheric, dense, and a little strange.

It runs in your browser via **Unity + WebGL**, and it's **multiplayer** — you can share a space with others in real time.

## Highlights

- 🏙️ **A vertical city** — a tall, handcrafted world you move up through
- 🎮 **Built in Unity** — shipped to the browser with WebGL (and standalone builds)
- 👥 **Real-time multiplayer** — 2–4 players share a room and see each other move
- 🔑 **Room codes** — host a space and invite others with a simple 4-digit code
- 🗄️ **From the archive** — scenes and assets curated from the Arthis collection

## How it works

ARTHIS.land is a Unity client that connects to a lightweight relay for multiplayer. The client owns the world and the players; the relay simply moves messages between everyone in a room.

```text
   ┌──────────────┐        ┌──────────────┐        ┌──────────────┐
   │  Player 1    │        │  Player 2    │        │  Player 3/4  │
   │ Unity (WebGL)│        │ Unity (build)│        │ Unity        │
   └──────┬───────┘        └──────┬───────┘        └──────┬───────┘
          │   HOST:1234 / JOIN:1234 · STATE · SCENE · NAME │
          └───────────────┬───────────────┬───────────────┘
                          ▼               ▼
                   ┌───────────────────────────┐
                   │      arthisland-relay      │
                   │  rooms · 2–4 players · TCP │
                   │  + WebSocket · stdlib only │
                   └───────────────────────────┘
```

1. **Join a space.** One player hosts a room (`HOST:<code>`); others join it (`JOIN:<code>`). Each player is assigned a stable ID.
2. **Sync in real time.** Every client streams its state, scene, and name to the relay, which fans those updates out to everyone else in the room (`P:<id>,STATE:…`).
3. **Leave cleanly.** When someone disconnects, the others are notified (`LEFT:<id>`) and the world updates. When the last player leaves, the room closes.

The relay is transport-agnostic — **WebGL** builds connect over **WebSocket**, standalone builds over **plain TCP**, both on the same port. See **[arthisland-relay](https://github.com/akversebusiness-beep/arthisland-relay)** for the full protocol.

## Tech

![Unity](https://img.shields.io/badge/Unity-000000?style=flat-square&logo=unity&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=flat-square&logo=c-sharp&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-990000?style=flat-square&logo=webgl&logoColor=white)
![Python relay](https://img.shields.io/badge/relay-Python%20stdlib-3776AB?style=flat-square&logo=python&logoColor=white)

## The ARTHIS universe

| Project | What it is |
| ------- | ---------- |
| 🌆 **[ARTHIS.land](https://arthis.land)** | This — "The Wall," the vertical city |
| 🎮 **[ARTHIS.space](https://arthis.space)** | An endless feed of single- & multiplayer mini-games |
| 🛰️ **[arthisland-relay](https://github.com/akversebusiness-beep/arthisland-relay)** | The real-time multiplayer relay backend |

---

<div align="center">
Made by <a href="https://github.com/akversebusiness-beep">@akversebusiness-beep</a> · <a href="https://arthis.land">arthis.land</a>
</div>
