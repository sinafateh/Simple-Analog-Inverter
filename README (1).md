# ⚡ Simple Inverter Without Microcontroller

## 🎯 Project Objective
This project demonstrates a basic **DC to AC inverter** built entirely with analog and digital logic components, without using any microcontroller. It uses a 555 timer and a CD4017 decade counter to generate alternating control signals for driving a transformer through MOSFETs.

---

## 🧠 How It Works

1. **Pulse Generation with 555 Timer**
   - The 555 timer is configured in **astable mode** to generate a square wave of approximately **200 Hz**.

2. **Frequency Division with CD4017**
   - The square wave signal is fed into a **CD4017 decade counter**.
   - The counter sequentially activates output pins (Q0–Q9) with each pulse.
   - We use **Q0 and Q2** outputs to generate alternating signals to control the switching of MOSFETs.

3. **MOSFET Switching**
   - Two **MOSFETs** (e.g., **IRFZ44N**) receive the signals from the CD4017 and switch the DC power to the transformer's primary side alternately.

4. **Voltage Step-Up via Transformer**
   - The transformer (e.g., 12V to 220V) steps up the switched DC to **220V AC** (square wave).
   - The inverter was tested successfully with a small AC load (e.g., a lamp).

---

## 📦 Components List
| Component | Quantity | Description |
|----------|----------|-------------|
| IC 555 | 1 | Pulse generator |
| CD4017 | 1 | Decade counter |
| IRFZ44N MOSFET | 2 | Power switching |
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
![image](https://github.com/user-attachments/assets/c831efc1-5e10-442e-9195-119312cd4167)
![image](https://github.com/user-attachments/assets/7ef1d7bc-c44a-4ecf-954c-eed85a5aba4a)
![image](https://github.com/user-attachments/assets/64cfa857-88d5-4648-b53c-0449e4618e28)
![image](https://github.com/user-attachments/assets/a73da09b-e7af-4dc8-9a05-13f32f6a3b7b)

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
