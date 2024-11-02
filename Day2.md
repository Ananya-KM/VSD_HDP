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

## Hierarchial vs Flat Synthesis

In **Hierarchical Synthesis**, each part of the design is worked on separately, and then these parts are combined to create the complete design. 

In **Flat Synthesis**, the whole design is processed all at once, without breaking it down into smaller parts. 

Steps

1. **Invoke Yosys**:
   ```bash
   yosys
   ```

2. **Read Liberty Files**:
   This command loads the library file needed for synthesis.
   ```bash
   read_liberty -lib /home/dhanvanti/scl_pdk_v2/stdlib/fs120/liberty/lib_flow_ff/tsl18fs120_scl_ff.lib
   ```

3. **Read Verilog Files**:
   This command reads in your Verilog design files.
   ```bash
   read_verilog multiple_modules.v
   ```

4. **Run Synthesis on Top Level Module**:
   This tells Yosys to synthesize the specified top-level module.
   ```bash
   synth -top multiple_modules
   ```

5. **Logic Optimization Using ABC Algorithm**:
   This step performs logic optimization on the synthesized design using the ABC tool, leveraging the same liberty file.
   ```bash
   abc -liberty /home/dhanvanti/scl_pdk_v2/stdlib/fs120/liberty/lib_flow_ff/tsl18fs120_scl_ff.lib
   ```

6. **Show the Module**:
   Finally, this command displays the synthesized design.
   ```bash
   show
   ```
![WhatsApp Image 2024-11-02 at 8 35 03 AM](https://github.com/user-attachments/assets/c353d49c-2214-4c92-80f6-ce3addeb993e)

![WhatsApp Image 2024-11-02 at 8 35 03 AM (1)](https://github.com/user-attachments/assets/f4878c53-8ac3-4c7b-aba5-e3d030ebd4a8)

![WhatsApp Image 2024-11-02 at 8 35 03 AM (2)](https://github.com/user-attachments/assets/08981d06-693b-487c-96a9-2aef9a491f94)

## FLAT SYNTHESIS
Steps


1. **Flatten the Design**:
   This command flattens the hierarchical design, combining all modules into a single flat structure.
   ```bash
   flatten
   ```

2. **Write the Flattened Design to a Verilog File**:
   This command writes the flattened design to a new Verilog file without any attributes.
   ```bash
   write_verilog -noattr multiple_module_flat.v
   ```

3. **Open the Flattened Verilog File**:
   This command opens the newly created Verilog file in the gVim editor for further editing or review.
   ```bash
   !gvim multiple_module_flat.v
   ```
![WhatsApp Image 2024-11-02 at 8 35 03 AM (3)](https://github.com/user-attachments/assets/f28bd7f2-98dd-4435-983e-ab13e3ec90eb)

![WhatsApp Image 2024-11-02 at 8 35 03 AM (4)](https://github.com/user-attachments/assets/331cc630-03ac-47fa-8ca3-d6372a1a8490)

![WhatsApp Image 2024-11-02 at 8 35 03 AM (5)](https://github.com/user-attachments/assets/c79afd97-8490-47de-91da-77e2700560af)




