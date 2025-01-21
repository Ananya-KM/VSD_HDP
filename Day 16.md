# **Post-Placement STA and Timing Graphs with OpenSTA**

The **SPEF file** generated contains the parasitic details like resistance and capacitance extracted after routing, and the **post-placement Verilog file** represents the design netlist post-placement and routing. I used these files in **OpenSTA** to perform static timing analysis, check timing constraints, and identify critical paths. This helped ensure that the design meets setup and hold requirements, making it ready for fabrication.

 The following TCL script can be executed to perform  post placement STA for the available PVT corners using the Sky130 timing libraries.
 #### The TCL file is
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
      read_verilog /OpenSTA/examples/BabySOC/vsdbabysoc_post_place.v
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
|  tt_025C_1v80    |5.5352   | 0.3112    | 0   | 0    |
|  ff_100C_1v65     |6.6856  | 0.2499   | 0    | 0    |
|  ff_100C_1v95    |7.6140    | 0.1970    | 0    | 0    |
|  ff_n40C_1v56   |5.3046  | 0.2930   | 0    | 0    |
|  ff_n40C_1v65     |6.0904    | 0.2566   | 0   | 0    |
|  ff_n40C_1v76  |6.7773  | 0.2251   | 0   | 0    |
|  ss_100C_1v40    |-4.1967   | 0.8871    | -4.1967  | -924.7471  |
|  ss_100C_1v60     |0.6172   | 0.6283  | 0.0000 | 0.0000    |
|  ss_n40C_1v28    |-32.8997  | 1.7757   | -32.8997   | -15373.5605   |
|  ss_n40C_1v35   |-18.9134  | 1.3061  | -18.9134   | -7077.3320   |
|  ss_n40C_1v40|-12.9723  | 1.0941  | -12.9723   | -4009.4502   |
|  ss_n40C_1v44  |-9.6203  | 0.9624   | -9.6203 | -2727.8179  |
|  ss_n40C_1v76     |1.8175   | 0.4882   | 0.0000   | 0.0000   |

![Screenshot 2025-01-21 055201](https://github.com/user-attachments/assets/4c8d93ac-f8d6-411f-a010-46c557b05ffc)
![Screenshot 2025-01-21 060056](https://github.com/user-attachments/assets/32e81b9c-adcf-4ec8-99a5-dc51f3ab7790)
![Screenshot 2025-01-21 060503](https://github.com/user-attachments/assets/a68baf60-70d5-4d20-952a-dd15abdb251c)
![Screenshot 2025-01-21 060954](https://github.com/user-attachments/assets/715f59d6-b8d3-426f-860b-ca79d3838e02)
