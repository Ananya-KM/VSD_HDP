# **1. Voltage Transfer Characteristics: SPICE Simulations**  
For a **CMOS inverter**, the **SPICE deck** includes:

- **Component Connectivity:** Define connections between components like **PMOS**, **NMOS**, **Vdd**, **Vss**, and **Vin/Vout**.
- **Component Values:** Specify values for components such as **threshold voltages (Vth)**, **transistor sizes**, and **supply voltages**.
- **Identify Nodes:** Identify all electrical nodes like **Vin**, **Vout**, **source**, **drain**, and **bulk** for both transistors.
- **Name Nodes:** Assign names to each node, ensuring clear identification during simulations (e.g., **Vout** for the output node).
![Screenshot 2024-12-13 003927](https://github.com/user-attachments/assets/cbf4ee58-97a1-4389-96d3-f56df12d93e6)
### SPICE simulation for CMOS inverter
SPICE Netlist for CMOS Inverter
A **SPICE netlist** for a CMOS inverter includes transistor models, power supply connections, input voltage source, transistor specifications (PMOS and NMOS), and simulation commands (e.g., `.tran` for transient analysis).
![Screenshot 2024-12-13 003936](https://github.com/user-attachments/assets/833cd2db-1557-497c-be4f-c2ee86a120ee)
Same Wn/Ln = Wp/Lp = 1.5. Plot out vs in:
![Screenshot 2024-12-13 003947](https://github.com/user-attachments/assets/cbe47c76-eadf-433c-a4be-5d08b6e95f44)
Now, Wn/Ln = 1.5 and Wp/Lp = 3.75. Plot out vs in:
![Screenshot 2024-12-13 003956](https://github.com/user-attachments/assets/37b73a91-1e97-4cd5-924a-4247654711a3)
## **Static Behavior Evaluation: CMOS Inverter Robustness and Switching Threshold (Vm)**  
The **switching threshold (Vm)** is the point where **Vin = Vout**, and both transistors are in saturation (since **Vds = Vgs**). At **Vm**, maximum power is drawn due to large current, and it can be graphically found at the intersection of the **VTC** with the **Vin = Vout** line. The analytical expression for **Vm** is obtained by equating the drain currents of PMOS and NMOS (**IDSn = IDSp**).
![Screenshot 2024-12-13 004003](https://github.com/user-attachments/assets/f2ac7e8f-1cce-4613-94a8-bb3462375d5e)
![Screenshot 2024-12-13 004012](https://github.com/user-attachments/assets/b1f8f7ae-775d-465d-b22d-a6a700f4384d)

In the **velocity-saturated** case, the **switching threshold (Vm)** is the point where both **NMOS** and **PMOS** transistors are in saturation, and the drain currents are equal. This occurs when the **VDS** of both devices is less than the saturation voltage, i.e., **VDSAT < (Vm − VT)**. The threshold voltage **Vm** can be derived by equating the drain currents of both transistors, with the device widths and lengths (W/L ratios) playing a key role in determining the point where both transistors conduct equally.
![Screenshot 2024-12-13 004020](https://github.com/user-attachments/assets/87908ece-64ca-4866-b973-7705ee51066a)
![Screenshot 2024-12-13 004028](https://github.com/user-attachments/assets/b2b0e2f1-14b4-4360-8fee-7636da0c1a5d)
![Screenshot 2024-12-13 004037](https://github.com/user-attachments/assets/9180b205-11f1-42ed-bde0-52b2541725ed)
![Screenshot 2024-12-13 004046](https://github.com/user-attachments/assets/69898e46-2849-4fdb-97a2-8fd9c390ccf8)
![Screenshot 2024-12-13 004053](https://github.com/user-attachments/assets/ef02f187-26e5-43a4-8ee4-c476d5b225fb)


---

## Velocity Saturation and Switching Threshold (Vm) Analysis

- **Case 1: Velocity Saturation Occurs**  
  - Happens in short-channel devices or high supply voltage.  
  - Switching threshold **Vm** occurs when currents of PMOS and NMOS transistors are equal.  
  - The ratio **r** (PMOS to NMOS strength) influences **Vm**.  
  - For **Vm ≈ VDD/2**, **r ≈ 1**.  
  - **Vm** can be adjusted by changing the PMOS or NMOS width:  
    - Increase PMOS width → shift **Vm** upwards.  
    - Increase NMOS width → shift **Vm** downwards.  

- **Case 2: Velocity Saturation Does Not Occur**  
  - Applies to long-channel devices or low supply voltage.  
  - The switching threshold **Vm** is still affected by **r** but with a simpler formula.  
  - If **r ≈ 1**, **Vm** is near **VDD/2**.

- **PMOS Width Effect on VTC**  
  - Increasing PMOS width shifts **Vm** upwards.  
  - Increasing NMOS width shifts **Vm** downwards.  
  - **Vm** is relatively stable with small variations in transistor ratios.

![Screenshot 2024-12-13 004109](https://github.com/user-attachments/assets/96db3cee-e37e-483c-bc26-b0b73a5e9879)
### Applications of CMOS inverter in clock network and STA
![Screenshot 2024-12-13 004117](https://github.com/user-attachments/assets/eca7545e-77fd-445f-9cb3-e4bab470e467)
![Screenshot 2024-12-13 004125](https://github.com/user-attachments/assets/5c1f76b4-c628-4c1a-99b6-a284ddd10546)
![Screenshot 2024-12-13 004137](https://github.com/user-attachments/assets/3e8d32f4-0f22-481c-813f-3c5dcbfa747b)
![Screenshot 2024-12-13 004148](https://github.com/user-attachments/assets/354c9277-12c2-45b0-b4af-2f20acf4d2e6)
# LABS
## 1. Voltage transfer characteristics: SPICE simulations
#### Sky130 SPICE simulation for CMOS - VTC
     *Model Description
     .param temp=27

      *Including sky130 library files
      .lib "sky130_fd_pr/models/sky130.lib.spice" tt

      *Netlist Description
       XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=0.84 l=0.15
       XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15
       Cload out 0 50fF
       Vdd vdd 0 1.8V
       Vin in 0 1.8V

       *simulation commands
        .op
       .dc Vin 0 1.8 0.01

        .control
         run
        setplot dc1
        display
        .endc
        .end
        
![WhatsApp Image 2024-12-12 at 10 59 21 PM](https://github.com/user-attachments/assets/e5b60ff6-bc40-47f8-bedd-d0e1f406fae6)
![WhatsApp Image 2024-12-12 at 10 59 21 PM (1)](https://github.com/user-attachments/assets/1d249ffe-65a4-4f87-a632-1c8114f4ff69)

- **Switching Threshold (VM):**  
  The input voltage (**Vin**) at which the output voltage (**Vout**) equals the input voltage.  
  - It is the intersection point on the Voltage Transfer Curve (VTC).  
  - Also referred to as the **midpoint voltage** of the CMOS inverter.

  ### Sky130 SPICE simulation for CMOS - Transient Analysis
      *Model Description
       .param temp=27

      *Including sky130 library files
        .lib "sky130_fd_pr/models/sky130.lib.spice" tt

        *Netlist Description
         XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=0.84 l=0.15
         XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15
         Cload out 0 50fF
         Vdd vdd 0 1.8V
         Vin in 0 PULSE(0V 1.8V 0 0.1ns 0.1ns 2ns 4ns)

         *simulation commands
         .tran 1n 10n
         .control
          run
          .endc
          .end
  
  ![WhatsApp Image 2024-12-12 at 10 59 17 PM](https://github.com/user-attachments/assets/bad784a5-848a-4190-a74f-bd70ce13cf5d)
  ![WhatsApp Image 2024-12-12 at 10 59 18 PM](https://github.com/user-attachments/assets/7a95401c-8491-4a4d-ac4f-b3cc1dc7ebc5)
- **Propagation Delay:**  
  The time difference (measured at 50% of input-output transition) between the input signal change and the corresponding output signal switch in a logic gate (e.g., inverter).
