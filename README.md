
# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM: 
 To simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop
And counters using Vivado 2023.2

# APPARATUS REQUIRED:

vivado 2023

# PROCEDURE:

STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button.
Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

**LOGIC DIAGRAM**

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

# VERILOG CODE
module SR(clk,s,r,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

Endmodule


# Output
![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/13ae7331-9150-4461-a222-f6f6ab58e356)


# JK FLIPFLOP

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/c5a1ef17-09ca-4864-bb06-a06fb585b2d2)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

VERILOG CODE

module jk(j,k,clk,rst,Q);

input j,k,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)Q=0;

else

begin

case({j,k})

2'b00:Q=Q;

2'b01:Q=0;

2'b10:Q=1;

2'b11:Q=~Q;

endcase

end

end

Endmodule

# Output
![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/adfb4971-8b9d-44bd-a708-f3ee67a5c55a)

# T FLIPFLOP

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/14ea1615-047f-4916-b9ea-637649d8d925)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

# VERILOG CODE
module tff(t,clk,rst,Q);

input t,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else if(t==0)

Q=Q;

else

Q=~Q;

end

Endmodule

# Output
![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/123b9b9f-9cc8-4761-880f-1e780d7e8af8)

# D FLIPFLOP

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/c70eaf3c-96ed-48db-a866-59020ff2ce91)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

# VERILOG CODE
module dff(d,clk,rst,Q);

input d,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else

Q=d;

end

Endmodule

# Output
![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/4a97b830-d1c7-4746-93f1-a932a58bc03c)

COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

# Updown Counter
![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/0bc45ff9-8d61-4805-a051-bd9bc2e25088)

# VERILOG CODE
module updown(clk,rst,updown,out);

input clk,rst,updown;

output reg[3:0]out;

always@(posedge clk)

begin

if(rst==1)

out=4'b0000;

else if(updown==1);

out=out-1;

end

endmodule

# Output

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/6789f805-c995-4c30-9dcf-99c79e948976)

# MOD COUNTER

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/ceadd76e-a2a7-4ce4-a113-3730028a95ee)

# VERILOG CODE

module mod(clk,rst,out);

input clk,rst;

output reg[3:0]out;

always @(posedge clk)

begin

if(rst==1 | out==4'b1001)

out=4'b0000;

else

out=out+1;

end

endmodule
# Output

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/fbd89778-9bcb-49d6-a09e-3a2bbe66b8e0)

# RIPPLE CARRY COUNTER

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/e24a094a-26da-429b-bedf-ec7076b34625)

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/4efea111-bc3f-4ccd-93ce-182f195699cf)

# VERILOG CODE

module ripple_carry_counter(q, clk, reset);

output [3:0] q;

input clk, reset;

T_FF tff0(q[0], clk, reset);

T_FF tff1(q[1], q[0], reset);

T_FF tff2(q[2], q[1], reset);

T_FF tff3(q[3], q[2], reset);

endmodule


module T_FF(q, clk, reset);

output q;

input clk, reset;

wire d;

D_FF dff0(q, d, clk, reset);

not n1(d, q); 

endmodule


module D_FF(q, d, clk, reset);

output q;

input d, clk, reset;

reg q;

always @(posedge reset or negedge clk)

if (reset)

q = 1'b0;

else

q = d;

endmodule
   
# Output

![image](https://github.com/priyangi123/VLSI-LAB-EXP-4/assets/165141104/4215e31f-73a4-477a-95a3-f954d3d7d82c)

# RESULT

Thus simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop
And counters was succesfully executed and verified.


