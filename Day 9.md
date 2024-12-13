# SPICE SIMULATION FOR LOWER NODES AND VELOCITY SATURATION EFFECT
#### SPICE simulation for lower nodes
![Screenshot 2024-12-12 222449](https://github.com/user-attachments/assets/4afe1119-b9e8-4720-b119-5c748c15b79b)
![Screenshot 2024-12-12 222501](https://github.com/user-attachments/assets/a4e1f3e7-0744-4aea-b9a0-555725f4458b)
![Screenshot 2024-12-12 222512](https://github.com/user-attachments/assets/51dcfc4e-1bf6-432a-8c92-62b25bf697ac)

For **long-channel devices**, drain current shows a **quadratic dependence** on gate voltage.  
For **short-channel devices**, it is **quadratic at low gate voltage** but becomes **linear at higher voltages** due to **velocity saturation**.
![Screenshot 2024-12-12 222526](https://github.com/user-attachments/assets/74266571-2ac3-49bf-94ed-65dbaa1d78d8)

At **lower electric fields**, carrier velocity increases **linearly** with the electric field.  
At **higher electric fields**, velocity **saturates** and becomes **constant** due to **velocity saturation**.

![Screenshot 2024-12-12 222535](https://github.com/user-attachments/assets/a7698c98-1ce7-4774-99bb-172579c32628)
![Screenshot 2024-12-12 222550](https://github.com/user-attachments/assets/4ad308b3-d1fb-4640-8cfe-e00f4d6ce50f)
![Screenshot 2024-12-12 222603](https://github.com/user-attachments/assets/fe03377d-a55c-469a-ace2-ae1071f7cc33)

**Velocity Saturation Drain Current Model:**  
- **Technology Parameter:** Saturation voltage (**Vdsat**) – the voltage at which carrier velocity saturates, independent of **Vgs** or **Vds**.  
- **Vgt** is minimum → FET is in **saturation region** (both long and short channel).  
- **Vds** is minimum → FET is in **linear region** (both long and short channel).  
- **Vdsat** is minimum → FET velocity **saturates** (**only for short channel**).
  ![Screenshot 2024-12-12 222619](https://github.com/user-attachments/assets/6c3e7777-717b-4dab-8872-098222275cdd)
  ![Screenshot 2024-12-12 222631](https://github.com/user-attachments/assets/25850f89-e319-440d-b104-d3b2968373f8)
  #### OBSERVATIONS:
  **Observation 1:** For short-channel devices, at **higher electric fields**, the device enters **velocity saturation**, causing **Ids to remain constant** as **Vds increases**. Here, **Ids** becomes a **linear function of Vgs**, unlike the **quadratic dependence** in long-channel devices.  

**Observation 2:** **Velocity saturation** causes the device to **saturate earlier**.
## **CMOS Voltage Transfer Characteristics (VTC):**  
1. Vout is **high** when Vin is low, and Vout is **low** when Vin is high.  
2. The **transition region** shows a steep drop where both NMOS and PMOS conduct, defining the switching threshold.
#### MOSFET as a switch
![Screenshot 2024-12-12 222716](https://github.com/user-attachments/assets/481b40d8-dec1-4e3f-bed2-6a422cb87758)
![Screenshot 2024-12-12 222727](https://github.com/user-attachments/assets/e14b5a54-ab76-450a-8cbb-32bd5c414175)
![Screenshot 2024-12-12 222740](https://github.com/user-attachments/assets/c3684f36-747e-405c-a4e0-e2f169640849)
**Introduction to Standard MOS Voltage-Current Parameters:**  
In MOS devices, **Rp** (PMOS) and **Rn** (NMOS) act as **non-linear resistors**, where their resistance is a **function of drain current (Ids)**, influenced by gate voltage (Vgs) and drain voltage (Vds).
![Screenshot 2024-12-12 222754](https://github.com/user-attachments/assets/a0b8534a-4b3e-41d2-bfe1-30d8041b68e8)
**PMOS/NMOS Drain Current vs. Drain Voltage:**

1. **Linear Region (Vds < Vdsat):**  
   - Drain current (**Ids**) increases **linearly** with **Vds**.  
   - Device behaves like a **resistor** controlled by Vgs.  

2. **Saturation Region (Vds ≥ Vdsat):**  
   - Drain current (**Ids**) becomes **constant** and independent of Vds.  
   - For **NMOS**, Ids depends on **Vgs - Vth**.  
   - For **PMOS**, Ids depends on **Vth - Vgs**.  
![Screenshot 2024-12-12 222804](https://github.com/user-attachments/assets/26460459-1b5d-4545-9934-96ec82fdec7f)
 #### Step1. Convert **PMOS gate-source voltage** to **Vin**.  
 Replace internal node voltages with **Vin**, **Vdd**, **Vss**, and **Vout**.  
 Simulate and plot the **VTC** by varying **Vin** and analyzing **Vout**.
![Screenshot 2024-12-12 222823](https://github.com/user-attachments/assets/23b04673-d61d-41ea-b347-926069e10347)
**Step 2 & Step 3:**  
- Convert **PMOS** and **NMOS drain-source voltages** to **Vout**.  
- Relate the drain-source voltages of both devices to the output voltage (**Vout**) by considering their respective operating regions (linear or saturation).
![Screenshot 2024-12-12 222833](https://github.com/user-attachments/assets/90e46877-1003-4bd5-8dea-0bed5e81c6a1)
![Screenshot 2024-12-12 222841](https://github.com/user-attachments/assets/fd1929e1-ffd4-45b6-a2f6-1d15750467cc)
**Step 4:**  
- **Merge the PMOS and NMOS load curves** by combining their drain current (Ids) characteristics with respect to **Vout**.  
- **Plot the Voltage Transfer Characteristic (VTC)** by mapping **Vout** against **Vin**, showing the transition from low to high output voltage.
![Screenshot 2024-12-12 222852](https://github.com/user-attachments/assets/7125ef9e-5f05-4ba2-9b58-7cf8269e41df)

# LABS
## SPICE simulation for lower nodes and velocity saturation effect
#### Sky130 Id-Vgs
##### EXAMPLE 1
      *Model Description
      .param temp=27

      *Including sky130 library files
      .lib "sky130_fd_pr/models/sky130.lib.spice" tt

      *Netlist Description
       XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15
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

#### The plot of Ids vs Vds over constant Vgs:
![WhatsApp Image 2024-12-12 at 6 12 00 AM (2)](https://github.com/user-attachments/assets/6bb17e94-6efa-45e4-8f55-7e4bb8f7fe51)
![WhatsApp Image 2024-12-12 at 6 12 01 AM](https://github.com/user-attachments/assets/f873345a-9f1f-4848-8f94-cd86d104554b)

##### EXAMPLE 2
      *Model Description
       .param temp=27

       *Including sky130 library files
       .lib "sky130_fd_pr/models/sky130.lib.spice" tt

       *Netlist Description
        XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15
        R1 n1 in 55
        Vdd vdd 0 1.8V
        Vin in 0 1.8V

        *simulation commands
         .op
        .dc Vin 0 1.8 0.1 

        .control

         run
         display
         setplot dc1
         .endc
         .end
####  The plot of Ids vs Vgs over constant Vds:
![WhatsApp Image 2024-12-12 at 6 12 00 AM (1)](https://github.com/user-attachments/assets/7fdd6cf7-680e-4ac3-a27f-0afe30c417a8)
![WhatsApp Image 2024-12-12 at 6 12 00 AM](https://github.com/user-attachments/assets/a6789ed4-1278-4d7e-8b7c-810556929139)



