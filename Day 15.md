# Extraction of SPEF and Verilog Files post Routing
Here are the steps only until generating the post-placement Verilog file:



### **Step 1: Launch OpenROAD**
Start OpenROAD from your terminal:
```bash
openroad
```

---

### **Step 2: Run the Commands in Sequence**

#### **1. Read LEF Files**
Load the technology and standard cell LEF files:
```tcl
read_lef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/lef/sky130hd.lef
read_lef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/lef/avsdpll.lef
read_lef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/lef/avsddac.lef
```

#### **2. Read Liberty File**
Load the timing library:
```tcl
read_liberty /home/ananya123/OpenROAD-flow-scripts/flow/platforms/sky130hd/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

#### **3. Read DEF File**
Load the DEF file after the placement and routing stage:
```tcl
read_def /home/ananya123/OpenROAD-flow-scripts/flow/results/sky130hd/vsdbabysoc/base/5_route.def
```

#### **4. Write Post-Placement Verilog**
Generate the Verilog netlist and save it:
```tcl
write_verilog /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/vsdbabysoc_post_place.v
```

---

These steps will guide you to generate the **post-placement Verilog file** successfully. Let me know if you need further assistance!




