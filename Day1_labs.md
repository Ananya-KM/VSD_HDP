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
  
# Labs using iverilog and gtkwave
### LAB 1 -Tools Setup
#### To get started, clone the repository using the following command:


      git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
    

</p> my_lib: This directory contains all the necessary library files. </p>
</p> lib: Here, you’ll find the Sky130 standard cell library used for synthesis.</p>
</p> verilog_files: This folder holds the Verilog source files along with their corresponding testbench files. Each iverilog file is paired with its respective testbench.

![WhatsApp Image 2024-10-31 at 11 59 31 PM (1)](https://github.com/user-attachments/assets/8b36c55b-fdf8-434e-8d3b-b321dec20323)

### Lab 2: Introduction to iverilog gtkwave part1


![WhatsApp Image 2024-10-31 at 11 59 31 PM (2)](https://github.com/user-attachments/assets/beb29686-3378-45ff-ba1b-a223645a43c9)

![WhatsApp Image 2024-10-31 at 11 59 31 PM (3)](https://github.com/user-attachments/assets/2aee61ab-2e87-4deb-b5f4-64ef042199e4)

tep 1: Navigate to the verilog_files directory.

Step 2: Load the design by executing the following command:

bash
Copy code
iverilog good_mux.v tb_good_mux.v

