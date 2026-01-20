# ClearWaveRT – Architecture

## 1. Problem Definition
ClearWaveRT aims to reduce background noise from system audio in real time.
The system must process audio while it is being played, without noticeable delay.

Unlike offline audio tools, ClearWaveRT cannot buffer the entire audio stream
and must operate on small chunks of audio continuously.

---

## 2. What Does “Real-Time” Mean Here?
Real-time in this project means:
- Audio is processed as it is received
- No full-file buffering
- Latency must remain low enough that users do not notice delay

Target latency:
- Ideal: < 20 ms
- Acceptable: < 30 ms

---

## 3. High-Level System Design

Audio Source (Browser / App)
        ↓
System Audio Output
        ↓
Virtual Audio Loopback Device
        ↓
ClearWaveRT Processing Engine
        ↓
Cleaned Audio Output
        ↓
Speakers / Headphones

ClearWaveRT does not modify the original media source.
It only processes system audio output.

---

## 4. Audio Processing Flow
1. Capture audio frames from system audio device
2. Convert raw bytes into numerical samples
3. Apply noise reduction filters
4. Convert samples back to audio bytes
5. Play cleaned audio immediately

Each step must complete within the time of one audio frame.

---

## 5. Buffering and Latency
Audio is processed in fixed-size buffers (frames).

Smaller buffers:
- Lower latency
- Higher CPU usage

Larger buffers:
- Higher latency
- More stable processing

ClearWaveRT prioritizes low latency.

---

## 6. Why This Is Hard to Test (SDET Perspective)
- Output is continuous, not deterministic
- Human hearing is subjective
- Timing issues are as important as correctness
- Performance is a functional requirement

Testing must include:
- Unit tests for filters
- Performance tests for latency
- Stress tests for CPU and memory pressure

---

## 7. Trade-offs and Limitations
- Some latency is unavoidable
- Java garbage collection can affect real-time performance
- Advanced AI noise reduction is out of scope initially

