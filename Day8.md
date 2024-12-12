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
![Screenshot 2024-12-12 011536](https://github.com/user-attachments/assets/47aec678-7c37-48ec-b10c-37915e023577)
![Screenshot 2024-12-12 011613](https://github.com/user-attachments/assets/a12d1f14-1dfa-45b5-9d05-f1eb133ed09c)
**Drift Current**: Current caused by a potential difference across the material.  
**Diffusion Current**: Current resulting from a difference in carrier concentration.  
**Cox**: A constant value provided by the foundry, representing oxide capacitance.
![Screenshot 2024-12-12 011626](https://github.com/user-attachments/assets/ba5e7f84-ca44-4a6c-9b77-8551006c659e)
![Screenshot 2024-12-12 011642](https://github.com/user-attachments/assets/a7661c83-b46e-42d9-9b2b-069786ebf898)
#### Drain current model for linear region of operation
![Screenshot 2024-12-12 011652](https://github.com/user-attachments/assets/3ff39b7f-8710-4a6e-b7a4-c50370488285)
![Screenshot 2024-12-12 011710](https://github.com/user-attachments/assets/b157e9df-db88-4289-9634-7ad4341a4d1b)
![Screenshot 2024-12-12 011723](https://github.com/user-attachments/assets/601b8cfd-acc6-4aa2-8df8-076df0eb9062)

**SPICE Conclusion to Resistive Operation**:  
SPICE simulations allow us to calculate the **drain current (Id)** for different **Vgs** values by sweeping **Vds** for each **Vgs** until **Vgs - Vt** is reached. This helps in generating accurate **Id-Vds** curves and understanding the transistor's behavior.

**Saturation Region/Pinch-off Region Condition**:  
In the saturation (or pinch-off) region, the drain current **Id** becomes independent of **Vds** and depends only on **Vgs**, as long as **Vds ≥ Vgs - Vt**. This is where the transistor is fully "on" and conducting.

![Screenshot 2024-12-12 011739](https://github.com/user-attachments/assets/67f73504-79b1-4c3b-838e-e4b7fb773fd9)
![Screenshot 2024-12-12 011812](https://github.com/user-attachments/assets/30ef8329-e4fa-4400-9050-f12202c6a03e)
![Screenshot 2024-12-12 011837](https://github.com/user-attachments/assets/c46a22df-049b-40d5-af77-9ecf4325c723)
![Screenshot 2024-12-12 011846](https://github.com/user-attachments/assets/42bf30ca-e741-46c0-8be4-a4a91d58ad06)
![Screenshot 2024-12-12 011901](https://github.com/user-attachments/assets/1307efa5-544f-4630-ad70-6e8ffa7fbfdc)

**SPICE Conclusion to Resistive Operation**:  
SPICE simulations allow us to calculate the **drain current (Id)** for different **Vgs** values by sweeping **Vds** for each **Vgs** until **Vgs - Vt** is reached. This helps in generating accurate **Id-Vds** curves and understanding the transistor's behavior.

**Saturation Region/Pinch-off Region Condition**:  
In the saturation (or pinch-off) region, the drain current **Id** becomes independent of **Vds** and depends only on **Vgs**, as long as **Vds ≥ Vgs - Vt**. This is where the transistor is fully "on" and conducting.

![Screenshot 2024-12-12 011912](https://github.com/user-attachments/assets/d18f4224-e669-458b-9ebf-f58ecbb5a635)
![Screenshot 2024-12-12 011921](https://github.com/user-attachments/assets/24495c06-a43f-4c90-8dac-2d192d7101c8)
**SPICE Netlist Example**:  

- **M1 vdd n1 0 0 nmos W=1.8u L=1.2u**: Defines an **NMOS** transistor with gate width 1.8µ and length 1.2µ, connecting **vdd** (drain), **n1** (gate), **0** (source and substrate).  
- **R1 in n1 55**: Defines a **resistor** with value 55Ω between **in** and **n1**.  
- **Vdd vdd 0 2.5**: Defines a **voltage source** of 2.5V between **vdd** and ground (0).  
- **Vin in 0 2.5**: Defines an **input voltage source** of 2.5V between **in** and ground (0).  

This structure is used to describe circuit components and connections for simulation.
![Screenshot 2024-12-12 011936](https://github.com/user-attachments/assets/9390da37-d99d-49f5-a64d-b2d3e24e9cea)
#### Model to get NMOS
![Screenshot 2024-12-12 011947](https://github.com/user-attachments/assets/b9584758-fc89-4fd9-a67a-2f3648c25d66)
![Screenshot 2024-12-12 012002](https://github.com/user-attachments/assets/0a50ce1c-e003-43ce-adfb-1fd10313bf10)

# LABS
**1. Introduction to SPICE**

SPICE (Simulation Program with Integrated Circuit Emphasis) is a powerful tool used for simulating the behavior of electronic circuits. It allows circuit designers to analyze and validate designs before fabrication by providing insights into performance metrics such as voltage, current, and power consumption.

**SPICE Lab with Sky130 Models**

To use SPICE with Sky130 technology, you can clone the relevant GitHub repository containing Sky130 models and circuits for simulation.

- **Clone the repo**:  
  Clone the repository with the following command:  
  ```bash
  git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
  ```

**3 Important Files in the Repo**:

1. **`/sky130CircuitDesignWorkshop/design/sky130_fd_pr/cells/nfet_01v8/sky130_fd_pr__nfet_01v8__tt.pm3.spice`**  
   This file contains the SPICE model for the **NFET (N-channel MOSFET)** in the Sky130 process at typical (tt) conditions.

2. **`/sky130CircuitDesignWorkshop/design/sky130_fd_pr/cells/nfet_01v8/sky130_fd_pr__nfet_01v8__tt.corner.spice`**  
   This file provides the corner model for the **NFET**, used for simulating different process variations.

3. **`/sky130CircuitDesignWorkshop/design/sky130_fd_pr/models/sky130.lib.pm3.spice`**  
   This library file contains all the **SPICE models** for components in the Sky130 process node.

You can download ngspice for Windows from the official source using the following link:

[ngspice Downloads - SourceForge](http://ngspice.sourceforge.net/download.html)
### EXAMPLE
    
    *Model Description
    .param temp=27

    *Including sky130 library files
    .lib "sky130_fd_pr/models/sky130.lib.spice" tt

    *Netlist Description
     XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=5 l=2
     R1 n1 in 55
     Vdd vdd 0 1.8V
     Vin in 0 1.8V

    *simulation commands
    .op
    .dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

    .control

     run
     display
    setplot dc1
    .endc
    .end

### To plot the waveforms in ngspice
    ngspice day1_nfet_idvds_L2_W5.spice
    plot -vdd#branch

### The plot of Ids vs Vds over constant Vgs:
![WhatsApp Image 2024-12-10 at 9 31 06 PM](https://github.com/user-attachments/assets/5b9a1024-cd61-428c-919c-af8bfdbf694d)
![WhatsApp Image 2024-12-10 at 9 31 06 PM (2)](https://github.com/user-attachments/assets/99893245-4e92-48f1-83a1-f66699612970)
![WhatsApp Image 2024-12-10 at 9 31 06 PM (1)](https://github.com/user-attachments/assets/718c78cf-4b07-49fd-b774-913e2e19d72f)




