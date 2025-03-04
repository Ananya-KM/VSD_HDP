# **Post-Placement STA and Timing Graphs with OpenSTA**

The **SPEF file** generated contains the parasitic details like resistance and capacitance extracted after routing, and the **post-placement Verilog file** represents the design netlist post-placement and routing. I used these files in **OpenSTA** to perform static timing analysis, check timing constraints, and identify critical paths. This helped ensure that the design meets setup and hold requirements, making it ready for fabrication.

 The following TCL script can be executed to perform  post placement STA for the available PVT corners using the Sky130 timing libraries.
 #### The TCL file is
     export DESIGN_NICKNAME = vsdbabysoc
     export DESIGN_NAME = vsdbabysoc
     export PLATFORM    = sky130hd

     # export VERILOG_FILES_BLACKBOX = $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/IPs/*.v
     # export VERILOG_FILES = $(sort $(wildcard $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/*.v))
     # Explicitly list the Verilog files for synthesis
      export VERILOG_FILES = $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/vsdbabysoc.v \
                             $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/rvmyth.v \
                             $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/clk_gate.v

     export SDC_FILE      = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)/vsdbabysoc_synthesis.sdc

     export vsdbabysoc_DIR = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)

     export VERILOG_INCLUDE_DIRS = $(wildcard $(vsdbabysoc_DIR)/include/)
     # export SDC_FILE      = $(wildcard $(vsdbabysoc_DIR)/sdc/*.sdc)
     export ADDITIONAL_GDS  = $(wildcard $(vsdbabysoc_DIR)/gds/*.gds.gz)
     export ADDITIONAL_LEFS  = $(wildcard $(vsdbabysoc_DIR)/lef/*.lef)
     #export ADDITIONAL_LIBS = $(wildcard $(vsdbabysoc_DIR)/lib/*.lib)
     # export PDN_TCL = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)/pdn.tcl

    # Clock Configuration (vsdbabysoc specific)
    # export CLOCK_PERIOD = 20.0
      export CLOCK_PORT = CLK
      export CLOCK_NET = $(CLOCK_PORT)

    # Floorplanning Configuration (vsdbabysoc specific)
      export FP_PIN_ORDER_CFG = $(wildcard $(DESIGN_DIR)/pin_order.cfg)
    # export FP_SIZING = absolute

     export DIE_AREA   = 0 0 1600 1600
     export CORE_AREA  = 20 20 1590 1590

     # Placement Configuration (vsdbabysoc specific)
     export MACRO_PLACEMENT_CFG = $(wildcard $(DESIGN_DIR)/macro.cfg)
     export PLACE_PINS_ARGS = -exclude left:0-600 -exclude left:1000-1600: -exclude right:* -exclude top:* -exclude bottom:*
     # export MACRO_PLACEMENT = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)/macro_placement.cfg

     export TNS_END_PERCENT = 100
     export REMOVE_ABC_BUFFERS = 1

     # Magic Tool Configuration
     export MAGIC_ZEROIZE_ORIGIN = 0
     export MAGIC_EXT_USE_GDS = 1

     # CTS tuning
     export CTS_BUF_DISTANCE = 600
     export SKIP_GATE_CLONING = 1

     # export CORE_UTILIZATION=0.1  # Reduce this value to allow more whitespace for routing.
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
