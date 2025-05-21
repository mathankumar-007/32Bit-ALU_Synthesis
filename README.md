![WhatsApp Image 2025-05-21 at 15 28 31_bd627e30](https://github.com/user-attachments/assets/86bdfede-2943-4e26-b1a3-3672b22a6ffd)# 32Bit-ALU_Synthesis

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)
```
read_libs /cadence/install/FOUNDRY-01/digital/90nm/dig/lib/slow.lib
read_hdl alu_32bit.v
elaborate
syn_generic
report_area
syn_map
report_area
syn_opt
report_area 
report_area > alu_area.txt
report_power > alu_power.txt
report_gates > alu_gates.rpt
report_timing > alu_timing.txt
write_hdl >alu_netlist.v
gui_show
```
```
module alu_32bit_case(y, a, b, f);
  input [31:0] a;
  input [31:0] b;
  input [2:0] f;
  output reg [31:0] y;

  always @(*) begin
    case(f)
      3'b000: y = a & b;       // AND
      3'b001: y = a | b;       // OR
      3'b010: y = ~(a & b);    // NAND
      3'b011: y = ~(a | b);    // NOR
      3'b100: y = a + b;       // ADD
      3'b101: y = a - b;       // SUB
      3'b110: y = a * b;       // MUL
      default: y = 32'bx;      // Undefined
    endcase
  end

endmodule
```

### Step 2 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
![WhatsApp Image 2025-05-21 at 15 28 32_acef9f9c](https://github.com/user-attachments/assets/04a040f5-92a7-48e9-875f-1d25ba3f7cb9)

#### Area report:
![WhatsApp Image 2025-05-21 at 15 28 31_775143b1](https://github.com/user-attachments/assets/6d610845-9896-4101-860b-ccb2c94bb907)

#### Power Report:
![WhatsApp Image 2025-05-21 at 15 28 31_5d61e3cd](https://github.com/user-attachments/assets/2a6a7daf-eefb-4b83-84cc-8985d224e6ab)


#### Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
