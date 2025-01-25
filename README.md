# ALU DESIGN


## Basic Details
### Team Name: Ohmies


### Team Members
- Team Lead: Aiswarya Chandrasekharan - Toc H Institute of Science and Technology
- Member 2: Bhavana V Nair - Toc H Institute of Science and Technology

### Project Description
This project focuses on the design and construction of 4 bit Arithmetic and Logic Unit (ALU) using Xilinx Vivado. ALU is the most integral part of the processor and is the frequently accessed module during instruction execution. Here we designed an ALU based on combinational logic and is simulated and further synthesized to generate the gate level netlist. The timing diagram is also obtained to verify the result which can be later implemented in a Field Programmable Gate Array (FPGA) board. This ALU performs 16 operations including Addition, Subtration , multiplication , division , shift operations , rotate operations and many logical operations like AND , OR , XOR , XNOR , NOR , NAND and conditional operations. The basic building blocks include adders , multiplexers and basic logic gates.


### The Problem 
Area required , Power consumption and Speed are the various performace parameters of any ALU. By studying the speed , power and timing analysis reports of the circuit and thus making significant changes in it's design will lead the path for many custom processors.

## Technical Details
### Technologies/Components Used
For Software:
- Xilinx Vivado

### Implementation
For Software: 
Verilog Code:
module alu1(
    input [3:0] A,B,
    input [3:0] ALU_Sel,
    output [3:0] ALU_out,
    output CarryOut
    );
    reg [3:0] ALU_Result;
    wire [4:0] tmp;
    assign ALU_out=ALU_Result;
    assign tmp = {1'b0,A} + {1'b0,B};
    assign CarryOut = tmp[4];
    always @(*)
    begin
        case(ALU_Sel)
        4'b0000:
        ALU_Result = A + B ;
        4'b0001:
        ALU_Result = A - B ;
        4'b0010:
        ALU_Result = A * B ;
        4'b0011:
        ALU_Result = A/B ;
        4'b0100:
        ALU_Result = A<<1 ;
        4'b0101:
        ALU_Result = A>>1 ;
        4'b0110:
        ALU_Result = {A[2:0],A[3]};
        4'b0111:
        ALU_Result = {A[0],A[3:1]} ;
        4'b1000:
        ALU_Result = A & B ;
        4'b1001:
        ALU_Result = A | B ;
        4'b1010:
        ALU_Result = A ^ B ;
        4'b1011:
        ALU_Result = ~(A | B);
        4'b1100:
        ALU_Result = ~(A & B);
        4'b1101:
        ALU_Result = ~(A ^ B) ;
        4'b1110:
        ALU_Result =(A>B)?4'd1:4'd0 ;
        4'b1111:
        ALU_Result = (A==B)?4'd1:4'd0 ;
        default: ALU_Result = A + B;
        endcase
    end

TestBench Code:
module TB_ALU1;
reg[3:0] A,B;
reg[3:0] ALU_Sel;
wire[3:0] ALU_out;
wire CarryOut;
alu1 uut(
            A,B,
            ALU_Sel,
            ALU_out,
            CarryOut
    );
   initial begin 
   A=4'b1010;    B=4'b0010;
   ALU_Sel= 4'b0000; #10;
   ALU_Sel= 4'b0001; #10;
   ALU_Sel= 4'b0010; #10;
   ALU_Sel= 4'b0011; #10;
   ALU_Sel= 4'b0100; #10;
   ALU_Sel= 4'b0101; #10;
   ALU_Sel= 4'b0110; #10;
   ALU_Sel= 4'b0111; #10;
   ALU_Sel= 4'b1000; #10;
   ALU_Sel= 4'b1001; #10;
   ALU_Sel= 4'b1010; #10;
   ALU_Sel= 4'b1011; #10;
   ALU_Sel= 4'b1100; #10;
   ALU_Sel= 4'b1101; #10;
   ALU_Sel= 4'b1110; #10;
   ALU_Sel= 4'b1111; #10;
end
endmodule

# Documentation
https://drive.google.com/file/d/1RGmW7a_dJqSn0B4iuq0hJcFDgJ7F3vYj/view?usp=drive_link

# Diagrams
https://drive.google.com/file/d/1RGmW7a_dJqSn0B4iuq0hJcFDgJ7F3vYj/view?usp=drive_link

# Schematic & Circuit
https://drive.google.com/file/d/1RGmW7a_dJqSn0B4iuq0hJcFDgJ7F3vYj/view?usp=drive_link

---
Made with ❤️ at TinkerHub Useless Projects 

![Static Badge](https://img.shields.io/badge/TinkerHub-24?color=%23000000&link=https%3A%2F%2Fwww.tinkerhub.org%2F)
![Static Badge](https://img.shields.io/badge/UselessProject--24-24?link=https%3A%2F%2Fwww.tinkerhub.org%2Fevents%2FQ2Q1TQKX6Q%2FUseless%2520Projects)



