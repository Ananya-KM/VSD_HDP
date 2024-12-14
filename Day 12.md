# **1. Static Behavior Evaluation: CMOS Inverter Robustness - Power Supply Variation**

**Overview:**  
- Power supply scaling affects the static behavior of the CMOS inverter, including the switching threshold, noise margins, and overall robustness.  

**Smart SPICE Simulation:**  
- Simulate the CMOS inverter across different supply voltage values (VDD).  
- Analyze how the voltage transfer characteristics (VTC) and critical parameters (like VM and noise margins) shift with varying power supply.  

**Key Observations:**  
1. As **VDD decreases**, the switching threshold (VM) may shift closer to the center of the supply range, but noise margins reduce.  
2. Lower power supply reduces overall noise immunity and can impact performance.  
3. At higher VDD, both static power dissipation and noise margins increase.  
![Screenshot 2024-12-14 064110](https://github.com/user-attachments/assets/0881a71d-23ca-4788-acd3-022200051cd4)
![Screenshot 2024-12-14 064121](https://github.com/user-attachments/assets/1b095533-5d5d-4847-8d9c-4284c23f816d)
### **Simulation Observations: Power Supply Variations**

1. **Robust Operation at Lower VDD:**  
   - The CMOS inverter operates effectively even at 0.8V, which is below half the original supply voltage (1.8V) and close to the transistor threshold voltages.

2. **Switching Threshold Proportionality:**  
   - With a fixed transistor ratio (*r*), the switching threshold (VM) is approximately proportional to VDD.

3. **Gain in Transition Region:**  
   - The inverter gain in the transition region increases as the supply voltage decreases.

4. **Transition Region Width:**  
   - The width of the transition region reduces when the supply voltage is scaled down from the original VDD.
   ![Screenshot 2024-12-14 064131](https://github.com/user-attachments/assets/d6867666-b993-4fcc-80c3-b68bf2e70c33)
   ![Screenshot 2024-12-14 064143](https://github.com/user-attachments/assets/63977762-4d62-41ac-bbe9-f5d596c9e75d)
### **Limitations of Operating at Low Supply Voltages**

1. **Performance Degradation:**  
   - Lowering the supply voltage reduces energy dissipation but significantly increases gate transition times, negatively affecting performance.

2. **Parameter Sensitivity:**  
   - At low supply voltages, the DC characteristics become highly sensitive to variations in device parameters, such as transistor threshold voltages.

3. **Reduced Signal Swing:**  
   - Scaling VDD reduces signal swing, lowering internal noise (e.g., crosstalk) but increasing sensitivity to external noise sources, which do not scale proportionally.
![Screenshot 2024-12-14 064154](https://github.com/user-attachments/assets/43789076-775b-4629-901c-22ff3cbd6891)
### **CMOS Inverter Robustness to Device Variations**

1. **Design vs. Real Operating Conditions:**  
   - Gates are designed for nominal conditions, but actual operating temperatures and device parameters can vary widely after fabrication.

2. **DC Characteristics Stability:**  
   - The DC characteristics of the CMOS inverter are relatively insensitive to variations in device parameters, allowing the gate to remain functional across a broad range of operating conditions.

3. **Sources of Variation:**  
   - One common source of variation is the etching process during fabrication, which can affect device parameters.
   ### SOURCES OF ETCHING PROCESS
![Screenshot 2024-12-14 064237](https://github.com/user-attachments/assets/37536703-156f-447e-a54b-a8f780b7eec3)
![Screenshot 2024-12-14 064244](https://github.com/user-attachments/assets/6957d230-95ea-49e9-8aa6-7e0997b9169c)
![Screenshot 2024-12-14 064256](https://github.com/user-attachments/assets/26d74cde-84b3-448d-ad3b-17614a6cdd4c)
![Screenshot 2024-12-14 064307](https://github.com/user-attachments/assets/acefb5ff-0705-4f5f-a95c-071aa3e27857)
### Sources of variation: Oxide Thickness
![Screenshot 2024-12-14 064317](https://github.com/user-attachments/assets/011ff2a9-1203-4501-a5ca-5c8d8f68d536)
![Screenshot 2024-12-14 064325](https://github.com/user-attachments/assets/f78cebab-3c33-45d5-af1f-7b3d1d6276b1)
# LABS
## Static behavior evaluation: CMOS inverter robustness, Power supply variation
### Smart SPICE simulation for power supply variations

![WhatsApp Image 2024-12-14 at 5 54 28 AM (1)](https://github.com/user-attachments/assets/6e264a52-15c6-4a99-a603-692e9b51b689)
![WhatsApp Image 2024-12-14 at 5 54 28 AM](https://github.com/user-attachments/assets/6d89ba5d-aa04-42e6-b895-c2253399447c)


### **CMOS Inverter Robustness: Extreme Device Width Variation**

- **Robustness to Width Variation:**  
   The CMOS inverter remains functional even under extreme variations in device width (W) due to its static behavior properties.  

- **Effect on Switching Threshold:**  
   Large deviations in device width primarily affect the switching threshold \( V_M \) but do not drastically impact the inverter's ability to operate as a logic gate.  

- **Impact on Noise Margins:**  
   Variations in width cause asymmetry in the noise margins, with one margin (high or low) reducing while the other increases.

- **Key Insight:**  
   The CMOS inverter exhibits robust static behavior, tolerating extreme width variations without functional failure.

![Screenshot 2024-12-14 064110](https://github.com/user-attachments/assets/2ff1be23-c941-4053-bac2-caa191f08308)
![WhatsApp Image 2024-12-14 at 5 54 29 AM](https://github.com/user-attachments/assets/ebc534a4-d0fc-42c4-916f-bc564a118478)
![WhatsApp Image 2024-12-14 at 5 54 29 AM (1)](https://github.com/user-attachments/assets/eb560b25-1bbc-4e88-b2f7-d3af78af9d54)
