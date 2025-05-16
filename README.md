# PCIe Gen6 VIP Development

## Overview
This project involves UVM-based verification of an existing PCIe Gen3 VIP, with enhancements and updates to support PCIe Gen6 features and test scenarios.

## Running VIP Testcase on Panther Server using QuestaSim

### Prerequisites:
1. **Panther Server Access**  
   Request access to the Panther server from the IT team if not already available.

2. **Environment Setup**  
   Follow internal documentation to correctly install and configure the Panther environment on your system.

### Steps:

3. **Create Working Directory**  
   Create a working directory (e.g., `PCIe_UVC_Dev`) under an appropriate location, such as:  
   `example/tb_pcie_svt_app_agent_uvm/PCIe_UVC_Dev`

4. **Copy Existing VIP Code**  
   Obtain the path to the existing Gen3 VIP codebase and copy it into your working directory. Make sure to include all required source files, environment configuration, and testbench files.

5. **Note on Simulator Choice**  
   Due to memory allocation issues with VCS, we are currently using **QuestaSim** for simulation.

6. **Launch QuestaSim**  
   From a terminal with environment variables set, launch QuestaSim using:
   vsim &
   
8. **Verify Simulation Directory**  
In the QuestaSim GUI, ensure that you are in the correct simulation directory (`PCIe_UVC_Dev`) containing your testbench and project files.

9. **Run the Simulation**  
Start the simulation by executing the following command inside the QuestaSim console:
do run.do
10. do file:
# Compile DUT and Testbench
vlog integrate.svh +incdir+/remote/pviphome01/uvm-1.1c/src 
vsim -novopt -suppress 12110 top -sv_lib /global/apps/mentor_graphics/questa_10.7d/questasim/uvm-1.2/linux_x86_64/uvm_dpi +UVM_TESTNAME=pcie_config_n_wr_rd_test +UVM_VERBOSITY=UVM_HIGH +RC_GOOD_PKT=2 +RC_BAD_PKT=0 +NUM_PKT=2
run -all
