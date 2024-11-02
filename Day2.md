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
   read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1V80.v
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
   abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1V80.v
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

## Submudule level Synthesis
Repeat the above steps and do the synthesis for sub_module1
![WhatsApp Image 2024-11-02 at 8 35 03 AM (7)](https://github.com/user-attachments/assets/aed3a391-b3a9-4fad-8184-c3703ec3824d)

![WhatsApp Image 2024-11-02 at 8 35 03 AM (6)](https://github.com/user-attachments/assets/5f053b74-869c-423b-b3ac-8d077f74668b)

![WhatsApp Image 2024-11-02 at 8 35 00 AM (1)](https://github.com/user-attachments/assets/cc3e1e5d-919a-4b88-ba4f-e50293ca6bf1)

![WhatsApp Image 2024-11-02 at 8 35 00 AM](https://github.com/user-attachments/assets/c5973c41-8486-4fb4-b202-9a6d9424128a)

## Flop Coding Styles
### part 1: Different Flip Flops
step 1: Run iverilog for an Asynchronous Reset D-Flip Flop using its testbench

step 2: Execute the output file (a.out)

![WhatsApp Image 2024-11-02 at 8 35 00 AM (2)](https://github.com/user-attachments/assets/0591fb79-195b-4d81-8d48-971a58b667cb)



step 3: Run GTKWave to view the behaviour of the Asynchronous Reset D-Flip Flop
Observe the behaviour of the Asynchronous Reset D-Flip Flop

![WhatsApp Image 2024-11-02 at 8 34 59 AM](https://github.com/user-attachments/assets/c52d10f2-2b90-4ed7-9798-e686e2de3d31)

![WhatsApp Image 2024-11-02 at 8 34 59 AM (1)](https://github.com/user-attachments/assets/a04ecfac-007c-4804-b843-9ac2f4f2c203)

step 4:Repeat Steps 1-3 using the Asynchronous Set D-Flip Flop
![WhatsApp Image 2024-11-02 at 8 34 59 AM (2)](https://github.com/user-attachments/assets/9b67da09-e619-42c9-aba4-cd5380af1cc7)

step 5:Observe the behaviour of the Asynchronous Set D-Flip Flop
![WhatsApp Image 2024-11-02 at 8 34 59 AM (3)](https://github.com/user-attachments/assets/f3b6867c-2625-4c76-ab57-ab31a46492ac)

![WhatsApp Image 2024-11-02 at 8 34 59 AM (4)](https://github.com/user-attachments/assets/43d21906-28f0-411c-9e98-86fa0614437c)

step 6:Repeat Steps 1-3 using the Synchronous Reset D-Flip Flop 

![WhatsApp Image 2024-11-02 at 8 34 59 AM (7)](https://github.com/user-attachments/assets/92e7741e-242d-4e09-aca3-c672cbae3fc5)

</p> Observe the behaviour of the Synchronous Reset D-Flip Flop

![WhatsApp Image 2024-11-02 at 8 34 59 AM (5)](https://github.com/user-attachments/assets/e13b5354-80e0-4a3c-9429-635af69637dd)

![WhatsApp Image 2024-11-02 at 8 34 59 AM (6)](https://github.com/user-attachments/assets/03c934e0-7801-45c5-879b-0cae5ca3dbce)

### PART 2 : FLOP SYNTHESIS

1. **Read the Library**:
   ```bash
   read_liberty -lib /path/to/your/library.lib
   ```

2. **Read the Verilog File**:
   ```bash
   read_verilog dff.v
   ```

3. **Define the Top-Level Module to Synthesize**:
   ```bash
   synth -top dff
   ```
 ![WhatsApp Image 2024-11-02 at 8 34 59 AM](https://github.com/user-attachments/assets/92a455a1-91eb-4d69-94da-88a873ac9d2c)
   
![WhatsApp Image 2024-11-02 at 8 34 59 AM (1)](https://github.com/user-attachments/assets/1eade65f-b7af-475a-b1c9-f6de69365183)

![WhatsApp Image 2024-11-02 at 8 34 59 AM (2)](https://github.com/user-attachments/assets/7121b456-c26a-453a-a338-6e0c43391cf4)

![WhatsApp Image 2024-11-02 at 8 34 59 AM (3)](https://github.com/user-attachments/assets/8fef56d5-0b2b-4b93-b423-4e676db1b609)

Execute show to view the netlist for the Asynchronous Reset D-Flip Flop

![WhatsApp Image 2024-11-02 at 8 34 59 AM (4)](https://github.com/user-attachments/assets/34e29130-5eba-4705-880a-74b5e26ebfd5)


Execute show to view the netlist design for the Ashynchronous Set D-Flip Flop

![WhatsApp Image 2024-11-02 at 8 34 59 AM (5)](https://github.com/user-attachments/assets/150893ae-4ffb-4e6d-98a8-1575055d6e15)

Execute show to view the netlist design for the Synchronous Reset D-Flip Flop

![WhatsApp Image 2024-11-02 at 8 34 59 AM (6)](https://github.com/user-attachments/assets/7ea9f83a-6ce3-4b8c-9eb2-c97b35feeb63)

## Special Case Optimization
### 1. mul2 Synthesis

1. **Read the Verilog File**:
   ```bash
   read_verilog mult_2.v
   ```

2. **Synthesize the Top-Level Module**:
   ```bash
   synth -top mult2
   ```
 ![WhatsApp Image 2024-11-02 at 8 34 59 AM (11)](https://github.com/user-attachments/assets/f67f7f41-536c-4d0e-be4c-27276f3e2e08)
 ![WhatsApp Image 2024-11-02 at 8 34 59 AM (8)](https://github.com/user-attachments/assets/80474427-9dd5-4bd6-8cc6-4f1a0cff3851)
![WhatsApp Image 2024-11-02 at 8 34 59 AM (9)](https://github.com/user-attachments/assets/4f62c5df-a938-4508-9d33-7904ea606a49)
![WhatsApp Image 2024-11-02 at 8 34 59 AM (10)](https://github.com/user-attachments/assets/660c9877-e804-4653-a1fe-848deb355c10)

### 2.mul8 Synthesis

1. **Read the Verilog File**:
   ```bash
   read_verilog mult_8.v
   ```

2. **Synthesize the Top-Level Module**:
   ```bash
   synth -top mult8
   ```
![WhatsApp Image 2024-11-02 at 8 34 59 AM (3)](https://github.com/user-attachments/assets/102c86f3-643b-44bd-bb62-b2c696bb36be)


![WhatsApp Image 2024-11-02 at 8 34 59 AM](https://github.com/user-attachments/assets/b41c5d43-c740-4df7-a631-85a69420e929)

 ![WhatsApp Image 2024-11-02 at 8 34 59 AM (1)](https://github.com/user-attachments/assets/4ab0041b-8de6-44e3-9645-f72d296d006e)
   
![WhatsApp Image 2024-11-02 at 8 34 59 AM (2)](https://github.com/user-attachments/assets/3fc04c95-3657-4fee-87b0-681686390bee)

