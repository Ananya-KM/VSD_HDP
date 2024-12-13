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
**Static Behavior Evaluation: CMOS Inverter Robustness and Switching Threshold (Vm)**  
The **switching threshold (Vm)** is the point where **Vin = Vout**, and both transistors are in saturation (since **Vds = Vgs**). At **Vm**, maximum power is drawn due to large current, and it can be graphically found at the intersection of the **VTC** with the **Vin = Vout** line. The analytical expression for **Vm** is obtained by equating the drain currents of PMOS and NMOS (**IDSn = IDSp**).
