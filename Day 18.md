# Autotuner Setup for VSDBabySoC
AutoTuner in OpenROAD is a framework for optimizing physical design parameters to improve performance, power, and area (PPA) metrics. This setup integrates AutoTuner with VSDBabySoC, enabling automated tuning of design constraints using machine learning techniques. The process involves setting up dependencies, configuring the tuning environment, and running AutoTuner to analyze and optimize the SoC's placement and routing parameters.




### **AutoTuner Setup for VSDBabySoC**

**Step 1: Navigate to AutoTuner Directory**
```bash
cd /home/ananya123/OpenROAD-flow-scripts/tools/AutoTuner
```

**Step 2: List the Contents of the Directory**
```bash
ls -la
```
![WhatsApp Image 2025-02-04 at 9 08 15 AM](https://github.com/user-attachments/assets/4aedab3d-5755-4629-9eda-4434872b4687)

**Step 3: Update the `requirements.txt` File for Pip Version Compatibility**  
Open the `requirements.txt` file and update the pip version in it for `ray==2.31.0` 

![WhatsApp Image 2025-02-04 at 9 29 26 AM](https://github.com/user-attachments/assets/6de9192f-5b33-44f0-89a5-5072e0f2a80c)



**Step 4: Run the `installer.sh` Command**  
Execute the installer script to begin the installation of dependencies and setup:
```bash
 installer.sh
```
![WhatsApp Image 2025-02-04 at 9 32 07 AM](https://github.com/user-attachments/assets/232507b3-24a8-45a9-9834-08ac5199faa2)

![WhatsApp Image 2025-02-04 at 9 08 15 AM (3)](https://github.com/user-attachments/assets/d453c992-cee4-42bc-915d-3c592e19a331)

