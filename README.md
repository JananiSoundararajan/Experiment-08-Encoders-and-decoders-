```
Name: JANANI S
Register Number: 212222230049
```
# Experiment 07 Encoders and decoders 
### AIM: 
To implement 8 to 3 Encoder and  3to8 Decoder using verilog and validate its outputs
### HARDWARE REQUIRED: 
– PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:  
Quartus prime
### THEORY:

#### Encoders
Binary code of N digits can be used to store 2N distinct elements of coded information. This is what encoders and decoders are used for. Encoders convert 2N lines of input into a code of N bits and Decoders decode the N bits into 2N lines.

1. Encoders –
An encoder is a combinational circuit that converts binary information in the form of a 2N input lines into N output lines, which represent N bit code for the input. For simple encoders, it is assumed that only one input line is active at a time.

As an example, let’s consider Octal to Binary encoder. As shown in the following figure, an octal-to-binary encoder takes 8 input lines and generates 3 output lines.

![image](https://user-images.githubusercontent.com/36288975/171543588-bc0746df-a173-4b35-989e-5fb7d385fe8a.png)
#### Figure -01 3 to 8 Encoder 


Implementation –

X = D4 + D5 + D6 + D7
Y = D2 +D3 + D6 + D7
Z = D1 + D3 + D5 + D7 
Hence, the encoder can be realised with OR gates as follows:


![image](https://user-images.githubusercontent.com/36288975/171543740-68403b82-aa93-4c98-9343-f32b14885a2e.png)
#### Figure -02 3 to 8 Encoder implenentation 

 #### Decoders 
A decoder does the opposite job of an encoder. It is a combinational circuit that converts n lines of input into 2n lines of output.

Let’s take an example of 3-to-8 line decoder.
Implementation –
D0 is high when X = 0, Y = 0 and Z = 0. Hence,

D0 = X’ Y’ Z’ 
Similarly,

D1 = X’ Y’ Z
D2 = X’ Y Z’
D3 = X’ Y Z
D4 = X Y’ Z’
D5 = X Y’ Z
D6 = X Y Z’
D7 = X Y Z 


![image](https://user-images.githubusercontent.com/36288975/171543978-ee2d0671-2846-40a1-8705-507fd6287a49.png)
#### Figure -03 8 to 3 Decoder 



![image](https://user-images.githubusercontent.com/36288975/171543866-5a6eace6-8683-49d7-9c4f-a7cb30ec3035.png)
#### Figure -04 8 to 3 Decoder implementation 

### Procedure:
1. Create a New Project:
   - Open Quartus and create a new project by selecting "File" > "New Project Wizard."
   - Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).

2. Create a New Design File:
   - Once the project is created, right-click on the project name in the Project Navigator and select "Add New File."
   - Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language.

3. Write the Combinational Logic Code:
   - Open the newly created Verilog or VHDL file and write the code for your combinational logic.
     
4. Compile the Project:
   - To compile the project, click on "Processing" > "Start Compilation" in the menu.
   - Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.

5. Analyze and Fix Errors:*
   - If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window.
   - Review and fix any issues in your code if necessary.
   - View the RTL diagram.

6.*Verification:
   - Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF".
   - Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.
   - Give the Input Combinations according to the Truth Table amd then simulate the Output Waveform.



### PROGRAM 
##### Encoder:
```
module encoder(a0,a1,a2,y0,y1,y2,y3,y4,y5,y6,y7);
input y0,y1,y2,y3,y4,y5,y6,y7;
output a0,a1,a2;
or(a0,y7,y5,y3,y1);
or(a1,y7,y6,y3,y2);
or(a2,y7,y6,y5,y4);
endmodule
```
```
module decoder(a0,a1,a2,y0,y1,y2,y3,y4,y5,y6,y7);
input a0,a1,a2;
output y0,y1,y2,y3,y4,y5,y6,y7;
wire a0bar,a1bar,a2bar;
not(a0bar,a0);
not(a1bar,a1);
not(a2bar,a2);
and(y0,a0bar,a1bar,a2bar);
and(y1,a0,a1bar,a2bar);
and(y2,a0bar,a1,a2bar);
and(y3,a0,a1,a2bar);
and(y4,a0bar,a1bar,a2);
and(y5,a0,a1bar,a2);
and(y6,a0bar,a1,a2);
and(y7,a0,a1,a2);
endmodule

```

### RTL DIAGRAM:
#### Encoder-
![Screenshot 2023-11-09 085135](https://github.com/Vanitha-SM/Experiment-08-Encoders-and-decoders-/assets/119557985/91aaa217-95a8-4f94-8101-388c0fe1d27d)
#### Decoder-
![image](https://github.com/Vanitha-SM/Experiment-08-Encoders-and-decoders-/assets/119557985/4c90f4a0-d878-451b-b477-f7833e186af2)






### TRUTH TABLE :
#### Encoder-
![image](https://github.com/Vanitha-SM/Experiment-08-Encoders-and-decoders-/assets/119557985/b79ea793-7269-40c7-b667-f4ec965cd5d8)
#### Decoder:
![image](https://github.com/Vanitha-SM/Experiment-08-Encoders-and-decoders-/assets/119557985/bf5a6369-ab2b-4c83-b91e-84e3c7f6ab22)



### OUTPUT WAVEFORM:
#### Encoder-
![281952786-2a6afac1-4ebf-42e2-a91f-518bee1ba760](https://github.com/JananiSoundararajan/Experiment-08-Encoders-and-decoders-/assets/119477549/c0e153f9-6cb8-4ab7-9af8-35a161586baf)
#### Decoder-
![image](https://github.com/Vanitha-SM/Experiment-08-Encoders-and-decoders-/assets/119557985/a43617b8-1253-4a69-90ee-778cb8b4dd6b)


### RESULT:
Thus the program to design encoder and decoder is executed successfully .
