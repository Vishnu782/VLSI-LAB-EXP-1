# SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS

# AIM: 
  To simulate and synthesis Logic Gates,Adders and Subtractor using VIVADO 2023.1

# APPARATUS REQUIRED: 
   VIVADO 2023.1

# PROCEDURE: 
STEP:1 Open Vivado: Launch Xilinx Vivado software on your computer.

STEP:2 Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

STEP:3 Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

STEP:4 Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

STEP:5 Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

STEP:6 Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

STEP:7 Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

STEP:8 Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

STEP:9 View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# Logic Diagram :

# Logic Gates:
![301405876-ee17970c-3ac9-4603-881b-88e2825f41a4](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/210fdead-78c0-4319-8c8c-6ef2793e55a9)

Full adder:

![301406527-9bb3964c-438f-469d-a3de-c1cca6f323fb](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/12fa98ab-3953-43bd-9077-d8bedc125e3a)

Full Subtractor:

![301406088-d66f874b-c1f2-44b3-a035-7149b56430c1](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/edf1042f-984c-4907-8669-0af863c10446)

Half Adder:

![301406331-0e1ecb96-0c25-4556-832b-aeeedfdfe7b9](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/772ff61e-3689-4804-8c15-6ee9a0abc45b)


Half Subtractor:

![301406051-731470b7-eb4e-49f8-8bb7-2994052a7184](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/81d481fb-74b5-4d43-a03c-fcc2d4b5e1d4)


8 Bit Ripple Carry Adder:

![301406117-7385a408-40a5-4203-8050-b72818622d79](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/14566adb-2024-4e49-98cf-81d0af956a62)


# VERILOG CODE:

 # Full Adder:
``` 
module fulladder (sum, cout, a,b,c);
input a,b,c;
output sum, cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and al(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,w2,w3); or o2(cout,w5,w4);
endmodule
```

# Full Subractor:
```
module full_subtractor(a, b, c,D, Bout);
input a, b, c;
output D, Bout;
assign D = a^b^c;
assign Bout = (a & b) | ((a^ b) & c);
endmodule
```

# Half Adder:
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
or(sum,a,b);
and(carry,a,b);
endmodule
```

# Half Subractor:
```
module half_subtractor(D,Bo,A,B);
input A,B;
output D,Bo;
assign D=A^B;
assign Bo=(~A)&B;
endmodule
```

# Logic Gates:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```

# Ripple Carry Adder 4Bit:
```
module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;// Two 4-bit inputs
input Cin;
output [3:0] S;
output Cout;
wire w1, w2, w3;fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
xor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
```

OUTPUT:
# LOGIC GATES:

![ffb6c0b3-f821-4305-b1ab-1e908f51c047](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/4b0514af-094b-41e1-9583-0d3763b9ae5a)


# FULL ADDER:
![ada504c3-1762-43d4-8d0d-9f255c6b1bb9](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/c08e50f0-b0da-4aa8-bd1f-f81a923aedc1)

# FULL SUBRACTOR:
![1740bc02-7481-4245-80be-ee0f9a17a5bd](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/1e83704b-de9f-48d3-8488-ef786535bd3a)


# HALF ADDER:

![fd2aa6c4-1456-4051-9c7c-a92a0c507a81](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/13e26eb8-a138-4622-9b64-1fd6486d124a)

# HALF SUBRACTOR :

![92e6dc51-575c-4540-90ed-c6545ccaaf09](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/86426486-a292-4a28-808b-d7983ba4040f)

# RIPPLE CARRY ADDER 4 bit:
![314f8699-d5a1-4a40-a768-9d963e5b00c6](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/ea0ae739-f01d-4a0a-9fae-c7d271f86f42)

#  RIPPLE CARRY ADDER 8 bit:
![318389566-5f580fee-30ea-4256-bc0c-1390963ed0b3](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/6b94749a-db5c-4761-b6bc-d570bd361871)

# RTL Design:

Full Adder
![324384779-a00a1428-41f1-419f-9c2c-09a19dc02593](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/3b79ee9f-f434-4dc6-bf8d-941791f6dd77)

Full Subractor
![324384968-6aaf5330-2db0-4045-9357-5ba03e7187ae](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/cfba45ad-4ec3-4742-93f2-73994b5874ca)

Half Adder
![324385052-9599b9cb-8f41-4321-9a66-4c63f99e90d7](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/95e386c8-8d05-4278-a432-ecb12d77f197)

Half Subractor
![324385099-44ef62e2-f75f-467b-bd39-00ed3cad081c](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/b13bdffb-819a-45f5-a710-4ff9cd36b641)


Logic Gates
![324385249-ad868688-74fe-4070-a086-8eb25dfcec8c](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/8cb8785b-5dc3-4a88-957b-a9b56991f3a5)

Ripple Carry Adder 4bit
![324385309-f68c9678-9f0e-4caa-b93f-35261722fe55](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/74ddf258-aa04-4152-b58d-3f6b806ff97a)

Ripple Carry Adder 8bit
![324385352-ca0d8db1-719e-466d-bcf7-0c199390f62a](https://github.com/Vishnu782/VLSI-LAB-EXP-1/assets/102226356/537cb23c-7715-40a2-96ed-98e6587d88d0)

# Result:
Thus the Simulation of Logic Gates ,Adders and Subtractors is done and verified.
