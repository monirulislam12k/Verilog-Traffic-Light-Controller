# 🚦 Verilog Traffic Light Controller Chip Design

This project implements a Finite State Machine (FSM) based **Traffic Light Controller chip** designed in Verilog HDL. The logic design and sequence execution have been fully verified through a testbench simulated using **Questa-Altera Starter FPGA Edition**.

## 🛠️ Project Components
- `traffic_light.v` - Hardware description architecture (RTL Design).
- `traffic_light_tb.v` - Hardware verification and stimulus environment (Testbench).
- `waveform.png` - Visual proof of logical correctness.

---

## 📊 Timing Simulation Analysis
The output waveform below showcases the sequential behavior of the traffic lights operating smoothly under regular clock pulses:

![Simulation Waveform](waveform.png)

### State Definitions & Timing:
1. **0ps to 12000ps [Reset Phase]:** System resets; the `red` light triggers HIGH (`1`) while others remain LOW (`0`).
2. **12000ps to 25000ps [Green Phase]:** The system automatically transitions, turning the `green` light HIGH (`1`).
3. **25000ps to 35000ps [Yellow Phase]:** The `yellow` light turns HIGH (`1`) as a warning indicator before loop completion.
4. **35000ps+:** The cycle securely resets back to the `red` light state.

---

## 💻 Simulation Setup in Questa
To run this project locally, execute the following commands in your Questa/ModelSim transcript:
```bash
# Compile design and testbench
vlog traffic_light.v traffic_light_tb.v

# Start simulation with object visibility turned on
vsim -voptargs="+acc" work.traffic_light_tb

# Run all simulation time blocks
run -all
```
