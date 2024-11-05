# DAY 3
# Combinational and Sequential Optimizations
## Introduction to optimizations
## Combinational Logic Optimisation:
### Technique used for combinatinal optimisation:
#### 1.Constant propogation- Direct optimisation technique using boolean expression

<img width="574" alt="Screenshot 2024-11-04 100424" src="https://github.com/user-attachments/assets/563894e7-656d-4fb8-8b0c-03b023cbf6b8">

#### 2.Boolean logic optimization- Uses K-map and Quine Mckluskey and boolean expression to optimize the logic

<img width="609" alt="Screenshot 2024-11-04 100437" src="https://github.com/user-attachments/assets/760da673-ae98-4fb6-905e-b520ab0d65c8">


**Basic Techniques:**
- **Sequential Constant Propagation:** This technique involves simplifying circuits by identifying outputs that remain constant regardless of the reset and clock signals.

**Advanced Techniques:**
- **State Optimization:** This process focuses on minimizing the number of states in a sequential circuit, improving efficiency and reducing complexity.
- **Retiming:** This involves rearranging the timing of registers in a circuit to enhance performance without altering the overall functionality.

**Additional Technique:**
- **Sequential Logic Cloning:** This refers to creating duplicate copies of sequential elements to optimize circuit performance and manage complexity.
- 
 <img width="632" alt="Screenshot 2024-11-04 100523" src="https://github.com/user-attachments/assets/c7ecc86b-cc06-402e-a5c1-42f1a5cb6a70">

#### Advanced optimization:

<img width="616" alt="Screenshot 2024-11-04 100544" src="https://github.com/user-attachments/assets/c9609642-cb0c-47cf-8fda-c5d1c468b255">

## Combinational Logic Optimizations
### opt_check 1
steps
Sure! Here are the steps:

Here are your updated steps:

1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog opt_check1.v`
3. `synth -top opt_check1`
4. `opt_clean -purge`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`
##### Synthesis result
![WhatsApp Image 2024-11-04 at 9 28 31 AM](https://github.com/user-attachments/assets/56edff2e-cdb2-4d1f-8e3f-1e668e3816b2)
###### Optimization
![WhatsApp Image 2024-11-04 at 9 28 31 AM (1)](https://github.com/user-attachments/assets/5409423f-613c-4d48-a841-cf2f236f02ee)
###### Result:
![WhatsApp Image 2024-11-04 at 9 28 31 AM (2)](https://github.com/user-attachments/assets/ae3a9fba-3204-4cc9-97f7-9aaa6a04a50c)

### opt_check 2
steps
Here are your updated steps:

1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog opt_check2.v`
3. `synth -top opt_check2`
4. `opt_clean -purge`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM](https://github.com/user-attachments/assets/306bd599-2b50-4477-ab5b-ba9d70e6c08b)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (1)](https://github.com/user-attachments/assets/d9e41d9d-13b4-44cf-a402-cf3b520f9e0d)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (2)](https://github.com/user-attachments/assets/1da61c0f-95d9-4460-8c09-b27417ad02a7)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (3)](https://github.com/user-attachments/assets/ddd7419e-1c94-42bb-9115-53f0f6a3208e)

### opt_check 3
steps

1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog opt_check3.v`
3. `synth -top opt_check3`
4. `opt_clean -purge`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (4)](https://github.com/user-attachments/assets/ddb4f228-91c5-45ed-a4bd-fc3a4b5c0d89)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (5)](https://github.com/user-attachments/assets/1acae6e4-1bb4-4d0d-811a-aa74b45c7639)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (6)](https://github.com/user-attachments/assets/80f3e012-7ba3-4518-bc3f-9bbb6de97863)

### opt_check 4

Steps

1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog opt_check4.v`
3. `synth -top opt_check4`
4. `opt_clean -purge`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (7)](https://github.com/user-attachments/assets/66bfaa4d-f38f-45c6-b537-8f3457bdf071)

![WhatsApp Image 2024-11-04 at 9 28 28 AM (8)](https://github.com/user-attachments/assets/c2373cef-52cf-47fd-95db-ea616f0e3613)

## Sequential Logic Optimizations
### dff_const 1
steps
1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog dff_const1.v`
3. `synth -top dff_const1`
4. `dfflibmap -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (1)](https://github.com/user-attachments/assets/1989544e-ae60-42b0-a591-ef3ade88bbc4)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (2)](https://github.com/user-attachments/assets/13b7b84c-6587-4d13-a492-42db7a95c52e)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (3)](https://github.com/user-attachments/assets/2709e9a7-6ab6-48d5-86fe-bf21d0d904b6)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (4)](https://github.com/user-attachments/assets/a8df0522-1f2b-4524-936f-632e42837b63)

### dff_const 2
steps
1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog dff_const2.v`
3. `synth -top dff_const2`
4. `dfflibmap -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`
   
![WhatsApp Image 2024-11-04 at 9 28 28 AM (5)](https://github.com/user-attachments/assets/9d5a2b09-53bb-4e82-b8cd-c0ef81cb63e1)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (6)](https://github.com/user-attachments/assets/b2f303a8-a7a1-4b85-86c2-29ba9e3ad5be)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (7)](https://github.com/user-attachments/assets/7689188d-9996-41d8-9d29-a7ba7de442b6)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (8)](https://github.com/user-attachments/assets/e128eb45-d0f5-4660-abef-f342300f8fcc)

### dff_const 3
steps
1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog dff_const3.v`
3. `synth -top dff_const3`
4. `dfflibmap -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (10)](https://github.com/user-attachments/assets/83fc6b15-7b0c-4c59-b02f-ebc556c0c146)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (11)](https://github.com/user-attachments/assets/47105836-d07b-49f2-acf6-a398ba61457d)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (12)](https://github.com/user-attachments/assets/bd60aa4f-c8d6-47d0-b089-3199f1bb8e25)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (13)](https://github.com/user-attachments/assets/cb25d0db-c999-416f-b11e-f11335b020f4)

### dff_const 4
steps

1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog dff_const4.v`
3. `synth -top dff_const4`
4. `dfflibmap -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (9)](https://github.com/user-attachments/assets/b52b9ccc-ffd8-4507-975c-412bbb799d34)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (14)](https://github.com/user-attachments/assets/b6cd712b-5261-48e4-bffe-1a5ddffce847)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (15)](https://github.com/user-attachments/assets/614dc271-50e7-422e-b415-01704b791696)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (16)](https://github.com/user-attachments/assets/afe11647-8d3f-4f9f-beeb-d72cef41d042)

### dff_const 5
steps

1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog dff_const5.v`
3. `synth -top dff_const5`
4. `dfflibmap -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (17)](https://github.com/user-attachments/assets/18a907db-dbf5-42be-b606-a2851329971e)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (18)](https://github.com/user-attachments/assets/8ac2d8f4-5437-4eee-9030-1267a4307ba8)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (19)](https://github.com/user-attachments/assets/1530dd77-11ac-422d-8f43-7bc2b1e08ff9)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (20)](https://github.com/user-attachments/assets/f8572032-d171-4a66-b93d-d59967444fab)


## Sequential Optimizations for Unused Outputs
### counter_opt
steps
1. `read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
2. `read_verilog counter_opt.v`
3. `synth -top counter_opt`
4. `dfflibmap -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
5. `abc -liberty ../lib/sky130_fd_sc_hd_tt_025_1v80.lib`
6. `show`

![WhatsApp Image 2024-11-04 at 9 28 28 AM (21)](https://github.com/user-attachments/assets/4412ef11-1ec1-458e-ac1c-d8e85d9ae8da)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (22)](https://github.com/user-attachments/assets/ff958f4c-5a10-4f4f-96a8-7075350c8857)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (23)](https://github.com/user-attachments/assets/cc6d14e7-da71-4fc2-a755-3568cecd921f)
![WhatsApp Image 2024-11-04 at 9 28 28 AM (24)](https://github.com/user-attachments/assets/08d7e3ff-b8b6-4baa-9234-8887ed82b65e)




   

   


