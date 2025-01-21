# Extraction of SPEF and Verilog Files Post_Routing
 steps only until generating the post-placement Verilog file:



### **Step 1: Launch OpenROAD**
Start OpenROAD from your terminal:
```bash
openroad
```

---

![WhatsApp Image 2025-01-21 at 6 06 55 AM](https://github.com/user-attachments/assets/97bed788-041f-4118-b877-80843ac8a327)

### **Step 2: Run the Commands in Sequence**

#### **1. Read LEF Files**
Load the technology and standard cell LEF files:
```tcl
read_lef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/lef/sky130hd.lef
read_lef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/lef/avsdpll.lef
read_lef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/lef/avsddac.lef
```
![WhatsApp Image 2025-01-21 at 6 02 31 AM](https://github.com/user-attachments/assets/9b68ab76-2091-4a40-b388-f8acb5309f14)


#### **2. Read Liberty File**
Load the timing library:
```tcl
read_liberty /home/ananya123/OpenROAD-flow-scripts/flow/platforms/sky130hd/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
![WhatsApp Image 2025-01-21 at 6 02 30 AM](https://github.com/user-attachments/assets/c2979366-f996-4933-a7aa-dc5f4d5d7731)

#### **3. Read DEF File**
Load the DEF file after the placement and routing stage:
```tcl
read_def /home/ananya123/OpenROAD-flow-scripts/flow/results/sky130hd/vsdbabysoc/base/5_route.def
```
---
![WhatsApp Image 2025-01-21 at 6 02 30 AM (1)](https://github.com/user-attachments/assets/86e1df6a-49ca-478c-8db2-7b64608ca46c)

### **4. Define Process Corner**
Set the process corner for parasitic extraction:
```tcl
define_process_corner -ext_model_index 0 /home/ananya123/OpenROAD-flow-scripts/external-resources/open_pdks/sky130/openlane/rules.openrcx.sky130A.nom.calibre
```

---

### **5. Extract Parasitics**
Perform the parasitic extraction:
```tcl
extract_parasitics -ext_model_file /home/ananya123/OpenROAD-flow-scripts/external-resources/open_pdks/sky130/openlane/rules.openrcx.sky130A.nom.calibre
```

---

![WhatsApp Image 2025-01-21 at 6 02 30 AM (2)](https://github.com/user-attachments/assets/c5212bb6-3ff2-4995-991d-9181a8f50d4c)

### **6. Write SPEF File**
Generate the SPEF file and save it:
```tcl
write_spef /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/vsdbabysoc.spef
```
---
![WhatsApp Image 2025-01-21 at 6 02 29 AM](https://github.com/user-attachments/assets/c25b6bea-85c1-4d1d-aa24-2e8355ea46f2)
![WhatsApp Image 2025-01-21 at 6 02 29 AM (1)](https://github.com/user-attachments/assets/3c4aa5cd-048c-4673-96e6-374935664ce7)

### **7. Write Post-Placement Verilog File**
Save the post-placement Verilog netlist:
```tcl
write_verilog /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/vsdbabysoc/vsdbabysoc_post_place.v
```
---
![WhatsApp Image 2025-01-21 at 6 02 30 AM (3)](https://github.com/user-attachments/assets/0a43a5c3-ff11-425a-8c71-80212f36038f)
![WhatsApp Image 2025-01-21 at 6 02 29 AM (2)](https://github.com/user-attachments/assets/e4e27ffb-ed5c-47ea-93bf-c0c1371dd01b)


