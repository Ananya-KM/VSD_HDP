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
#### Pre-synthesis Simulation

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


### To view the waveform in gtkwave give the following command

     gtkwave pre_synth_sim.vcd
     
Drag and drop the CLK, reset, OUT (DAC) (as analog step), and RV TO DAC [9:0] signals to their respective locations in the simulation tool.
