# SYNCHRONOUS-UP & DOWN-COUNTER
# Developed By: BALAJI B M
# Ref.No: 25016669

## AIM:
To implement 4 bit synchronous up and down counter and validate functionality.

## SOFTWARE REQUIRED:
Quartus prime

## THEORY:
### 4 bit synchronous UP Counter

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

### 4 bit synchronous DOWN Counter
In a 4-bit synchronous DOWN counter using J-K flip-flops, all flip-flops share the same clock, so they change state at the same time, eliminating ripple delay. The least significant flip-flop (Q0) toggles on every clock pulse. Each higher-order flip-flop toggles only when all preceding (lower-order) outputs are LOW (0). This is done by setting J = K = 1 for a flip-flop only when the required lower bits are 0. Because all flip-flops are clocked simultaneously and the toggle conditions are properly controlled, the counter counts downward in the correct sequence without ripple effect.

<img width="943" height="617" alt="image" src="https://github.com/user-attachments/assets/2701e858-0d24-4229-8a94-6d44455b2701" />

<img width="1014" height="627" alt="image" src="https://github.com/user-attachments/assets/a27aaa99-063f-4cdc-9fcd-aab34b2ddf8c" />

A 4-bit synchronous down counter is a digital circuit that reduces its output value by one on every clock pulse. Based on the logic in the diagram, here are the key points to understand how it works: Synchronous Operation: Unlike ripple counters, all four flip-flops (DFF0–DFF3) are connected to the same common clock signal (clk). This ensures that all bits change state at exactly the same time, preventing timing glitches. The Decrement Logic: To count "down," the circuit uses the inverted outputs (usually labeled \bar{Q}) or specific logic gates (AND/XOR) to determine when the next bit should toggle. A bit toggles only when all the preceding bits (to its right) are 0. Example: To go from 1000 (8) to 0111 (7), the three lower bits must all flip because they were all zeros. Active-Low Reset (rstn): The "bubble" on the reset pin indicates it is active-low. When this signal drops to 0, the counter immediately forces the output to a starting state (usually 1111 or 15 in a down counter). Counting Range: Since it is a 4-bit counter, it has 2^4 = 16 possible states. It counts from 15 down to 0 (1111 \rightarrow 0000) and then "rolls over" back to 15 to start again. Output Bus: The output is shown as a single line with a diagonal slash and the number 4, signifying it is a 4-bit wide bus containing the values of all four flip-flops.

## Procedure:
1.  Open Quartus Prime and create a new project for the synchronous counter design.
2.  Write the Verilog HDL code for the 4-bit synchronous UP counter and DOWN counter using a common clock and reset.
3.  Compile the program and check for syntax errors and successful compilation.
4.  Generate and verify the RTL schematic to confirm correct counter logic implementation.
5.  Run the functional simulation, observe the timing diagrams, and verify correct up and down counting operation.

## PROGRAM:
### UP COUNTER
```
module up(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out+1;
end
endmodule
```

### DOWN COUNTER
```
module down(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out-1;
end
endmodule
```

## RTL LOGIC UP COUNTER:
### UP COUNTER
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c24e31a5-0bf9-4083-90a7-df978a2166cc" />

### DOWN COUNTER
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6834be68-407e-447d-ae00-d9a1f88c4403" />

## TIMING DIAGRAM FOR IP COUNTER:
### UP COUNTER
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/abcf579b-77f3-469a-8bfd-136385787721" />

### DOWN COUNTER
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9b16b36f-3576-4dd6-a7a1-c7c554caa300" />

## TRUTH TABLE:
<img width="1034" height="501" alt="image" src="https://github.com/user-attachments/assets/22d6641e-8313-40eb-93d8-12870f51ae52" />

## RESULTS:
Thus the implementation of 4 bit synchronous up counter and down counter and the validate functionality is successful.
