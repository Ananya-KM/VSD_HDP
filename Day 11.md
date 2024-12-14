# **Static Behavior Evaluation: CMOS Inverter Robustness and Noise Margin**

- **Introduction to Noise Margin:**  
  - Noise margin is the maximum noise voltage a CMOS circuit can tolerate without logic errors.  
  - If noise amplitude is below the noise margin, it is attenuated through the logic gate, ensuring error-free signal transmission.  

- **Function of Noise Margin:**  
  - Ensures signals with small noise added to **logic 1** remain as logic 1 and those with noise on **logic 0** remain as logic 0.  

- **Application:**  
  - Consider two back-to-back CMOS inverters.  
  - The voltage transfer curve (VTC) determines noise margins:  
    - **Ideal VTC**, **Piece-wise Linear VTC**, and **Realistic VTC** depict inverter robustness.  
![noise margin](https://github.com/user-attachments/assets/a33b8aeb-ae0d-43d9-ae48-7def565b38a7)
### **Noise Margin: VIL and VIH Points**

- **Definition:**  
  - **VIL** and **VIH** are operational points where the slope of the voltage transfer curve (VTC) is **-1**.  
  - These points correspond to the gain of the inverter being equal to **-1**.  

- **Logic Recognition:**  
  - Input voltage **0 to VIL** → Recognized as **Logic 0**.  
  - Input voltage **VIH to VDD** → Recognized as **Logic 1**.
   ### **Noise Margins in CMOS Logic Gates**

1. **Conditions for Proper Operation:**  
   - The following conditions must hold for a logic gate to function correctly in the presence of noise:  
     ```
     VOL_MAX < VIL_MAX  
     VOH_MIN > VIH_MIN  
     ```  

2. **Behavior in Different Input Ranges:**  
   - **For Vin ≤ VIL**:  
     The inverter gain magnitude is less than unity, resulting in minimal output change for a given input change.  
   - **For Vin ≥ VIH**:  
     The gain magnitude is also less than unity, leading to minimal output change.  
   - **For VIL < Vin < VIH**:  
     The gain magnitude exceeds unity, causing significant output changes. This range is called the **undefined region** because noise signals pushing Vin into this range may introduce errors.  

3. **Noise Margin Equations:**  
   - **Low-Level Noise Margin (NML):**  
     ```
     NML = VIL_MAX - VOL_MAX  
     ```  
   - **High-Level Noise Margin (NMH):**  
     ```
     NMH = VOH_MIN - VIH_MIN  
     ```  
   - **Overall Noise Margin (NM):**  
     ```
     NM = Min(NML, NMH)  
     ```  

These noise margins define the tolerance of a circuit to noise without compromising its logical operation.

![Screenshot 2024-12-14 060014](https://github.com/user-attachments/assets/c000fdd5-613a-4435-a50e-697833e020a4)
![Screenshot 2024-12-14 060023](https://github.com/user-attachments/assets/69f1635b-f6bc-428a-877b-3e92cbf11983)
![Screenshot 2024-12-14 060208](https://github.com/user-attachments/assets/ae231e3a-e15e-49b4-b89f-2d50b83efc30)
![Screenshot 2024-12-14 060218](https://github.com/user-attachments/assets/dfebc541-b16c-42b3-9528-5eb521356c7a)
#### Noise Margin Robustness against variations in Device Ratio
![Screenshot 2024-12-14 060229](https://github.com/user-attachments/assets/640897da-ade6-4ecf-a3fd-cf4d7bfceb05)
# LABS
##  Static behavior evaluation: CMOS inverter robustness, Noise margin
##### Noise Margin - sky130 Inverter (Wp/Lp=1u/0.15u, Wn/Ln=0.36u/0.15u)

 ![WhatsApp Image 2024-12-14 at 5 54 27 AM](https://github.com/user-attachments/assets/43ebdaa6-fb03-4f5a-94cd-b2dd3a9c82d3)
 ![WhatsApp Image 2024-12-14 at 5 54 27 AM (1)](https://github.com/user-attachments/assets/293edd46-ef9c-4e2c-afb9-edabb73ad6e7)
