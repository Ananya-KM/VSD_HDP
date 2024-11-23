# Installation of OpenSTA
OpenSTA (Open Static Timing Analyzer) is a versatile tool used for timing analysis in digital circuits. To install OpenSTA, ensure your system is set up with the necessary build tools like GCC, Make, and Tcl/Tk development libraries. The installation process typically involves cloning the OpenSTA GitHub repository, building the source code, and adding the compiled binary to your system's PATH for easy access.

##### the OpenSTA tool is installed

![WhatsApp Image 2024-11-23 at 6 37 18 AM](https://github.com/user-attachments/assets/59f707ee-8163-41cd-8724-bb6188d39d3a)

## PVT Corner Analysis 
##### The STA checks are performed over across all the corners to confirm the design meets the target timing requirements.
and in that

###### The worst max path (Setup-critical) corners in the sub-40nm process nodes are usually: ss_LowTemp_LowVolt, ss_HighTemp_LowVolt (Slowest corners)
###### The worst min path (Hold-critical) corners being: ff_LowTemp_HighVolt,ff_HighTemp_HighVolt (Fastest corners)

![WhatsApp Image 2024-11-23 at 6 37 17 AM (1)](https://github.com/user-attachments/assets/f1300469-befa-4a39-8a74-4b986583887e)

</p> error occured while running the  sta_across_pvt.tcl file , shows that the riscv_pipelined_final_netlist.v file is missing </p>
