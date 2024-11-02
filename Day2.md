# DAY 2
## Timing Libraries, Hierarchical vs Flat Synthesis, and Efficient Flop Coding Styles
### Introduction to timing.libs
The timing library named `sky130_fd_sc_hd__tt_025C_1v80.lib` is associated with the SkyWater 130nm process design kit (PDK). Here's a breakdown:

- **Sky130**: Refers to the 130nm technology node developed by SkyWater.
- **fd_sc_hd**: Indicates that it's a fully-depleted, high-density standard cell library.
- **tt_025C**: Denotes the typical-typical process corner at a temperature of 25°C.
- **1v80**: Indicates a nominal supply voltage of 1.8 volts.

This library is essential for designing digital circuits using this specific technology and parameters.

![WhatsApp Image 2024-11-02 at 8 35 04 AM](https://github.com/user-attachments/assets/ff945ccd-9920-4758-963b-97e9b0be30c7)

### UNDERSTANDING THE CELLS
The library name contains key information about its specifications:

- **Technology Node**: The library is based on a 130nm technology node.
- **PVT Corner**: The designation `tt_025C_1V80` indicates the process, voltage, and temperature (PVT) corner:
  - **tt**: Typical type library
  - **025C**: Operating temperature of 25°C
  - **1V80**: Operating voltage of 1.8V

These parameters define the operating conditions for the cells in the library.

In the `.lib` file, the following details are specified:

- **Technology**: The library is designed for CMOS technology.
- **Delay Module**: Contains a lookup table for delay values.
- **Time Unit**: Measured in nanoseconds (1ns).
- **Voltage Unit**: Measured in volts (1V).
- **Leakage Power Unit**: Measured in nanowatts (1nW).
- **Current Unit**: Measured in milliamperes (1mA).
- **Pulling Resistance Unit**: Measured in kilohms (1kΩ).
- **Capacitive Load Unit**: Measured in picofarads (pF).

These parameters define the operational characteristics of the library cells.

