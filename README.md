EXP-4

date:

                   SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

AIM: o simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Vivado 2023.1.


APPARATUS REQUIRED:

Vivado 2023.1



PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

Logic Diagram 2 bit Multiplier

**LOGIC DIAGRAM**

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


VERILOG CODE
```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```

OUTPUT 

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/e224f622-d3ab-4581-a429-acdb15ce45eb)

JK FLIPFLOP

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/9e051266-d88c-4d9e-9874-a911f751dfd1)

VERILOG CODE
```
module JK_flipflop (q, q_bar, j,k, clk, reset);
  input j,k,clk, reset;
  output reg q;
  output q_bar;
  always@(posedge clk) begin
    if(!reset)�        q <= 0;
    else 
  begin
      case({j,k})
        2'b00: q <= q;  
        2'b01: q <= 1'b0; 
        2'b10: q <= 1'b1;
        2'b11: q <= ~q; 
      endcase
    end
  end
  assign q_bar = ~q;
endmodule
```
OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/9e3a5ce8-fc24-4896-8df5-6edb9857198a)

T FLIPFLOP

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/3ac31959-9f10-49bb-825e-4624d75aff0f)

VERILOG CODE
```
module tff (t,clk, rstn,q);  
 input t,clk, rstn;
 output reg q;
  always @ (posedge clk) begin  
    if (!rstn)  
      q <= 0;  
    else  
        if (t)  
            q <= ~q;  
        else  
            q <= q;  
  end  
endmodule
```

OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/cf276d7a-a8fa-4a2e-967e-5fa2c3e85d54)

D FLIPFLOP

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/2a5769e6-36a7-4b61-bf8e-0e51a770b845)

VERILOG CODE
```
module DFlipFlop (D, clk, reset, Q) ;
input D;
input clk;
input reset; 
output reg Q; 
always @ (posedge clk)
begin
    if(reset == 1'b1)
        Q <= 1'b0;
    else
        Q <= D;
end
endmodule
```
OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/184f283a-764c-47db-b75c-2b3e956cb0c3)

COUNTER

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/62f68304-d070-4148-81b5-093db4fcc512)

Ripple Carry Counter
VERILOG CODE
```
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
module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); 
endmodule
module ripple_carry_counter(q, clk, reset);
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset);
T_FF tff1(q[1], q[0], reset);
T_FF tff2(q[2], q[1], reset);
T_FF tff3(q[3], q[2], reset);
endmodule
```
OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/304a3841-997a-444a-8abd-a90ddb2bc018)

MOD 10 COUNTER
VERILOG CODE
```
module counter(
input clk,rst,enable,
output reg [3:0]counter_output
);
always@ (posedge clk)
begin 
if( rst | counter_output==4'b1001)
counter_output <= 4'b0000;
else if(enable)
counter_output <= counter_output + 1;
else
counter_output <= 0;
end
endmodule
```
OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/8ad2b8ea-9d29-422c-bb60-0f1204e35c2a)

UP DOWN COUNTER
VERILOG CODE
```
module updown_counter(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```
OUTPUT

![image](https://github.com/kristipatishivani/VLSI-LAB-EXP-4/assets/161432255/db732c1d-6b6f-4ed6-8757-c29fad38fe78)


RESULT:
       Thus the simulation and implementation of sequential logic gates is done and verified.









   

