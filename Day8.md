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

 
