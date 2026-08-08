<div align="center">

# ♟ Simultaneous Blind Chess

**A chess variant where both players move at the same instant — locally or online across two devices.**

[![Play Local](https://img.shields.io/badge/📱%20Play%20Local-Pass%20%26%20Play-00d2d3?style=for-the-badge)](https://malikaoo.github.io/simultaneous-blind-chess/)
[![Play Online](https://img.shields.io/badge/🌐%20Play%20Online-P2P%20WebRTC-ff9f43?style=for-the-badge)](https://malikaoo.github.io/simultaneous-blind-chess/online.html)
[![License: Non-Commercial](https://img.shields.io/badge/License-Non--Commercial-54a0ff?style=for-the-badge)](./LICENSE)
[![No Server](https://img.shields.io/badge/Serverless-GitHub%20Pages-2ed573?style=for-the-badge)](#run-it)

![Simultaneous Blind Chess gameplay screenshot](screenshot.png)

</div>

---

## Why this is different from standard chess

Standard chess alternates turns. This doesn't.

Both players secretly pick their move—either on the same device or across two separate devices online—lock it in, and execute both moves at exactly the same time. That single change creates an entirely new game of psychology, prediction, and risk:

- You must **predict intent**, not just react to position
- Pieces can **collide** mid-board and annihilate each other
- Both kings can be **in check simultaneously**
- A king can actually be **physically captured**
- **100% Serverless Online Play:** Cryptographic commit-reveal guarantees neither player can peek at the opponent's choice over the network before locking in their own.

---

## 🎮 Play Modes

### 📱 Mode 1: Pass & Play (Same Device)
Two players alternate using the same screen. Player 1 locks White's move, hands the device over, Player 2 locks Black's move, and both execute simultaneously.

### 🌐 Mode 2: Online P2P (Two Devices)
Play remotely across two different devices using **PeerJS (WebRTC)** directly in your browser—no backend server or account required.
* **Room Code Matchmaking:** One player clicks **Host New Game** to generate a code, and the second player pastes that code to **Join**.
* **Cryptographic Commit-Reveal Scheme:** When you lock your move, your browser sends a SHA-256 salted hash (Commitment) to your opponent. Only after *both* players submit their commitments do the actual moves exchange (Reveal) and verify mathematically—ensuring total secrecy.

---

## Original Rules

### Base: Standard chess
All standard piece movements, castling, promotion, check, checkmate, and stalemate apply — plus the rules below.

---

### 🟣 Purple Lock — No Repeat Moves
The piece you just moved is highlighted purple and **locked for one full turn**. You must move a different piece. This prevents any single piece from dominating every round and forces strategic variety.

---

### 💥 Collision — Same Square, Same Moment
If both players move to the same square simultaneously:

| Situation | Result |
|-----------|--------|
| Different piece values | Higher-value piece wins and stays |
| Same piece value | **Both pieces are destroyed** — square left empty |

| Piece | Value |
|-------|-------|
| ♙ Pawn | 1 |
| ♘ Knight | 3 |
| ♗ Bishop | 3 |
| ♖ Rook | 5 |
| ♕ Queen | 9 |
| ♔ King | 100 |

---

### ⚠️ Double Check — Both Kings Can Be Threatened at Once
Because moves are simultaneous, both kings can be in check at the same time. Each player must independently resolve their own king's danger. Moves that would leave your king exposed are **blocked** — they won't appear as valid options.

---

### 👑 King Capture — The Simultaneous Threat
Unlike standard chess, a king can be **physically captured** here because both pieces land at the same moment.

| Situation | Result |
|-----------|--------|
| Your king is captured | You lose |
| Both kings captured in same move | **Draw** |
| No legal moves + in check | Checkmate — you lose |
| No legal moves + not in check | Stalemate — Draw |

---

## How to Play

### 📱 Same Device (Pass & Play)
1. **White** selects a piece and destination, then clicks **Lock White Move**.
2. Hand the device to Player 2 — they cannot see White's choice.
3. **Black** selects their move and clicks **Lock Black Move**.
4. Press **EXECUTE TURN** — both moves apply simultaneously.

### 🌐 Two Devices (Online P2P)
1. Open the **[Online Version](https://malikaoo.github.io/simultaneous-blind-chess/online.html)** on two separate devices.
2. Player 1 clicks **Host New Game** and sends the generated Room Code to Player 2.
3. Player 2 enters the code and clicks **Join Game**.
4. Both players select their moves privately on their own screens and click **Lock & Submit Move**.
5. The game automatically verifies hashes, reveals moves, and executes the turn simultaneously.

---

## Run It

**No installation. No dedicated server. No dependencies.**

* 📱 **[Play Local (Pass & Play)](https://malikaoo.github.io/simultaneous-blind-chess/)**
* 🌐 **[Play Online (Peer-to-Peer)](https://malikaoo.github.io/simultaneous-blind-chess/online.html)**

**Run locally:**
1. Clone or download the repository.
2. Open `index.html` (Local) or `online.html` (Online P2P) in any modern web browser.
3. Play immediately!

---

## About This Project

**Invented and built in 2025 by [Tarek Nasser].**  
Email: `malikao@gmail.com` | `t_nasser@hotmail.com`

The combination of:
- Blind simultaneous move selection (shared device or salted WebRTC hash exchange)
- The Purple Lock (no-repeat-move) rule
- Collision resolution by piece value

...is an original invention by the author.

---

## License

✅ Free for personal, non-commercial use  
❌ Commercial use requires written permission from the author

See [LICENSE](./LICENSE) for full terms.

---

<div align="center">
<sub>Built with pure HTML, CSS, JavaScript, and PeerJS — zero server dependencies.</sub>
</div>
