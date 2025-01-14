# Floorplan to Routing of VSDBabySoC
### Structure of OpenROAD-flow-scripts 
    ├── OpenROAD-flow-scripts             
    │   ├── docker           
    │   ├── docs               
    │   ├── flow               
    |   ├── jenkins          
    │   ├── tools           
    │   ├── etc              
    │   ├── setup.sh    
    
![WhatsApp Image 2024-12-21 at 10 16 03 AM](https://github.com/user-attachments/assets/c260f6c1-5f97-4f07-919e-ca32e007d032)


 ### Now go to flow directory
     ├── flow           
     │   ├── designs         
     │   ├── makefile       
     │   ├── platforms         
     |   ├── tutorials        
     │   ├── util            
     │   ├── scripts    
     
![WhatsApp Image 2024-12-21 at 10 16 03 AM (1)](https://github.com/user-attachments/assets/f8c28755-2d84-4a1e-9e5c-f5679dd2485d)

  ###  RTL2GDS Flow for VSDBabySoC: Initial Steps 

1. **Create Directories:**
   - Inside `OpenROAD-flow-scripts/flow/designs/sky130hd/`, create a folder named `vsdbabysoc`.
   - Create another folder named `vsdbabysoc` in `OpenROAD-flow-scripts/flow/designs/src/` and place all Verilog files here.

2. **Copy Folders:**
   - From your `VSDBabySoC` folder, copy the following folders into `sky130hd/vsdbabysoc`:
     - **gds:** Contains `avsddac.gds`, `avsdpll.gds`.
     - **include:** Contains `sandpiper.vh`, `sandpiper_gen.vh`, `sp_default.vh`, `sp_verilog.vh`.
     - **lef:** Contains `avsddac.lef`, `avsdpll.lef`.
     - **lib:** Contains `avsddac.lib`, `avsdpll.lib`.

3. **Copy Constraint and Configuration Files:**
   - Copy `vsdbabysoc_synthesis.sdc` into `sky130hd/vsdbabysoc`.
   - Copy `macro.cfg` and `pin_order.cfg` into `sky130hd/vsdbabysoc`.

4. **Create Config File:**
   - Create a `config.mk` file in `sky130hd/vsdbabysoc` with the required configuration details. 
   ##### the file details are given below
   
         # Design and Platform Configuration
          export DESIGN_NICKNAME = vsdbabysoc
          export DESIGN_NAME = vsdbabysoc
          export PLATFORM    = sky130hd

         # Design Paths
         export vsdbabysoc_DIR = /home/ananya123/OpenROAD-flow-scripts/flow/designs/sky130hd/$(DESIGN_NICKNAME)

         # Explicitly list Verilog files for synthesis
          export VERILOG_FILES = /home/ananya123/OpenROAD-flow-scripts/flow/designs/src/vsdbabysoc/vsdbabysoc.v \
                                /home/ananya123/OpenROAD-flow-scripts/flow/designs/src/vsdbabysoc/rvmyth.v \
                                /home/ananya123/OpenROAD-flow-scripts/flow/designs/src/vsdbabysoc/clk_gate.v


         # Include Directory for Verilog Header Files
          export VERILOG_INCLUDE_DIRS = $(vsdbabysoc_DIR)/include

         # Constraints File
           export SDC_FILE = $(vsdbabysoc_DIR)/vsdbabysoc_synthesis.sdc

         # Additional GDS Files
           export ADDITIONAL_GDS = $(vsdbabysoc_DIR)/gds/avsddac.gds \
                                   $(vsdbabysoc_DIR)/gds/avsdpll.gds

         # Additional LEF Files
          export ADDITIONAL_LEFS = $(vsdbabysoc_DIR)/lef/avsddac.lef \
                                   $(vsdbabysoc_DIR)/lef/avsdpll.lef

         # Additional LIB Files
          export ADDITIONAL_LIBS = $(vsdbabysoc_DIR)/lib/avsddac.lib \
                                   $(vsdbabysoc_DIR)/lib/avsdpll.lib

        # Pin Order and Macro Placement Configurations
          export FP_PIN_ORDER_CFG = $(vsdbabysoc_DIR)/pin_order.cfg
          export MACRO_PLACEMENT_CFG = $(vsdbabysoc_DIR)/macro.cfg

        # Clock Configuration
          export CLOCK_PORT = CLK
          export CLOCK_NET  = $(CLOCK_PORT)
          export CLOCK_PERIOD = 20.0

       # Floorplanning Configuration
         export DIE_AREA   = 0 0 1600 1600
         export CORE_AREA  = 20 20 1590 1590

       # Placement Configuration
         export PLACE_PINS_ARGS = -exclude left:0-600 -exclude left:1000-1600 -exclude right:* -exclude top:* -exclude bottom:*

       # Tuning for Timing and Buffers
         export TNS_END_PERCENT     = 100
         export REMOVE_ABC_BUFFERS  = 1
         export CTS_BUF_DISTANCE    = 600
         export SKIP_GATE_CLONING   = 1

        # Magic Tool Configuration
          export MAGIC_ZEROIZE_ORIGIN = 0
          export MAGIC_EXT_USE_GDS    = 1
   #### Now go to terminal and run the following commands:
        cd OpenROAD-flow-scripts
        source env.sh
        cd flow
   #### Commands for synthesis:
         make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk synth
   
 ![WhatsApp Image 2024-12-21 at 10 15 59 AM](https://github.com/user-attachments/assets/ac0c1ca4-43ba-4c0f-b274-a9e2990174ad)
 ![WhatsApp Image 2024-12-21 at 10 15 59 AM (3)](https://github.com/user-attachments/assets/6a965abf-99fa-41d2-9df4-271f6682a3c7)

   #### Synthesis netlist
![WhatsApp Image 2024-12-21 at 10 19 26 PM](https://github.com/user-attachments/assets/9858668a-4b9e-469e-a44d-3e6a0ad90d94)

   #### Synthesis log:
![WhatsApp Image 2024-12-21 at 10 15 59 AM (4)](https://github.com/user-attachments/assets/dace679d-b01d-4b8c-a82d-182ef230f5cc)
![WhatsApp Image 2024-12-21 at 10 15 59 AM (1)](https://github.com/user-attachments/assets/8bd1e399-d26f-4140-9d50-426fdfb6d894)

   #### Synthesis check:
![WhatsApp Image 2025-01-04 at 8 39 08 AM (2)](https://github.com/user-attachments/assets/ceb54816-6f0d-468d-96ac-1c2c759eae8a)
   #### synthesis stats:
![WhatsApp Image 2025-01-04 at 8 39 08 AM](https://github.com/user-attachments/assets/b85c170a-1d25-43d8-ab72-4b8e9052ed43)
![WhatsApp Image 2025-01-04 at 8 39 08 AM (1)](https://github.com/user-attachments/assets/f8351887-95ed-4ae1-b418-a21d3b270495)

   #### Commands for floorplan:
        make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk floorplan
![WhatsApp Image 2024-12-21 at 10 15 59 AM (1)](https://github.com/user-attachments/assets/0ab187cd-67a8-4f19-bbe2-329bb2a5aa6d)
![WhatsApp Image 2024-12-21 at 10 15 59 AM](https://github.com/user-attachments/assets/8ede60ce-24d8-4f5a-9a5d-37dd3d0b87c2)

  
   #### Command for floorplan gui
         make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_floorplan
![WhatsApp Image 2024-12-21 at 10 15 59 AM (2)](https://github.com/user-attachments/assets/9530b0f0-c35c-40f3-af54-a69811f767ea)

   #### FLOORPLAN gui
 ![WhatsApp Image 2024-12-21 at 10 15 59 AM (3)](https://github.com/user-attachments/assets/723feac5-cb40-4ec5-b40c-6e92183c44b0)

   #### Command for placement:
        make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk place
![WhatsApp Image 2024-12-21 at 10 15 59 AM (4)](https://github.com/user-attachments/assets/d1b3f6da-52c4-4cef-bba6-8536f568a38e)
![WhatsApp Image 2024-12-21 at 10 15 59 AM (5)](https://github.com/user-attachments/assets/54c33f4a-271f-4892-9097-b6d9f8a1eef7)

   #### Command for placement gui
        make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_place
        
![WhatsApp Image 2024-12-21 at 10 30 15 PM](https://github.com/user-attachments/assets/01055240-51c0-4f4b-986a-c2a6e16ca69e)

   #### PLACEMENT gui
        make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_place
![WhatsApp Image 2024-12-21 at 10 15 59 AM (6)](https://github.com/user-attachments/assets/24f53c56-032e-456a-8aa2-88a719782cb3)

   #### HEATMAP:
![WhatsApp Image 2024-12-21 at 10 15 59 AM (7)](https://github.com/user-attachments/assets/a70c100d-f324-4c92-bb07-7567201a36e7)

#### Command for CTS:
     make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk cts
![WhatsApp Image 2025-01-14 at 6 53 57 AM (2)](https://github.com/user-attachments/assets/aa347298-dc8f-4361-9819-c6f219d792a5)
![WhatsApp Image 2025-01-14 at 6 53 57 AM (1)](https://github.com/user-attachments/assets/7fcab10c-8036-4b57-b77c-1b903fb937ae)

#### CTS gui:
     make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_cts
![WhatsApp Image 2025-01-14 at 6 53 57 AM (3)](https://github.com/user-attachments/assets/3732ed47-bb6e-408a-ab0f-4738ce5bf2cf)
![WhatsApp Image 2025-01-14 at 6 53 57 AM](https://github.com/user-attachments/assets/0c19d302-3623-4e18-beaa-844aecdb159a)

#### Command for Routing:
     make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk route
![WhatsApp Image 2025-01-14 at 6 53 56 AM](https://github.com/user-attachments/assets/2f2b8d93-cd5b-46eb-98be-e0dedfceed11)
