# **OpenROAD installation guide**  
**OpenROAD** is an open-source, fully automated RTL-to-GDSII flow for digital integrated circuit (IC) design. It supports synthesis, floorplanning, placement, clock tree synthesis, routing, and final layout generation. The tool is built to enable rapid design iterations and experimentation, making it ideal for academic and industrial use.  

---

### **Steps to Install OpenROAD and Run GUI**  

#### **1. Clone the OpenROAD Repository**  
Download the OpenROAD Flow Scripts repository:  
```bash
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
```

---

#### **2. Run the Setup Script**  
Set up the environment and tools by running:  
```bash
sudo ./setup.sh
```

---

#### **3. Build OpenROAD**  
Build OpenROAD locally:  
```bash
./build_openroad.sh --local
```

---

#### **4. Verify Installation**  
1. Source the environment script:  
   ```bash
   source ./env.sh
   ```
2. Check if OpenROAD and Yosys are installed:  
   ```bash
   yosys -help  
   openroad -help
   ```

---

#### **5. Run the OpenROAD Flow**  
1. Go to the **flow** directory:  
   ```bash
   cd flow
   ```
2. Run a sample design flow:  
   ```bash
   make
   ```
3. Launch the graphical user interface (GUI) to visualize the final layout:  
   ```bash
   make gui_final
   ```

---

