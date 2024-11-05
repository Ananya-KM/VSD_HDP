# Day 4- GLS, Blocking vs Non-blocking, and Synthesis-Simulation Mismatch
## GLS, Synthesis-Simulation Mismatch, and Blocking/Non-blocking Statements
### GLS Concept andFlow using Iverilog
**Gate-Level Simulation (GLS)** checks the synthesized design to ensure it works correctly after synthesis, with proper timing and no setup/hold violations.

**GLS flow using Iverilog**:

1. **Write Testbench**: Create a testbench to test your design.
2. **Generate Gate-Level Netlist**: Synthesize your RTL into a gate-level netlist.
3. **Compile with Iverilog**: Compile the synthesized netlist and testbench.
4. **Run Simulation**: Simulate and check waveforms (timing and functionality).
5. **Analyze Results**: Verify if the design meets timing constraints and behaves as expected.

In short, GLS ensures your synthesized design behaves correctly under real gate delays and meets timing requirements.

<img width="631" alt="Screenshot 2024-11-05 062222" src="https://github.com/user-attachments/assets/dc3c0917-7272-4d05-9bb7-0c6f6daa6f1c">


**Gate-Level Simulation (GLS)** has two main types:

1. **Timing-Aware GLS (Back-Annotated)**:
   - **Purpose**: Verifies both **functionality** and **timing delays**.
   - **Details**: Uses **SDF** (Standard Delay Format) files to apply real gate delays, helping detect **setup/hold violations**.
   - **Use Case**: Used **post-synthesis** for final timing verification but is **slower** due to detailed timing modeling.

2. **Functional GLS (Zero-Delay)**:
   - **Purpose**: Verifies **functional correctness** without considering timing.
   - **Details**: Runs simulations with **zero-delay gates**, which makes it **faster** but ignores timing behavior.
   - **Use Case**: Used **immediately after synthesis** to confirm the design's logical equivalency to the RTL.

---

### **Synthesis-Simulation Mismatch**

This occurs when the synthesized gate-level netlist doesn’t match the behavior of the original RTL simulation. It can happen for various reasons:

1. **Missing Sensitivity List**:
   - **Cause**: If an RTL process (like an `always` block) lacks a complete sensitivity list, it won't trigger correctly.
   - **Example**: Omitting a signal from the sensitivity list in a combinational `always` block means it won’t react to that signal’s changes, causing mismatches.
   - **Solution**: Use `always @(*)` for combinational logic or ensure the sensitivity list is correct.

2. **Blocking vs. Non-Blocking Assignments**:
   - **Cause**: Incorrect use of `=` (blocking) and `<=` (non-blocking) assignments.
   - **Example**: Using blocking assignments in a clocked `always` block leads to incorrect sequential behavior since they update signals immediately, not after the clock edge.
   - **Solution**: Use non-blocking (`<=`) for sequential logic and blocking (`=`) for combinational logic.

3. **Non-Standard Verilog Coding**:
   - **Cause**: Using unconventional Verilog code can cause inconsistent behavior between simulation and synthesis.
   - **Example**: Leaving variables unassigned in some branches of a combinational block might create **inferred latches**, causing mismatches.
   - **Solution**: Follow standard Verilog practices to avoid inferred latches and ensure consistency.

4. **Caveats with Blocking Statements**:
   - **Cause**: Incorrect use of blocking statements, especially in sequential logic.
   - **Solution**: Always use non-blocking (`<=`) assignments in sequential logic to avoid simulation/synthesis mismatches.

In summary, GLS ensures that your design behaves as expected after synthesis, and common synthesis-simulation mismatches are often caused by improper Verilog coding practices.

## Labs on GLS and Synthesis-Simulation Mismatch
### 1.ternary_operator_mux.v
RTL Simulation

![WhatsApp Image 2024-11-05 at 5 38 40 AM](https://github.com/user-attachments/assets/f2963bf1-3787-4f44-b348-b031b40a9922)

Synthesis

![WhatsApp Image 2024-11-05 at 5 38 40 AM (1)](https://github.com/user-attachments/assets/702a6801-c554-46eb-80e7-ba4a79a9d52e)

![WhatsApp Image 2024-11-05 at 5 38 38 AM](https://github.com/user-attachments/assets/d53ec49a-7680-4642-b659-5385c86b85fc)

output

![WhatsApp Image 2024-11-05 at 5 38 36 AM](https://github.com/user-attachments/assets/1eeae96e-34aa-4f52-b90b-edee78e36c5f)

GLS Ouput

![WhatsApp Image 2024-11-05 at 5 38 34 AM](https://github.com/user-attachments/assets/42cc18af-1c5a-498d-a8ea-a96e79841899)

### 2.bad_mux.v

RTL Simulation 

![WhatsApp Image 2024-11-05 at 5 38 34 AM](https://github.com/user-attachments/assets/b8f56ca6-1182-47fd-9183-883dff2315a5)

Synthesis

![WhatsApp Image 2024-11-05 at 5 38 34 AM (1)](https://github.com/user-attachments/assets/360636d9-553b-4848-80d0-bfebd58321d3)

OUTPUT

![WhatsApp Image 2024-11-05 at 5 38 34 AM (2)](https://github.com/user-attachments/assets/545a0810-ad47-46f8-b4e5-0142fa90b2c6)

GLS Output

![WhatsApp Image 2024-11-05 at 5 38 34 AM (3)](https://github.com/user-attachments/assets/5d8601d7-f296-454e-9c5f-92c3218f731a)

## Labs on Synth-Sim Mismatch for Blocking Statement
### blocking_caveat

![WhatsApp Image 2024-11-05 at 5 38 34 AM](https://github.com/user-attachments/assets/25b19225-8b2a-43cf-97a3-0608cf027cd2)

![WhatsApp Image 2024-11-05 at 5 38 34 AM (1)](https://github.com/user-attachments/assets/b371e37e-34f0-41a6-a065-e99113a6cb1d)

![WhatsApp Image 2024-11-05 at 5 38 34 AM (2)](https://github.com/user-attachments/assets/f24bbd15-11d7-4dd5-b2a0-d01bf5ade5a1)

![WhatsApp Image 2024-11-05 at 5 38 34 AM (3)](https://github.com/user-attachments/assets/101605d0-25c3-48f9-b36d-dcf873670deb)

![WhatsApp Image 2024-11-05 at 5 38 34 AM (4)](https://github.com/user-attachments/assets/6906a832-f70c-422e-a736-1916823d1e74)

![WhatsApp Image 2024-11-05 at 5 38 34 AM (5)](https://github.com/user-attachments/assets/76907202-b8bc-45e8-b045-a0f0a814739b)
