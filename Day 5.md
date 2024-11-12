# VSDBabySoC 
### Overview
The **VSDBabySoC** project is a simple System-on-Chip (SoC) design that integrates basic components commonly found in many SoCs. These components include:
- **RISC-V processor (rvmyth)**: A 32-bit processor based on the RISC-V architecture.
- **PLL module (pll)**: A Phase-Locked Loop (PLL) used for generating stable clock signals to synchronize the operation of various parts of the SoC.
- **DAC module (dac)**: A Digital-to-Analog Converter that converts digital signals to analog ones, typically for interfacing with real-world analog systems.

This project demonstrates how these modules are integrated together to form a basic SoC, and focuses on simulating and verifying the design behavior both **before** and **after synthesis**. The goal is to check the functionality and performance of the system through these simulation stages.

### Project Structure
The project is organized in the following way:
- **`src/include/`**: This directory contains **header files** (with `.vh` extension) that define key **macros** and **parameters** for the SoC design. These may include configuration settings like clock frequencies, reset behaviors, or other design-specific constants.
  
- **`src/module/`**: This directory contains the **Verilog files** that define the logic and behavior of the individual modules in the SoC. These include the Verilog code for the RISC-V processor, PLL, DAC, and possibly other supporting modules.

- **`output/`**: The **output directory** is where all the generated files from the compilation and simulation processes will be stored. This includes compiled files, waveform files, and any other results generated from running simulations.

### Requirements
To work with this project, you will need the following software tools installed:

- **Icarus Verilog**: This is an open-source Verilog compiler and simulator that will be used to compile the Verilog code in the project. It converts the Verilog code into simulation-ready files.
  
- **GTKWave**: This is a waveform viewer used to visualize the results of the simulations. It allows you to view the signals and check if your SoC is behaving as expected during the simulations.

The project is intended to be run on a **Unix-like environment**, meaning it is designed to work on operating systems such as **Linux** or **macOS**. If you are using Windows, you may need to use a compatibility layer such as **WSL** (Windows Subsystem for Linux) to set up a similar environment.

### Simulations
The project involves two key stages of simulation:

1. **Pre-synthesis simulation**: This is done before any synthesis of the design (mapping it to actual hardware) and focuses on simulating the RTL (Register Transfer Level) design to ensure functional correctness.
  
2. **Post-synthesis simulation**: This is done after synthesis has been performed and takes into account how the design will behave once it is mapped to the actual hardware (e.g., gates, flip-flops, etc.). It is used to verify that the design will work as intended on actual hardware.

# 1. Setup and Prepare Project Directory
Clone or set up the directory structure as follows

# Simulation Steps
## Pre-synthesis Simulation

### Step 1: Clone **VSDBabySoC** (Top-Level SoC Module)
```bash
git clone https://github.com/manili/VSDBabySoC.git
```

### Step 2: Clone **rvmyth** (RISC-V Core)
```bash
git clone https://github.com/kunalg123/rvmyth.git
```

### Step 3: Clone **avsdpll** (PLL Module)
```bash
git clone https://github.com/lakshmi-sathi/avsdpll_1v8.git
```

### Step 4: Clone **avsddac** (DAC Module)
```bash
git clone https://github.com/vsdip/rvmyth_avsddac_interface.git
```
### step 5: 
    cd VSDBabySoC
### step 6:
    mkdir -p output/pre_synth_sim
### step 7:
    iverilog -o /home/ananya123/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out -DPRE_SYNTH_SIM \
    -I /home/ananya123/VSDBabySoC/src/include -I /home/ananya123/VSDBabySoC/src/module \
    /home/ananya123/VSDBabySoC/src/module/testbench.v
### step 8:
    cd output/pre_synth_sim
### step 9:
    /pre_synth_sim.out
### step 10:
    gtkwave pre_synth_sim.vcd
    
![WhatsApp Image 2024-11-09 at 8 40 14 AM](https://github.com/user-attachments/assets/e44fee49-951d-4a2c-b3ad-c0d1b27f81ff)


### To view the waveform in gtkwave give the following command

     gtkwave pre_synth_sim.vcd

![WhatsApp Image 2024-11-09 at 8 40 13 AM (1)](https://github.com/user-attachments/assets/4db80722-b452-45b9-bc2c-f5868c371473)

Drag and drop the CLK, reset, OUT (DAC) (as analog step), and RV TO DAC [9:0] signals to their respective locations in the simulation tool.

![WhatsApp Image 2024-11-09 at 8 40 13 AM](https://github.com/user-attachments/assets/3059b368-45f3-4c5a-b4e1-4b8a9765b1ea)

# DEBUGGING STEPS
## Debugging Guide: Single Clock Cycle Output Issue in Simulation

When working with digital simulations, encountering an issue where output is only visible for a single clock cycle is common. This issue can have multiple causes, and this guide provides a beginner-friendly explanation of possible sources and debugging steps.

## Possible Causes and Debugging Steps

### 1. Clock Signal Issues
   - *Cause*: The clock signal might not be defined or generated correctly, leading to interruptions in the clock pulses.
   - *Debugging Steps*:
     - Verify that the clock signal is defined in your testbench and is toggling continuously.
     - Check the clock frequency and ensure that the setup is aligned with the design's timing requirements.
     - Inspect the waveform to see if the clock pulse is present throughout the simulation.

### 2. Reset Signal Issues
   - *Cause*: If the reset signal remains active (asserted) throughout the simulation, it can hold the design in a reset state, causing no output to be generated.
   - *Debugging Steps*:
     - Confirm that the reset signal is only active during initialization and then de-asserted to allow the design to operate.
     - Check the waveform to verify that the reset signal is set to inactive after the initial setup period.

### 3. Enable Signal Configuration

  - *Cause*: Some designs include enable signals that control when the circuit should be active. If this signal is only active for one clock cycle, output will also be limited to that cycle.
   - *Debugging Steps*:
     - Inspect the design to identify any enable signals that control output.
     - Ensure that the enable signal remains active for the desired period.
     - Monitor the enable signal in the waveform viewer to confirm it aligns with the expected functionality.

### 4. Simulation Time Limit
   - *Cause*: If the simulation is set to run for a very short time, it may only cover one clock cycle.
   - *Debugging Steps*:
     - Extend the simulation time to capture multiple clock cycles and observe the behavior over a longer period.
     - Ensure that the simulation’s stop time is set to allow enough time for testing multiple cycles.

### 5. Waveform Tool Settings
   - *Cause*: Sometimes, the waveform viewer might be configured to display only a small time window, making it appear as if output is only generated for one cycle.
   - *Debugging Steps*:
     - Adjust the time window in your waveform viewer to see a larger portion of the simulation timeline.
     - Ensure that all signals are visible in the viewer and set to display for the entire simulation duration
     - 
#### pre_synth
     iverilog -o /home/ananya123/VSDBabySoCC/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out -DPRE_SYNTH_SIM     -I 
     /home/ananya123/VSDBabySoCC/VSDBabySoC/src/include -I /home/ananya123/VSDBabySoCC/VSDBabySoC/src/module     
     /home/ananya123/VSDBabySoCC/VSDBabySoC/src/module/testbench.v

![WhatsApp Image 2024-11-10 at 6 42 16 AM](https://github.com/user-attachments/assets/a21ca055-f25f-4428-bfc7-208a65b92297)
![WhatsApp Image 2024-11-10 at 6 42 16 AM (1)](https://github.com/user-attachments/assets/fe819be2-979a-4413-b9ef-d12272f7a717)
