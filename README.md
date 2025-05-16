# PCIe_gen6_VIP_development

## Overview
This project provides a UVM-based development and verification of existing Gen3 VIP and upgrading to Gen6 VIP by adding all features and testing

## Steps followed to run VIP testcase in Panther server using Questa sim:
1) Panther server access required, so install Panther server asking for access from IT team
2) Setup env as guidelines given for installing Panther in your device
3) When its done, create a separate directory naming 'PCIe_UVC_Dev' say, inside example/tb_pcie_svt_app_agent_uvm
4) Copy the path provided to get the existing code for VIP
5) Not runnign using vcs for now due to memory allocation issue, so run using questa sim
6) To open questa sim: vsim &
7) Check in the questasim tool if you are present in the simulation area, say PCIe_UVM_dev
8) To fire run: do run.do
