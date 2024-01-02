## NAME: GOKUL SACHIN
## REFERENCE NO: 23004843
## Exp-6-Synchornous-counters - up counter and down counter
## AIM: To implement 3 bit up and down counters and validate functionality.
## HARDWARE REQUIRED: – PC, Cyclone II , USB flasher
## SOFTWARE REQUIRED: Quartus prime
## THEORY
## UP COUNTER
The counter is a digital sequential circuit and here it is a 3 bit counter, which simply means it can count from 0 to 7 and vice versa based upon the direction of counting (up/down).

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle. The Counter will be set to Zero when “reset” input is at logic high. The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down. The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output. The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence. Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1: Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

Three-bit “Up” Counter up
![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/b5c572b7-5275-40fe-becd-121635b7f80c)

## DOWN COUNTER
As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode. down

Three-bit Count Down Counter
![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/ad8e48c4-9aa0-42ed-9b20-02d80061f26a)

## Procedure
1.Create a new project in Quartus II software. 2.Name the project as uc for upcounter and dc for downcounter. 3.Create a new Verilog HDL file in the project file. 4.Name the module as dc and uc for downcounter and upcounter. 5.Within the module declare input and output variables. 6.Complete the program. 7.End the module.

## PROGRAM
## UP COUNTER
module uc(clk, A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

A[2]=(((A[0])&(A[1]))^A[2]);

A[1]=(A[0])^A[1];

A[0]=A[0]^1;

end

endmodule

## DOWN COUNTER
module dc(clk,A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

A[2]=(((~A[0])&(~A[1]))^A[2]);

A[1]=(~A[0])^A[1];

A[0]=1^A[0];

end

## RTL LOGIC UP COUNTER AND DOWN COUNTER
## UP COUNTER

![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/5379dca3-d34f-4db0-b9d5-f2658d20cea1)


## DOWN COUNTER

![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/72850ce6-6c46-40f6-a895-1984d35e67d3)


## TIMING DIGRAMS FOR COUNTER
## UP COUNTER

![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/769b0429-4297-4274-9ab5-fe8a5716322f)


## DOWN COUNTER

![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/4a9dfe25-cefe-4841-b3c8-702dc8a85dc4)


## TRUTH TABLE
## UP COUNTER

![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/b1c913b7-b7ad-42c8-bb5a-4427baf2a210)


## DOWN COUNTER

![image](https://github.com/thamzzz610/Exp-7-Synchornous-counters-/assets/151115849/8f50a58c-8419-4425-b1cc-95cb68fbdc64)


## RESULTS
Thus, the flipflops are implemented using verilog.
