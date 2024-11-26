# GLS OF BABYSOC
## POST-SYNTHESIS SIMULATION

### Purpose of GLS:
Gate-Level Simulation is used to verify the functionality of a design after the synthesis process. Unlike behavioral or RTL (Register Transfer Level) simulations, which are performed at a higher level of abstraction, GLS works on the netlist generated post-synthesis. This netlist includes the actual gates and connections used to implement the design.

### Key Aspects of GLS for BabySoC:
1. **Verification with Timing Information:**
   - GLS is performed using Standard Delay Format (SDF) files to ensure timing correctness.
   - This checks if the SoC behaves as expected under real-world timing constraints.

2. **Design Validation Post-Synthesis:**
   - Confirms that the design's logical behavior remains correct after mapping it to the gate-level representation.
   - Ensures that the design is free from issues like metastability or glitches.

3. **Simulation Tools:**
   - Tools like Icarus Verilog or a similar simulator can be used for compiling and running the gate-level netlist.
   - Waveforms are typically analyzed using GTKWave.

4. **Importance for BabySoC:**
   - BabySoC consists of multiple modules like the RISC-V processor, PLL, and DAC. GLS ensures that these modules interact correctly and meet the timing requirements in the synthesized design.


Here is the step-by-step execution plan for running the  commands manually:
---
### **Step 1: Load the Top-Level Design and Supporting Modules**
```bash
yosys
```

![WhatsApp Image 2024-11-16 at 5 20 29 AM (4)](https://github.com/user-attachments/assets/69c01da4-592e-4165-afcf-d42eb0eab08c)


Inside the Yosys shell, run:
```yosys
read_verilog /home/ananya123/VSDBabySoCC/VSDBabySoC/src/module/vsdbabysoc.v
read_verilog -I /home/ananya123/VSDBabySoCC/VSDBabySoC/src/include /home/ananya123/VSDBabySoCC/src/module/rvmyth.v
read_verilog -I /home/ananya123/VSDBabySoCC/VSDBabySoC/src/include /home/ananya123/VSDBabySoCC/src/module/clk_gate.v

```
![WhatsApp Image 2024-11-16 at 5 54 12 AM](https://github.com/user-attachments/assets/648dc511-7c3c-496a-97c7-a24aa6cb0bae)

![WhatsApp Image 2024-11-16 at 5 20 29 AM (2)](https://github.com/user-attachments/assets/6db87310-6389-4f7c-9418-40e4f6780c18)

![WhatsApp Image 2024-11-16 at 5 20 29 AM (1)](https://github.com/user-attachments/assets/8eddf6c8-c3fb-44d9-b804-5eb836558c44)

---

### **Step 2: Load the Liberty Files for Synthesis**
Inside the same Yosys shell, run:
```yosys
read_liberty -lib /home/ananya123/VSDBabySoCC/VSDBabySoC/src/lib/avsdpll.lib
read_liberty -lib /home/ananya123/VSDBabySoCC/VSDBabySoC/src/lib/avsddac.lib
read_liberty -lib /home/ananya123/VSDBabySoCC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
![WhatsApp Image 2024-11-16 at 5 20 29 AM](https://github.com/user-attachments/assets/2ec505bd-8004-415f-ba9c-3b76a41562f8)

---

### **Step 3: Run Synthesis Targeting `vsdbabysoc`**
```yosys
synth -top vsdbabysoc
```
![WhatsApp Image 2024-11-16 at 5 20 28 AM](https://github.com/user-attachments/assets/8a49050d-55cb-4ae2-9a93-5fe7c2c72710)
![WhatsApp Image 2024-11-16 at 5 20 26 AM](https://github.com/user-attachments/assets/f00545e7-bb37-4444-80e7-0881938fb634)
![WhatsApp Image 2024-11-16 at 5 20 24 AM (2)](https://github.com/user-attachments/assets/655dfaaf-bece-47dc-8a24-bf257e064a4f)
![WhatsApp Image 2024-11-16 at 5 20 24 AM (1)](https://github.com/user-attachments/assets/5d7a9d12-7722-432c-8ad6-270be51b1df9)
![WhatsApp Image 2024-11-16 at 5 20 24 AM](https://github.com/user-attachments/assets/51f25b92-c968-4cf3-b553-21ecdbefc828)
![WhatsApp Image 2024-11-16 at 5 20 23 AM (8)](https://github.com/user-attachments/assets/241a089c-ce62-4f2c-8c6b-9e76d3929197)

---

### **Step 4: Map D Flip-Flops to Standard Cells**
```yosys
dfflibmap -liberty /home/ananya123/VSDBabySoCC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM (7)](https://github.com/user-attachments/assets/566b121d-a5da-47c2-a09b-1660592569c5)

---

### **Step 5: Perform Optimization and Technology Mapping**
```yosys
opt
abc -liberty /home/ananya123/VSDBabySoCC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib -script +strash;scorr;ifraig;retime;{D};strash;dch,-f;map,-M,1,{D}
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM (6)](https://github.com/user-attachments/assets/5657a167-e0e2-431a-882e-4a785b059b5d)
![WhatsApp Image 2024-11-16 at 5 20 23 AM (5)](https://github.com/user-attachments/assets/a0ab61ba-24dc-4b9b-83fa-eb5b78f79f40)

---

### **Step 6: Perform Final Clean-Up and Renaming**
```yosys
flatten
setundef -zero
clean -purge
rename -enumerate
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM (4)](https://github.com/user-attachments/assets/e2fd7bc4-5e8a-4236-84dc-002887f3eb82)

---

### **Step 7: Check Statistics**
```yosys
stat
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM (3)](https://github.com/user-attachments/assets/292c9093-9a6d-417e-b094-0b8a6e27e7c3)
![WhatsApp Image 2024-11-16 at 5 20 23 AM (2)](https://github.com/user-attachments/assets/ce8ad45b-92ae-4cc8-a4dd-0f52028e078e)
![WhatsApp Image 2024-11-16 at 5 20 23 AM (1)](https://github.com/user-attachments/assets/e1741767-2b83-4d88-909e-e5d4c73411f4)

---

### **Step 8: Write the Synthesized Netlist**
```yosys
write_verilog -noattr /home/ananya123/VSDBabySoCC/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v
```
![WhatsApp Image 2024-11-16 at 5 20 23 AM](https://github.com/user-attachments/assets/1e0444b4-ad66-4798-b7f7-7bc1e13cf88a)

---

## POST_SYNTHESIS SIMULATION AND WAVEFORMS
---

### **Step 1: Compile the Testbench**
Run the following `iverilog` command to compile the testbench:
```bash
iverilog -o /home/ananya123/VSDBabySoCC/VSDBabySoC/output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM -DFUNCTIONAL -DUNIT_DELAY=#1 -I /home/ananya123/VSDBabySoCC/VSDBabySoC/src/include -I /home/ananya123/VSDBabySoCC/VSDBabySoC/src/module /home/ananya123/VSDBabySoCC/VSDBabySoC/src/module/testbench.v
```
---
### **Step 2: Navigate to the Post-Synthesis Simulation Output Directory**
```bash
cd output/post_synth_sim/
```
---
### **Step 3: Run the Simulation**

```bash
./post_synth_sim.out
```
---
### **Step 4: View the Waveforms in GTKWave**

```bash
gtkwave post_synth_sim.vcd
```
---

![WhatsApp Image 2024-11-25 at 9 07 01 PM](https://github.com/user-attachments/assets/9d79b832-7315-46ed-b028-e2dd5d14d27a)

![WhatsApp Image 2024-11-25 at 9 07 01 PM (2)](https://github.com/user-attachments/assets/0a6d272d-1aae-45b5-b6aa-914a0087df84)

![WhatsApp Image 2024-11-25 at 9 07 01 PM (1)](https://github.com/user-attachments/assets/239557c2-2447-4cd1-a18f-fb1966feebf2)

