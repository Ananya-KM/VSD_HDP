# Day 1: Introduction to Verilog RTL design and Synthesis
### SIMULATOR
</p> A simulator is a tool used to verify and analyze the design of digital systems. Iverilog is one example of such a simulator.</p>

### DESIGN
</p> Design is the actual Verilog code which has the intended functionality to meet with the required specifications. </p>

### TESTBENCH
</p> Testbench is the setup to apply the stimulus(test_vectors) to the design to check its functionality. </p>

### How Does a Simulator Work?
</p> Simulator looks for changes on the input signals
Upon change to the input signal output is evaluated</p>
If no change to the input signal no change to output

# Structure of Test bench
<img width="582" alt="Screenshot 2024-10-31 075112" src="https://github.com/user-attachments/assets/279c3327-f383-4196-9e0d-f3fc6892d454">

## Note:
</p> Design may have one or more primary inputs, one or more primary outputs. </p>
Testbench does not have Primary input or primary outputs.

# Iverilog based simulation flow
  <img width="612" alt="Screenshot 2024-10-31 075127" src="https://github.com/user-attachments/assets/7fe371c6-8a25-4567-93a0-e3b06476f9e9">
