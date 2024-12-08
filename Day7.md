# Installation of OpenSTA
OpenSTA (Open Static Timing Analyzer) is a versatile tool used for timing analysis in digital circuits. To install OpenSTA, ensure your system is set up with the necessary build tools like GCC, Make, and Tcl/Tk development libraries. The installation process typically involves cloning the OpenSTA GitHub repository, building the source code, and adding the compiled binary to your system's PATH for easy access.

##### the OpenSTA tool is installed

![WhatsApp Image 2024-12-07 at 9 37 03 AM](https://github.com/user-attachments/assets/0f73dcfd-0ca8-49e6-ac4e-e57335d79c7d)


## Static timing analysis using OpenSTA
#### Timing Ananlysis Using In line Commands
    
       read_liberty /OpenSTA/examples/nangate45_slow.lib.gz
       read_verilog /OpenSTA/examples/example1.v
       link_design top
       create_clock -name clk -period 10 {clk1 clk2 clk3}
       set_input_delay -clock clk 0 {in1 in2}
       report_checks

![WhatsApp Image 2024-12-07 at 9 14 09 AM](https://github.com/user-attachments/assets/5c3805ca-2199-4b09-bfaa-c47d0806c5a3)
![WhatsApp Image 2024-12-07 at 9 14 09 AM (1)](https://github.com/user-attachments/assets/51d631ae-20e7-43b3-b4bd-d1ed37d60998)

#### Timing Analysis using TCL file
    read_liberty-min sky130_fd sc hd tt 025C 1v80.lib
    read liberty max sky130 fd sc hd tt 025C 1v80.lib
    read_liberty-min avsdpll.lib
    read liberty -max avsdpll.lib
    read_liberty min avsddac.lib
    read_liberty -max avsddąc.lib
    read verilog vsdbabysoc.synth.v
    link design vsdbabysoc
    read_sdc vsdbabysoc_synthesis.sdc
    report checks
    
    
![WhatsApp Image 2024-12-07 at 9 14 08 AM (1)](https://github.com/user-attachments/assets/12dd9c03-5fbc-4a7a-aced-2942d80321d7)
![WhatsApp Image 2024-12-07 at 9 14 08 AM (2)](https://github.com/user-attachments/assets/b6183d55-418e-4ef5-96d3-cba7c43b676c)
![WhatsApp Image 2024-12-07 at 9 14 08 AM](https://github.com/user-attachments/assets/84818f23-16f1-4fde-99ee-1980ceca70e0)



#### VSDBabySoC basic timing analysis
     read_liberty -min /OpenSTA/examples/timing_libs/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_liberty -max /OpenSTA/examples/timing_libs/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_liberty -min /OpenSTA/examples/timing_libs/avsdpll.lib
     read_liberty -max /OpenSTA/examples/timing_libs/avsdpll.lib
     read_liberty -min /OpenSTA/examples/timing_libs/avsddac.lib
     read_liberty -max /OpenSTA/examples/timing_libs/avsddac.lib
     read_verilog /OpenSTA/examples/BabySOC/vsdbabysoc.synth.v
     link_design vsdbabysoc
     read_sdc /OpenSTA/examples/BabySOC/vsdbabysoc_synthesis.sdc
     report_checks

     
![WhatsApp Image 2024-12-07 at 9 14 08 AM (4)](https://github.com/user-attachments/assets/d67e5fd1-99a8-47b5-a8f4-cf6063e07bd5)
![WhatsApp Image 2024-12-07 at 9 14 07 AM](https://github.com/user-attachments/assets/c8652c4e-392d-4881-a97e-288e81c679b2)

     
### **VSDBabySoC PVT Corner Analysis (Post-Synthesis Timing)**  
STA is performed across all PVT corners to validate that the design meets timing requirements.

The worst max path (Setup-critical) corners in sub-40nm nodes are generally:  
- **ss_LowTemp_LowVolt**  
- **ss_HighTemp_LowVolt** *(Slowest corners)*  

The worst min path (Hold-critical) corners are:  
- **ff_LowTemp_HighVolt**  
- **ff_HighTemp_HighVolt** *(Fastest corners)*  

The following TCL script can be executed to perform STA for the available PVT corners using the Sky130 timing libraries.  
The timing libraries can be downloaded from:  
[https://github.com/efabless/skywater-pdk-libs-sky130_fd_sc_hd/tree/master/timing](https://github.com/efabless/skywater-pdk-libs-sky130_fd_sc_hd/tree/master/timing)  

#### the TCL file is 
     set list_of_lib_files(1) "sky130_fd_sc_hd__tt_025C_1v80.lib"
     set list_of_lib_files(2) "sky130_fd_sc_hd__ff_100C_1v65.lib"
     set list_of_lib_files(3) "sky130_fd_sc_hd__ff_100C_1v95.lib"
     set list_of_lib_files(4) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
     set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
     set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
     set list_of_lib_files(7) "sky130_fd_sc_hd__ss_100C_1v40.lib"
     set list_of_lib_files(8) "sky130_fd_sc_hd__ss_100C_1v60.lib"
     set list_of_lib_files(9) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
     set list_of_lib_files(10) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
     set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
     set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
     set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v76.lib"

     read_liberty /OpenSTA/examples/timing_libs/avsdpll.lib
     read_liberty /OpenSTA/examples/timing_libs/avsddac.lib

     for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
     read_liberty /OpenSTA/examples/timing_libs/$list_of_lib_files($i)
     read_verilog /OpenSTA/examples/BabySOC/vsdbabysoc.synth.v
     link_design vsdbabysoc
     current_design
     read_sdc /OpenSTA/examples/BabySOC/vsdbabysoc_synthesis.sdc
     check_setup -verbose
     report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > 
     /OpenSTA/examples/BabySOC/STA_OUPUT/min_max_$list_of_lib_files($i).txt

     exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_max_slack.txt
     report_worst_slack -max -digits {4} >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_max_slack.txt

     exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_min_slack.txt
     report_worst_slack -min -digits {4} >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_min_slack.txt

     exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_tns.txt
     report_tns -digits {4} >> /OpenSTA/examples/BabySoO/STA_OUPUT/sta_tns.txt

     exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_wns.txt
     report_wns -digits {4} >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_wns.txt
     }
     
| PVT_CORNER    | Worst Setup Slack    | Worst Hold Slack    | WNS    | TNS   |
|-------------|-------------|-------------|-------------|-------------|
|  tt_025C_1v80    |2.2603   | 0.3096    | 0   | 0    |
|  ff_100C_1v65     |4.1853   | 0.2491    | 0    | 0    |
|  ff_100C_1v95    |5.5202    | 0.1960    | 0    | 0    |
|  ff_n40C_1v56   |1.8047   | 0.2915   | 0    | 0    |
|  ff_n40C_1v65     |3.1788    | 0.2551   | 0   | 0    |
|  ff_n40C_1v76  |4.2413  | 0.2243    | 0   | 0    |
|  ss_100C_1v40    |-11.2888   | 0.9053    | -11.2888  | -9245.0244   |
|  ss_100C_1v60     |-4.8042   | 0.6420   | -4.8042  | -3378.2246    |
|  ss_n40C_1v28    |-55.7561   | 1.8296    | -55.7561    | -46170.3242   |
|  ss_n40C_1v35   |-35.1855  | 1.3475   | -35.1855   | -28713.4316   |
|  ss_n40C_1v40|-27.0853  | 1.1249  | -27.0853   | -21725.4824   |
|  ss_n40C_1v44  |-22.7070  | 0.9909   | -22.7070  | -17801.5625  |
|  ss_n40C_1v76     |-5.2654   | 0.5038   | -5.2654   | -3208.7793   |

![Screenshot 2024-12-08 064226](https://github.com/user-attachments/assets/c2735063-c6c8-4a51-8f6a-2d17818fa2e5)

![Screenshot 2024-12-08 065041](https://github.com/user-attachments/assets/769c8079-dfea-422e-8cc7-8e6240420b1b)

![Screenshot 2024-12-08 065913](https://github.com/user-attachments/assets/fc904026-5a3c-4bca-8e41-1624474f4852)

![Screenshot 2024-12-08 070712](https://github.com/user-attachments/assets/6daea128-878b-4286-96ab-08ea7bdd3b83)
