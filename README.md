# APEX-CV: Custom Tensor Accelerator Integration for RISC-V

> ⚠️ **Status:** Manuscript in preparation. Full RTL source code and Vivado implementation files are withheld pending journal submission. Source access is available to recruiters upon request.

## Overview
APEX-CV is a custom, reliability-aware AI accelerator designed for highly efficient edge inference. Built from first principles, the project integrates a custom Sparse Tensor Engine with the OpenHW Group’s CV32E40P RISC-V core. The system accelerates neural network workloads while dynamically managing sparsity and characterizing hardware fault vulnerabilities.

## System Architecture
The accelerator functions as a tightly coupled IP block within a System-on-Chip (SoC) environment, interfacing via AXI4 standard protocols.
* **Sparse Tensor Engine:** A custom 4x4 Processing Element (PE) array optimized for multiprecision matrix operations.
* **Hardware Zero-Skipping (`apex_zero_gate`):** Dedicated gating logic handles 2:4 structured weight sparsity and dynamic activation sparsity. By halting multiplier inputs and accumulator updates upon zero-detect, the architecture significantly reduces dynamic power consumption.
* **Memory & Control:** Features a 6D Address Generation Unit (AGU) and an AXI4 DMA read master for autonomous, high-bandwidth data fetching without stalling the host CPU.

![Vivado Block Design](https://github.com/user-attachments/assets/c3ce9c78-6450-4cad-a883-219a735bed71)

## Hardware Implementation & Results
The full APEX-CV architecture has been successfully synthesized, implemented, and validated on silicon. 
* **Target Hardware:** Xilinx ZCU104 Evaluation Board (Zynq UltraScale+ MPSoC)
* **Operating Frequency:** 44.12 MHz (Board-verified)
* **Integration:** Connected to the Zynq Processing System via AXI SmartConnect interconnects.

![Vivado Floorplan](https://github.com/user-attachments/assets/bce61936-ebb6-480c-bd8f-3851408e4f3c)
<img width="1337" height="422" alt="pouti" src="https://github.com/user-attachments/assets/e17ef644-1626-47da-85a8-7e811e86852d" />

## Verification & Fault-Injection Framework
Beyond standard functional verification, APEX-CV includes a comprehensive fault-injection testing framework to evaluate reliability in edge AI environments.
* **Bit-Band Sensitivity Inversion:** Through extensive fault-injection campaigns, we demonstrated that in specific control and status registers, LSBs dictate functionality (resulting in near-100% Architectural Vulnerability Factor), whereas MSBs remain largely resilient. 

## Project Team
**Authors:** Mohamed Shanil, Hafiz Ahmed C., Adhil Fayad C.P., Hanan Sha  
**Institution:** TKM College of Engineering, Kollam  
**Mentorship:** Prof. Zainaba N (Guide), Prof. Arun A.V (Co-Guide), Prof. Varun P. Gopi (Co-Guide)
