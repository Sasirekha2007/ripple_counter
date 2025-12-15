AIM:

To implement 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

SOFTWARE REQUIRED:

Quartus prime

THEORY

4 Bit Ripple Counter

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.


<img width="696" height="356" alt="Screenshot 2025-12-15 161337" src="https://github.com/user-attachments/assets/c68843e1-304b-4f37-ad7b-058582d9c6d9" />


In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

<img width="468" height="387" alt="Screenshot 2025-12-15 161345" src="https://github.com/user-attachments/assets/6ee30dc1-8952-4d92-b5d0-bd668d5931ac" />



<img width="367" height="298" alt="Screenshot 2025-12-15 161351" src="https://github.com/user-attachments/assets/d6c1156d-7df9-4187-8160-61f44eb9a74c" />



PROGRAM

module RIPPLECOUNTER(q, clk, reset); 
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset); 
T_FF tff1(q[1], q[0], reset); 
T_FF tff2(q[2], q[1], reset); 
T_FF tff3(q[3], q[2], reset); 
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

module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); // not is Verilog-provided primitive. 
endmodule


Developed by:B.SASIREKHA


RegisterNumber: 25015734

RTL LOGIC FOR 4 Bit Ripple Counter

TIMING DIGRAMS FOR 4 Bit Ripple Counter

RESULTS
