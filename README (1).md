# ⚡ Simple Inverter Without Microcontroller

## 🎯 Project Objective
This project demonstrates a basic **DC to AC inverter** built entirely with analog and digital logic components, without using any microcontroller. It uses a 555 timer and a CD4017 decade counter to generate alternating control signals for driving a transformer through MOSFETs.

---

## 🧠 How It Works

1. **Pulse Generation with 555 Timer**
   - The 555 timer is configured in **astable mode** to generate a square wave of approximately **299 Hz**.

2. **Frequency Division with CD4017**
   - The square wave signal is fed into a **CD4017 decade counter**.
   - The counter sequentially activates output pins (Q0–Q9) with each pulse.
   - We use **Q2 and Q4** outputs to generate alternating signals to control the switching of MOSFETs.

3. **MOSFET Switching**
   - Two **MOSFETs** (e.g., **IRF540N**) receive the signals from the CD4017 and switch the DC power to the transformer's primary side alternately.

4. **Voltage Step-Up via Transformer**
   - The transformer (e.g., 12V to 220V) steps up the switched DC to **220V AC** (square wave).
   - The inverter was tested successfully with a small AC load (e.g., a lamp).

---

## 📦 Components List
| Component | Quantity | Description |
|----------|----------|-------------|
| IC 555 | 1 | Pulse generator |
| CD4017 | 1 | Decade counter |
| IRF540N MOSFET | 2 | Power switching |
| Transformer 12V to 220V | 1 | Voltage step-up |
| Resistors & Capacitors | Several | For timer tuning |
| DC Power Source | 1 | Input supply (e.g., 12V battery) |

---

## ⚠️ Safety Notice
- The output of this inverter is **220V AC**, which is dangerous.
- Make sure to follow **electrical safety guidelines**, use insulation, and test the circuit carefully.

---

## 💡 Possible Improvements
- Add an **LC or RC filter** to smooth the square wave output into a more sine-like waveform.
- Include **over-voltage and over-current protection**.
- Add status indicator LEDs for better debugging.

---

## 📸 Project Images (optional)
> Include circuit diagrams, breadboard layout, or real-life build photos here.

---

## 🧪 Test Results
- Output: **220V AC (square wave)**
- Load test passed using a small lamp
- Stable operation during testing
---

## 🔁 Counter Reset Logic
To ensure the CD4017 doesn't continue counting through all 10 outputs, the **Q4 output** is connected to the **RESET pin** of the counter.
This causes the counter to restart its count cycle immediately after Q4 goes high, resulting in a loop between Q0 → Q1 → Q2 → Q3 → Q4 → RESET.

This reduces unnecessary switching and ensures more efficient signal timing for driving the MOSFETs.
