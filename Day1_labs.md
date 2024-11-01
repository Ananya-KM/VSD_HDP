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


![WhatsApp Image 2024-10-31 at 11 59 31 PM (2)](https://github.com/user-attachments/assets/beb29686-3378-45ff-ba1b-a223645a43c9)

![WhatsApp Image 2024-10-31 at 11 59 31 PM (3)](https://github.com/user-attachments/assets/2aee61ab-2e87-4deb-b5f4-64ef042199e4)

## Lab 2: Introduction to iverilog gtkwave part1

Step 1: Navigate to the verilog_files directory.
#### Step 2: Load the design by executing the following command:

     iverilog good_mux.v tb_good_mux.v
     
![WhatsApp Image 2024-10-31 at 11 59 31 PM (4)](https://github.com/user-attachments/assets/840c8973-973a-4cca-b957-2baf359d13fb)

A file called a.out is created

![WhatsApp Image 2024-10-31 at 11 59 31 PM (6)](https://github.com/user-attachments/assets/6364cdf6-f235-4746-9a40-f9f73e8fe27b)

Step 3: Execute using ./a.out, it will dump the vcd file
![WhatsApp Image 2024-10-31 at 11 59 31 PM (7)](https://github.com/user-attachments/assets/222beb82-3c84-4e9f-8113-48651a19360b)
Step 4: load vcd file in simulator gtkwave tb_good_mux.vcd
![WhatsApp Image 2024-10-31 at 11 59 31 PM (8)](https://github.com/user-attachments/assets/1e56f4e6-8276-462f-b47e-e6071db48c62)
Click on tb good mux, inputs and outputs signal will appear drag and drop them and click on Zoom fit.

![WhatsApp Image 2024-10-31 at 11 59 31 PM (9)](https://github.com/user-attachments/assets/5cc97a7b-e6fb-43a2-ba8b-002b21c9f541)

To see the transitions of particular input
![WhatsApp Image 2024-10-31 at 11 59 31 PM (10)](https://github.com/user-attachments/assets/f720b025-c709-435e-b16e-7c206511d527)

## Lab 2: Introduction to iverilog gtkwave part2

![WhatsApp Image 2024-10-31 at 11 59 31 PM (12)](https://github.com/user-attachments/assets/cf625cc2-c8b1-44c9-ac5a-013a508a7cf1)
![WhatsApp Image 2024-10-31 at 11 59 31 PM (11)](https://github.com/user-attachments/assets/cbc67ed6-d2ae-4a1f-8079-322028893af9)


