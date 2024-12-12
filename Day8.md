# INTRODUCTION TO CIRCUIT DESIGN AND SPICE SIMUATIONS
**Why do we need SPICE simulations?**  

SPICE simulations verify circuit behavior and performance before implementation. In **circuit design**, logic gates like NAND, NOR, and NOT are built using NMOS and PMOS transistors.  

For example, in an **inverter**:  
- PMOS (pull-up) and NMOS (pull-down) drains connect to the **output** with a capacitive load.  
- Both **gates** connect to the **input**, PMOS source to **VDD**, and NMOS source to **GND**.  

SPICE ensures the circuit meets functionality, timing, and power requirements.

## SPICE Simulation:  

SPICE simulations let us test and fine-tune circuits virtually before building them. For example, if we provide an **input waveform** to a circuit, SPICE generates the **output waveform**, showing how the circuit behaves.  

These waveforms help us measure things like **delay**. By tweaking the design parameters, such as the **width (W)** and **length (L)** of transistors, we can control the **current flow**, which in turn affects the delay. This makes it easier to optimize the circuit for better performance.
![Screenshot 2024-12-12 011351](https://github.com/user-attachments/assets/09835efd-d13a-4596-9d77-df1b65a61271)
![Screenshot 2024-12-12 011401](https://github.com/user-attachments/assets/debd3fe4-f1d9-4806-97d2-91054ed32a27)
 #### on considering the following example
 ![Screenshot 2024-12-12 011413](https://github.com/user-attachments/assets/ce7fd590-029b-4d1e-83da-b6660dd8189c)
 The difference between **CBUF1** and **CBUF2** comes from their **circuit design**, which might have different **drive strengths** or **W/L ratios** (transistor width-to-length).  

The **delay table values** are obtained from **SPICE simulations**, which are also used to verify delays for the circuit design.
### Introduction to Basic Element in Circuit Design - NMOS Transistor
**NMOS Transistor**: An N-type Metal-Oxide-Semiconductor that conducts when a positive voltage is applied to its gate, enabling current flow from drain to source.
 ![Screenshot 2024-12-12 011430](https://github.com/user-attachments/assets/7124668a-4be3-4dfb-a1ba-b7f5f348a8ff)
**Threshold Voltage**: A key parameter that drives SPICE simulations, representing the voltage at which a transistor switches from off to on.  

**Strong Inversion**: The condition where the transistor channel is fully formed, allowing significant current flow.  

**Threshold Voltage with Substrate Potential**: The threshold voltage varies with changes in substrate potential due to the **body effect**.
![Screenshot 2024-12-12 011439](https://github.com/user-attachments/assets/a90c6c53-42f2-4c32-9928-1caf35716a5a)
![Screenshot 2024-12-12 011448](https://github.com/user-attachments/assets/9565b439-4a9c-43ff-944d-dba11e2fb051)
##### Consider potential to Body terminal
![Screenshot 2024-12-12 011455](https://github.com/user-attachments/assets/32b8f4c6-5321-4385-8e19-2801ff3262d9)
![Screenshot 2024-12-12 011505](https://github.com/user-attachments/assets/8672e881-ba44-429c-9ac9-e79acb339942)

**Threshold Voltage at Vsb = 0**: The threshold voltage when the source-to-body voltage is zero.  

**Body Effect Coefficient and Fermi Potential**: Constants provided by the foundry that form the transistor model and are fed into SPICE simulations for various calculations.
![Screenshot 2024-12-12 011511](https://github.com/user-attachments/assets/6e95eb5f-f13f-43ee-b632-1be67fab1c62)
### NMOS Resistive and Saturation Regions of Operation
Resistive region of operation with small drain-source voltage
