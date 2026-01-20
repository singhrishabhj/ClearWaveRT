# ClearWaveRT

ClearWaveRT is a real-time audio noise reduction engine written in Java.
It captures system audio, processes it live using low-latency DSP techniques,
and outputs cleaner audio in real time.

## What
A Java-based real-time audio processing pipeline focused on noise reduction.

## Why
To understand and demonstrate:
- Real-time system constraints
- Audio DSP fundamentals
- Test engineering for non-functional systems
- Clean, extensible architecture

## How
ClearWaveRT captures system audio via a virtual loopback device,
processes audio frames using DSP filters,
and plays back cleaned audio with minimal latency.

## Project Status
1. Phase 1 – System audio capture & playback (in progress)

## Tech Stack
- Java 17+
- Java Sound API
- Maven (planned)

## Roadmap
See docs/ARCHITECTURE.md for details.

