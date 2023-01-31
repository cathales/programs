
[comment]: # "this template is for ARVM projects"

# **ARVM-FunctionalCoverage** Monthly Report for 16-January-2023

Project leader : Simon Davidmann   
Lead company :  Imperas  
Participating companies : SiLabs, Dolphin  

## Overview
There are almost 1,000 instructions in RV64 (inc. all ratified and soon to be ratified extensions).  
For each instruction somebody will need to write SystemVerilog covergroups and coverpoints…   
Maybe 10-40 lines of SystemVerilog for each instruction…   
That is 10,000-40,000 lines of SystemVerilog code to be written for each core… (and be correct and working…)  
And that is just for the basic un-privilege mode ISA…   

This sub-project is to collect requirements to enable the developing of VIPs (such as functional coverage) that can be used for many different core configurations/implementations.  

## Current Status
cv32e40p included and used first generation of SystemVerilog for RV32I generated by Imperas in 2020.  

Initial focus of this project is F,Zfinx (FPU) functional coverage for cv32e40pv2 (Dolphin) and Zc for cv32e40s (SiLabs).   
This second generation architecture is auto generated and works directly from RVVI-TRACE core tracer testbench interface.   

Uses machine readable ISA definition and generates examples as compliance level functional coverage for RV32I.  

This riscvISACOV is now documented and RV32I is available as open source from github: [https://github.com/riscv-verification/riscvISACOV](https://github.com/riscv-verification/riscvISACOV)

Currently soliciting input / requirements on what needs to be covered in verification plans for different ISA extensions.   

Also, beta code has been generated for many extensions, including: 32 bit I, E, M, C, B, K.  237 instructions covered in 2030 coverpoints.  

## Key activities / tasks completed this month
- F,Zfinx (FPU): First SystemVerilog functional coverage code for FPU has been generated and feedback from Dolphin has meant many more cross coverage and fixed values have been included.
- Zc (code-size-reduction): has been coded up and generated coverage is being reviewed by SiLabs - with feedback on cross coverage - and requirements for interrupt coverage across multi-cylce instructions like push/pop/mv  
    - This is now included in pull request for [core-v-verif/cv32e40s/vendor_lib/imperas/riscvISACOV/source/coverage/](https://github.com/openhwgroup/core-v-verif/tree/960880333a53d44b403c4d094d77b37652718880/cv32e40s/vendor_lib/imperas/riscvISACOV/source/coverage)  
- output of code generator has sections for verification plan in .csv - currently being reviewed  
- output also .md files of summaries of each extension

## Planned activities / tasks for coming month
- reviews of resultant functional coverage (RV32I, F, Zc)   
- addition of more requirements for F and Zc
- complete interrupt coverage over multi-cycle instructions  
- addition of more design verification (DV) coverage such as hazards (and micro-architectural)   
- discussions regarding working with isacov

## Issues / items that are slowing progress
- Zc functional coverage is currently awaiting update to RVVI to handle async trap handler notifications for cross coverage

