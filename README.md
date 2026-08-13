<div align="center">

# Karan Agrawal

**I build systems that have to survive contact with the real world — markets, hardware, and users who don't read docs.**

CSE (AI & ML) @ VIT Chennai, Class of 2029 · [GitHub](https://github.com/KaranAgrawal25) · [LinkedIn](https://linkedin.com/in/karanagrawal25) · agrawalkaran2508@gmail.com

</div>

<br/>

## What I'm actually doing right now

I'm not "exploring AI" — I'm building four production systems in parallel, and each one taught me something the tutorials don't cover:

- **A 6-agent video pipeline** that turns one line of text into a finished cinematic video (Gemma 2 9B, Groq, FFmpeg, MoviePy) — currently entered in the GDG Build with Gemma hackathon.
- **A real-time NSE accumulation scanner** running a two-stage architecture across 600–800 stocks simultaneously, built on Zerodha KiteConnect, now on its 7th major version with a full F&O engine.
- **A quantum key distribution simulator** (BB84 protocol) with a live Arduino hardware companion, built for my Engineering Physics coursework.
- **VIT Companion** — the only working reverse-engineered client for VIT's VTOP portal, handling a 3-step login handshake with CAPTCHA and CSRF by hand.

<br/>

## 🟢 Live from my repos

<!--LIVE-COMMIT-START-->
*This section auto-updates every 6 hours via GitHub Actions — pulled directly from my own commit history, not a third-party stats widget.*
<!--LIVE-COMMIT-END-->

<br/>

## Systems I've shipped — the real engineering, not the badge list

### 🎬 [VisionForge AI](https://github.com/KaranAgrawal25/VisionForge-AI)
A 6-agent pipeline (Prompt → Script → Voice → Image → Assembly → Review) that takes a one-line title and outputs a finished video, no manual steps.

The interesting part wasn't the happy path — it was making it *reliable*. edge-tts started throwing `403 WSServerHandshakeError` under concurrent builds because Microsoft rate-limits bursts; I fixed it with a process-wide inter-call spacing lock plus exponential backoff, and added a single build lock in the backend that returns HTTP 409 instead of corrupting state when two jobs collide. Migrated the LLM layer from OpenAI to Groq mid-build after hitting quota limits, and rebuilt the pipeline from semi-manual (user-uploaded images) to fully autonomous using Pollinations.ai — without a rewrite of the orchestration layer underneath.

`Next.js` `FastAPI` `Groq (Llama 3.3 70B)` `Gemma 2 9B` `MoviePy` `FFmpeg` `edge-tts`

### 📈 NSE Abnormal Participation Scanner
Detects institutional accumulation *before* the breakout, not after — that's the entire premise. Runs a two-stage architecture: a lightweight Stage 1 scan across 600–800 stocks to survive Zerodha's 3,000-token WebSocket limit, then a deep Stage 2 pass with full market depth on the candidates that survive filtering.

My core design call here, which I'd defend to anyone: **a missed genuine signal is worse than a manageable false positive.** Most scanners over-optimize for precision and quietly miss the setups that actually mattered. I built an adaptive weight-learning module (Pearson correlation-based) and post-alert outcome tracking specifically to keep tuning that trade-off with real data instead of gut feel. Now on v7 with a full 13-file F&O engine.

`Python` `KiteConnect (Zerodha)` `WebSockets` `Telegram Alerts`

### 🔐 [BB84 Quantum Key Distribution](https://github.com/KaranAgrawal25/BB84-QKD)
An interactive simulator for the BB84 protocol with a React/TypeScript/Vite frontend, backed by a real Arduino hardware companion — not just a textbook animation. Built for Engineering Physics at VIT, but engineered like a real project: proper SSH setup, documented README, structured for someone else to actually run it.

`React` `TypeScript` `Vite` `Arduino`

### 📱 VIT Companion
iOS-first Flutter/FastAPI app for VIT students — I'm the sole developer. The hard part was VTOP itself: a broken SSL chain, sticky-session cookies that silently invalidate on the wrong request order, and a 3-step login handshake involving CSRF tokens and CAPTCHA handling that no public documentation covers. Real parsers for Attendance, Timetable, and Marks, with a semester selector threading through every data provider.

`Flutter` `FastAPI` `JWT`

<br/>

## Stack

**Languages** — Python · TypeScript/JavaScript · Java · Kotlin · C/C++ · SQL
**Backend / Web** — FastAPI · Next.js · React · Flask · Node.js
**AI / LLM** — Groq · Gemma · LLM orchestration & multi-agent pipelines · prompt engineering · computer vision
**Hardware / IoT** — ESP32 · ESP8266 · ESP32-CAM · Arduino
**Infra** — Firebase · SQLite · MySQL · Git

<br/>

<div align="center">

*Reach out if you're working on multi-agent systems, market microstructure, or anything that touches hardware — that's where I do my best work.*

</div>
