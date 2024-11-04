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
7. 
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



