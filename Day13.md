# **OpenROAD installation guide**  
**OpenROAD** is an open-source, fully automated RTL-to-GDSII flow for digital integrated circuit (IC) design. It supports synthesis, floorplanning, placement, clock tree synthesis, routing, and final layout generation. The tool is built to enable rapid design iterations and experimentation, making it ideal for academic and industrial use.  

---

### **Steps to Install OpenROAD and Run GUI**  

#### **1. Clone the OpenROAD Repository**  
      git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
      cd OpenROAD-flow-script
#### **2. Run the Setup Script**  
       sudo ./setup.sh

![WhatsApp Image 2024-12-17 at 8 48 25 AM (2)](https://github.com/user-attachments/assets/9cfc4ee9-6b62-4f48-9ec9-011136c577d3)

#### **3. Build OpenROAD**  

      ./build_openroad.sh --local

![WhatsApp Image 2024-12-17 at 8 48 25 AM](https://github.com/user-attachments/assets/3c6f631c-8ce1-460e-8200-ca2f9c339af3)

#### **4. Verify Installation**  

       source ./env.sh
       yosys -help  
       openroad -help


![WhatsApp Image 2024-12-17 at 8 48 24 AM (2)](https://github.com/user-attachments/assets/0dbf32be-2174-4a18-9b0d-b1cfe08f208b)
![WhatsApp Image 2024-12-17 at 8 48 24 AM (1)](https://github.com/user-attachments/assets/f3530a26-7ac6-4109-9093-c3bc24ef29b5)



#### **5. Run the OpenROAD Flow**  
       cd flow
       make

![WhatsApp Image 2024-12-17 at 8 48 24 AM](https://github.com/user-attachments/assets/9554cf56-e6bf-44f1-8096-80c0b4c48777)

##### 3. Launch the graphical user interface (GUI) to visualize the final layout:  
      make gui_final
  
 ![WhatsApp Image 2024-12-17 at 8 48 23 AM](https://github.com/user-attachments/assets/7ca2908e-2434-4ecf-b0ce-f6e30055eec2)
#### directory structure

![WhatsApp Image 2024-12-17 at 8 48 23 AM (1)](https://github.com/user-attachments/assets/7675831c-7afc-4fb4-b3a4-0433bb7d6f16)

