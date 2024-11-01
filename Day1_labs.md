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

# Introduction to Yosys
</p> It's an open-source tool that converts Verilog designs into gate-level representations for digital logic synthesis. 

<img width="640" alt="Screenshot 2024-11-01 123726" src="https://github.com/user-attachments/assets/c4e16ddc-51e1-4ca6-8b9f-bffa840a7740">


### Introduction to Logic Synthesis

Logic synthesis encompasses several key processes:

1. **Translation**: This step transforms HDL code (like Verilog) into an internal representation for further processing.
   
2. **Optimization**: The design is refined to improve area, speed, and power efficiency by simplifying gate structures.

3. **Netlist Generation**: The result is a netlist that details the gates and their interconnections, ready for implementation.

### SYNTHESIS

<img width="610" alt="Screenshot 2024-11-01 123745" src="https://github.com/user-attachments/assets/02f5d5f1-91e7-4873-b614-466558fdac68">

### Why different flavors of gate?

<img width="593" alt="Screenshot 2024-11-01 123816" src="https://github.com/user-attachments/assets/267d8f0b-df7c-4ac5-9ffc-e0705429ef64">

### Why do we need Slow cells?

<img width="558" alt="Screenshot 2024-11-01 123843" src="https://github.com/user-attachments/assets/7bef07b7-a7da-471b-b550-a3381ef6d6b0">

### Faster Cells Vs Slower Cells

<img width="583" alt="Screenshot 2024-11-01 123854" src="https://github.com/user-attachments/assets/a0b2430c-1d44-4831-98a7-661ef67011c6">

### Synthesis Illustration

<img width="620" alt="Screenshot 2024-11-01 123914" src="https://github.com/user-attachments/assets/5d17bd79-9b85-4253-8dbf-6837735665ce">

## Labs Using Yosys and scl180 PDKs
### steps are:
#### Invoke yosys
      yosys 
      
![1](https://github.com/user-attachments/assets/a2ec47f9-1419-4d55-ae34-d092afa909ee)

#### Read liberty files
     read_liberty -lib /home/dhanvanti/scl_pdk_v2/stdlib/fs120/liberty/lib_flow_ff/tsl18fs120_scl_ff.lib
  
![WhatsApp Image 2024-11-01 at 12 01 45 PM](https://github.com/user-attachments/assets/778eda84-c880-40cb-af46-05bdcc060f8c)

#### Read verilog files
     read_verilog good_mux.v
     
![WhatsApp Image 2024-11-01 at 12 01 48 PM](https://github.com/user-attachments/assets/f93cefab-4ade-4fbd-aaeb-3715cd5b7f2d)


#### Run synthesis on top level module
      synth -top good_mux
      
![WhatsApp Image 2024-11-01 at 12 01 47 PM](https://github.com/user-attachments/assets/fc73e5ec-ac01-4baf-b607-44d7f15022b2)

![WhatsApp Image 2024-11-01 at 12 01 46 PM](https://github.com/user-attachments/assets/81e5ee63-1b9b-4794-8aae-f9a8fff24954)

#### logic optimization using ABC algorithm
     abc -liberty /home/dhanvanti/scl_pdk_v2/stdlib/fs120/liberty/lib_flow_ff/tsl18fs120_scl_ff.lib
     
![WhatsApp Image 2024-11-01 at 12 01 46 PM (2)](https://github.com/user-attachments/assets/b72345ac-dcaf-41dc-8b4e-4d910ac52aa8)

![WhatsApp Image 2024-11-01 at 12 01 46 PM (1)](https://github.com/user-attachments/assets/6b5c2def-0272-4bbe-aa42-2a4dea084b1c)

### Use command to view the design 
![WhatsApp Image 2024-11-01 at 12 01 44 PM](https://github.com/user-attachments/assets/97cfb3e7-d5af-433b-b64d-9e638e47cd9e)

![WhatsApp Image 2024-11-01 at 12 01 45 PM (2)](https://github.com/user-attachments/assets/20286d52-7fd1-40f6-92cc-22618b74c456)


#### Write netlist file
     write_verilog good_mux_netlist.v
     !gvim good_mux_netlist.v
![WhatsApp Image 2024-11-01 at 12 33 22 PM (2)](https://github.com/user-attachments/assets/04704919-72a1-4d81-a7e9-15175ae911c5)

#### Write precise netlist file
     write_verilog -noattr good_mux_netlist.v
     !gvim good_mux_netlist.v
     
![WhatsApp Image 2024-11-01 at 12 01 44 PM (1)](https://github.com/user-attachments/assets/381028c3-3b6d-471a-aaba-4443e23c3705)

