# 4-BIT-RIPPLE-COUNTER
 Developed by:AADHITHAN B RegisterNumber:212224040001
 
**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**
1.Increment count on each positive edge of the clock.

2.Reset count to zero when it reaches 15.

3.Generate clock signal (clk).

4.Instantiate the RippleCounter module.

5.Conduct functional testing by displaying the count at each clock cycle for 16 cycles.



**PROGRAM**

```
    module ripple (
   input clk,     // Clock input
   input reset,   // Reset input (active high)
   output [3:0] q // 4-bit output
   );
  // Internal signals for flip-flops
 reg [3:0] q_int;

  // Assign internal register to output
 assign q = q_int;

always @(posedge clk or posedge reset) begin
if (reset) 
    q_int[0] <= 1'b0; // Reset the first bit to 0
else 
    q_int[0] <= ~q_int[0]; // Toggle the first bit on clock edge
end

// Generate the other flip-flops based on the output of the previous one
genvar i;
generate
for (i = 1; i < 4; i = i + 1) begin : ripple
    always @(posedge q_int[i-1] or posedge reset) begin
        if (reset) 
            q_int[i] <= 1'b0; // Reset the bit to 0
        else 
            q_int[i] <= ~q_int[i]; // Toggle the bit on clock edge of previous stage
    end
end
endgenerate
endmodule
```
 Developed by:AADHITHAN B RegisterNumber:212224040001
*/

**RTL LOGIC FOR 4 Bit Ripple Counter**

![image](https://github.com/user-attachments/assets/acbf0373-0f49-4237-9f10-e1163e07eb2a)



**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![image](https://github.com/user-attachments/assets/bf9f3f6b-fe03-4e84-a10c-f599b152bda4)


**RESULTS**

THE 4 BIT RIPPLE COUNTER IS VERIFIED SUCCESSFULLY.
