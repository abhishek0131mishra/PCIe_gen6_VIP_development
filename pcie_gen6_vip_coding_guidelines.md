###  PCIe Gen6 VIP – Coding Guidelines

#### 1. General Principles
- Follow consistency, clarity, and modularity.
- Prioritize readability over cleverness.
- Reuse common components and follow DRY (Don't Repeat Yourself) principles.

---

#### 2. File Organization

- **File Naming Convention:**
  - Prefix file names with the layer/module for clarity.
    ```
    pcie_tlp_agent.sv
    pcie_config_space.sv
    pcie_gen6_seq_lib.sv
    ```
- **Directory Structure:**
- Put components/files coded within proper area as structured below
  ```
  src/
    agents/
    monitors/
    drivers/
    sequences/
    scoreboard/
    env/
    tb/
  docs/
    coding_guidelines.md
    architecture.md
  ```
---

#### 3. Naming Conventions

- **Classes/Modules/Interfaces:** 
  ```systemverilog
  class pcie_tlp_agent extends uvm_agent;
  class pcie_gen6_env extends uvm_env;
  ```
- **Functions/Tasks:** 
  ```systemverilog
  function void build_phase(uvm_phase phase);
  ```
- **Signals/Variables:** 
  ```systemverilog
  logic valid_data;
  bit[63:0] tlp_header;
  ```
- **Parameters/Defines:** `ALL_CAPS_WITH_UNDERSCORES`
  ```systemverilog
  parameter MAX_PAYLOAD_SIZE = 1024;
  `define DEFAULT_TIMEOUT 1000
  ```

---

#### 4. Indentation and Spacing

- Use **2 spaces per indentation level**.
- Do **not use tabs**. Convert tabs to spaces in your editor settings.
- Align continued statements:
  ```systemverilog
  if (valid_data && (tlp_type == MEM_RD32 || 
                     tlp_type == MEM_RD64)) begin
    ...
  end
  ```

- Add a space after commas, semicolons, and around binary operators:
  ```systemverilog
  a = b + c;
  my_function(arg1, arg2);
  ```

---

#### 5. UVM Component Guidelines

- Register all UVM components using factory:
  ```systemverilog
  `uvm_component_utils(pcie_tlp_agent)
  ```
---

#### 6. Comments and Documentation

- Use `//` for single-line comments, `/* */` only when necessary.
- Start module/class/function blocks with a short description.
  ```systemverilog
  // Monitors outgoing TLP packets and reports them to scoreboard
  class pcie_tlp_monitor extends uvm_monitor;
  ```
---

#### 7. Do’s and Don’ts

**✅ Do:**
- Use typedefs for enums and structs.
- Use `uvm_report_*` macros for messaging.
- Use consistent naming across environments and agents.

**❌ Don’t:**
- Hardcode delays or magic numbers.
- Mix functionality of different abstraction layers in a single class.
- Use wildcard imports (`import pkg::*;`) unless justified.

#### 8. Error Handling

- Use appropriate `uvm_report_*` macros: `uvm_info`, `uvm_warning`, `uvm_error`, `uvm_fatal`.
- Always provide meaningful messages and include `UVM_NONE/UVM_LOW` etc., verbosity levels.

---
