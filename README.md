# ASIC-Design-class
## Lab 1A: Create a small C program and compile it using gcc compiler.Verify the output of the C program after execution.
<details>
  <summary>Click to Open </summary>

Step1: Write the C Code in a file Using any text editor and save it as sum1ton.c(source code).


![2024-07-17 (14)](https://github.com/user-attachments/assets/4d2d6965-6021-4712-b226-601d0c1e8c5d)
![2024-07-17 (16)](https://github.com/user-attachments/assets/cdc76027-8f42-42c8-97b9-a337e80b36dc)

Step2: Now compile the source code using gcc compiler,this will generate the executable code.

![2024-07-17 (17)](https://github.com/user-attachments/assets/0ccf1314-7811-4a9b-b827-bb39adaa89bd)

Step3: Lastly run the executable code to see the output.

![2024-07-17 (18)](https://github.com/user-attachments/assets/a91a1be2-d6d0-4998-9c0a-187adf80448d)

</details>



## Lab 1B: Compiling a c code with RISC-V compiler and using O1 and Ofast.

 <details>
  <summary>Click to Open </summary>

step1: Compile the code using RISC-V GCC

![2024-07-17 (20)](https://github.com/user-attachments/assets/1524a9d4-8bac-4ddc-96bc-3d236a49f10b)

![2024-07-17 (21)](https://github.com/user-attachments/assets/dd8ec7b2-d473-49d4-8728-270074c34124)

Step2: Now put the O1 and Ofast Command and observe the output 


![2024-07-18](https://github.com/user-attachments/assets/7baa5530-8ae6-446e-881e-2f8ca4569655)

![2024-07-18 (6)](https://github.com/user-attachments/assets/0e0290ff-883f-40a4-b84e-4fee7cca445e)

![2024-07-18 (7)](https://github.com/user-attachments/assets/dfbc48ec-27b1-4ee0-96f3-945888665c7b)

![2024-07-18 (9)](https://github.com/user-attachments/assets/b35835eb-7a65-4a8d-a907-02f0262091fe)

 </details>

 
## Lab 2: Execution of the object file created by the RISC-V GCC compiler using Spike Simulator.

<details>
  <summary>Click to Open </summary>

Step1: Firstly we will check that the output using GCC compiler is same as RISC-V GCC compiler and the command we are using for RISC-V GCC compiler is spike pk sum1ton.o
we can see same output in below image now debugging using spike simulator, use spike -d pk sum1ton.o command to enter into debugging mode using spike
This will open a small debuger

![Screenshot 2024-07-20 215028](https://github.com/user-attachments/assets/609b3586-94e8-41d6-89f0-b2043a7b8a2a)

Step2:To load the memory allocation use riscv64-unkown-elf-objdump -d sum1ton.o | less  command in another tab and press enter it will display as shown below

![Screenshot 2024-07-20 225923](https://github.com/user-attachments/assets/bb2c0cf3-8496-48e3-942e-634cb103d7e5)

Step3: Now we want to run our program from memory location 0 to 100b0 and after that we will run it manually step by step and further checking the value of each register.
for this use command until pc 0 100b0 , where pc means program counter

![Screenshot 2024-07-20 215028](https://github.com/user-attachments/assets/f19a0c68-e1ce-4efd-bde3-ccf2270d8dbd)

Step4: Now put reg 0 a0 command.

![Screenshot 2024-07-20 222054](https://github.com/user-attachments/assets/406d0dcf-a9a8-4bb8-bb79-8e048387cc07)

Then press enter this will show the inital contain of register a0 , again press enter this will execute and load the new contains in register a0

![Screenshot 2024-07-20 222901](https://github.com/user-attachments/assets/c24556a4-1bb2-4786-b87b-88d69b98497f)

similarly we can do the same with next registers

lui a0, 0x21 means load upper immediate of a0 register from bit 12 to 31. 

![Screenshot 2024-07-20 223009](https://github.com/user-attachments/assets/7a2389d0-7b5b-488f-a9b4-2daf9b9833ba)

![Screenshot 2024-07-20 223703](https://github.com/user-attachments/assets/98a0339b-d296-4701-9595-30dcce13fbde)

![Screenshot 2024-07-20 224733](https://github.com/user-attachments/assets/31f9db8d-a2d8-46fd-ae18-d967aa19e416)


![Screenshot 2024-07-20 225330](https://github.com/user-attachments/assets/23309af0-bcf0-4af1-a6c0-b563625be5e7)

So in this way we debug our code and load each line manually


</details>





## Lab 3 :Identify various RISC-V instruction types and running assembly instructions according to the provided Verilog code in a RISC-V processor.

<details>
  <summary>TaskA </summary>

## Task A] Identify various RISC-V instruction types
        
  The given instructions are as follows  and we need to identify the type of instruction , write thier binary and hexadecimal equivalent.
    
         
         
         
         ADD r9, r10, r11
         SUB r11, r9, r10
         AND r10, r9, r11
         OR r8, r10, r5
         XOR r8, r9, r4
         SLT r00, r1, r4
         ADDI r02, r2, 5
         SW r2, r0, 4
         SRL r06, r01, r1
         BNE r0, r0, 20
         BEQ r0, r0, 15
         LW r03, r01, 2
         SLL r05, r01, r1

## Various RISC V instruction types are

R-type (Register): Encodes arithmetic and logical operations. The format is funct7 rs2 rs1 funct3 rd opcode.

I-type (Immediate): Used for immediate operations and loads. The format is imm[11:0] rs1 funct3 rd opcode.

S-type (Store): Used for store operations. The format is imm[11:5] rs2 rs1 funct3 imm[4:0] opcode.

B-type (Branch): Used for branch operations. The format is imm[12] imm[10:5] rs2 rs1 funct3 imm[4:1] imm[11] opcode.

U-type (Upper immediate): Used for immediate values for upper immediate operations. The format is imm[31:12] rd opcode.

J-type (Jump): Used for jump operations. The format is imm[20] imm[10:1] imm[11] imm[19:12] rd opcode.




## Decoding the given instruction type wise, the tabular representation of Hexadecimal and 32 bit decimal equivalent is shown below.


| Instruction       | Format | Opcode   | Funct7  | rs2  | rs1  | Funct3 | rd   | Immediate    | 32-bit Binary Encoding                           | Hexadecimal Encoding |
|-------------------|--------|----------|---------|------|------|--------|------|--------------|---------------------------------------------------|-----------------------|
| ADD r9, r10, r11  | R-Type | 0110011  | 0000000 | 01011| 01010| 000    | 01001| -            | `0000000 01010 01011 000 01001 0110011`         | `0x00B292B3`          |
| SUB r11, r9, r10  | R-Type | 0110011  | 0100000 | 01001| 01010| 000    | 01011| -            | `0100000 01010 01001 000 01011 0110011`         | `0x400292B3`          |
| AND r10, r9, r11  | R-Type | 0110011  | 0000000 | 01011| 01001| 111    | 01010| -            | `0000000 01001 01011 111 01010 0110011`         | `0x00B292B3`          |
| OR  r8, r10, r5   | R-Type | 0110011  | 0000000 | 00101| 01010| 110    | 01000| -            | `0000000 01010 00101 110 01000 0110011`         | `0x00A292B3`          |
| XOR r8, r9, r4    | R-Type | 0110011  | 0000000 | 00100| 01001| 100    | 01000| -            | `0000000 01001 00100 100 01000 0110011`         | `0x00A292B3`          |
| SLT r00, r1, r4   | R-Type | 0110011  | 0000000 | 00100| 00001| 010    | 00000| -            | `0000000 00001 00100 010 00000 0110011`         | `0x00129233`          |
| ADDI r02, r2, 5   | I-Type | 0010011  | -       | -    | 00010| 000    | 00010| 000000000101 | `000000000101 00010 000 00010 0010011`         | `0x0002 0203`         |
| LW   r03, r01, 2  | I-Type | 0000011  | -       | -    | 00001| 010    | 00011| 000000000010 | `000000000010 00001 010 00011 0000011`         | `0x0001 0323`         |
| SRL r06, r01, r1  | R-Type | 0010011  | 0000000 | 00001| 00001| 101    | 00110| -            | `0000000 00001 00001 101 00110 0010011`         | `0x0001 5653`         |
| BNE r0, r0, 20    | B-Type | 1100011  | -       | -    | 00000| 001    | 00000| 00000000010100 | `00000000010100 00000 001 00000 1100011`       | `0x0000 A0E3`         |
| BEQ r0, r0, 15    | B-Type | 1100011  | -       | -    | 00000| 000    | 00000| 00000000001111 | `00000000001111 00000 000 00000 1100011`       | `0x0000 0003`         |
| SLL r05, r01, r1  | R-Type | 0110011  | 0000000 | 00001| 00001| 001    | 00101| -            | `0000000 00001 00001 001 00101 0110011`         | `0x0001 2523`         |

</details>


## Task B]: Running assembly instructions according to the provided Verilog code in a RISC-V processor.

<details>
  <summary>TaskB </summary>

For the given verilog code and the instructions, the Bit pattern and the ISA according to the code can be viwed as below

![Inst](https://github.com/user-attachments/assets/aeb227aa-87f5-4b5f-a188-0e680d193f04)


Download the two files iiitb_rv32i.v and iiitb_rv32i_tb.v , save them in same folder and put the below command to execute and run the code.After that put the gtkwave command to get the waveforms.


![terminal](https://github.com/user-attachments/assets/3aaf85f3-4a85-4fce-bf46-5b06a1cae4ff)



Table to show standard risc-v isa and Hardcore isa for each operation :




| **Operation**          | **Standard RISC-V ISA** | **Hardcoded ISA** |
|------------------------|--------------------------|-------------------|
| **ADD R6, R2, R1**    | `32'h00110333`           | `32'h02208300`    |
| **SUB R7, R1, R2**    | `32'h402083b3`           | `32'h02209380`    |
| **AND R8, R1, R3**    | `32'h0030f433`           | `32'h0230a400`    |
| **OR R9, R2, R5**     | `32'h005164b3`           | `32'h02513480`    |
| **XOR R10, R1, R4**   | `32'h0040c533`           | `32'h0240c500`    |
| **SLT R1, R2, R4**    | `32'h0045a0b3`           | `32'h02415580`    |
| **ADDI R12, R4, 5**   | `32'h004120b3`           | `32'h00520600`    |
| **BEQ R0, R0, 15**    | `32'h00000f63`           | `32'h00f00002`    |
| **SW R3, R1, 2**      | `32'h0030a123`           | `32'h00209181`    |
| **LW R13, R1, 2**     | `32'h0020a683`           | `32'h00208681`    |
| **SRL R16, R14, R2**  | `32'h0030a123`           | `32'h00271803`    |
| **SLL R15, R1, R2**   | `32'h002097b3`           | `32'h00208783`    |




## Snapshot of waveform for each instruction is as shown below:


1] ADD R6, R2, R1

![1](https://github.com/user-attachments/assets/8140bd52-29e0-41c5-ad8e-8a60e09dfb77)


2] SUB R7, R1, R2

![2](https://github.com/user-attachments/assets/d7f96808-a62d-4abe-a297-3d07718231a4)


3] AND R8, R1, R3

![3](https://github.com/user-attachments/assets/e333b295-2445-4232-b83f-b9d01654dbe3)



4] OR R9, R2,R5

![4](https://github.com/user-attachments/assets/95447b4f-797d-4ed4-b2ff-5ca5eaab34b5)



5] XOR R10, R1, R4

![5](https://github.com/user-attachments/assets/50be6373-f00c-4982-91dc-b30c82ebf425)



6] SLT R1, R2, R4

![6](https://github.com/user-attachments/assets/6ccfbcbc-6408-4a03-a9da-241a1bdee174)



7] ADDI R12, R4, 5 

![7](https://github.com/user-attachments/assets/97a5caed-aa48-4e2b-8802-4e5bd50de733)



8] BEQ R0, R0, 15 

![8](https://github.com/user-attachments/assets/16ddca02-2508-4f86-803b-fc656779e667)

</details>

## Lab 4: To write an Application in C and compile it with gcc and Risc-v gcc
## Application: Monthly Expenses Tracker

<details>
  <summary>Click to Open </summary>
### Step1] Writing a C program in text editor

![cprogram](https://github.com/user-attachments/assets/17eb2157-2328-4c6b-8fa9-d7885e438060)

### Step2] Compile the program using gcc

![1](https://github.com/user-attachments/assets/481e970f-4fd5-4634-a0d4-befa0a6ee939)

### Step3] Compile the code with O1 and Ofast

## With O1
![2](https://github.com/user-attachments/assets/26713c9c-1191-4cfe-a1d6-35f97bbf37a3)

## With Ofast

![output with ofast](https://github.com/user-attachments/assets/ab23c3ac-0d2f-4675-8878-46ad81dcff8d)

### Step4] Checking the Assembly line code after executing the code with O1 and Ofast

 Use the below command to view the memory allocations 
![3](https://github.com/user-attachments/assets/c2931b81-a1c4-4960-b38a-feadfca94092)

Open new tab and type the following command

![4](https://github.com/user-attachments/assets/a705d9d4-4283-41d9-ba0f-5ca8acf25942)

We can see the memory allocations in the main section
![5(mem with O1)](https://github.com/user-attachments/assets/502c711d-9b7a-4274-b485-d5aa13add8b5)

Similarly for Ofast , the memory allocations can be viewed as-

![6(ofast)](https://github.com/user-attachments/assets/0a0a5cfc-3254-449d-a72a-976d24db751b)

Memory allocations using Ofast
![6(mem with Ofast)](https://github.com/user-attachments/assets/cede2457-bb9a-4bb4-9d2d-5e6c7515b4a8)

## Step5] Use spike simulator to debug the code

open debugger use spike -d pk todolist.c command and to execute from 0 to first address of main section use until pc 0 100b0 then press enter to check each execution one by one.

![spike dump](https://github.com/user-attachments/assets/c8e9888f-df75-4276-95ad-f6c92f305455)


### Below pic represents all compiles in a single frame.
![8all](https://github.com/user-attachments/assets/874ac3e5-4b21-4cec-8256-ed4ad89a297d)

## Conclusion: It is observed that all the three compilers(i.e gcc, O1, Ofast) resulted in same output for an application Monthly Expenses Tracker.

</details>

## Lab 5:To design a Baisc Risc-V processor core using TL-Verilog on Makerchip.

<details>
  <summary>Click to Open </summary>

  
Using the Makerchip platform, the implementation of a RISC-V microarchitecture or core is carried out. To begin the implementation, starter code available in the reference is utilized.The basic duilding blocks are-
* A simple RISC-V assembler.
* An instruction memory containing the sum 1..9 test program.
* Commented code for register file and memory.
* Visualization.

The given shell code is:
```c
\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;



      // YOUR CODE HERE
      // ...

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      //m4+imem(@1)    // Args: (read stage)
      //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)

   //m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule
```

![1(shellcode)](https://github.com/user-attachments/assets/d640e821-6ba5-457a-9bfe-f7db70c36cad)

## Fetch and Decode


### The Clk name clk_tus can be seen in below pic
![2(mem)](https://github.com/user-attachments/assets/fd441b03-e721-4e6c-b9da-a6e7cf5d2987)


![3(instr fetch with waveform)](https://github.com/user-attachments/assets/a2f95209-2c11-459e-843b-0f4070b90965)


To accurately decode a specific instruction, the processor must be aware of its type and format. Proper decoding is essential and must adhere to the specified format to prevent errors. In RISC-V, there are six instruction types:

* Register (R) type
* Immediate (I) type
* Store (S) type
* Branch (B) type
* Upper immediate (U) type
* Jump (J) type


![3(InstrTypes)](https://github.com/user-attachments/assets/d9e94264-46c6-4548-b283-80e77774e50f)

Instruction immediate value decode 

![4(Imm_Decode)](https://github.com/user-attachments/assets/e3e92b0e-9e5a-41ff-b844-b173ab9d1f2c)

![17(Viz)](https://github.com/user-attachments/assets/aca0e71d-efa9-4c13-8d22-9543c8a10b86)


Decoding the remaining fields of an instruction, such as source and destination registers, funct, and opcode, requires using valid methods and techniques.

![5(Valid)](https://github.com/user-attachments/assets/1bf59b7e-74f5-4993-81ec-a89daaff813d)



![6(Base Instr set)](https://github.com/user-attachments/assets/a9a050d7-e30e-4557-83dc-9604a243279e)

## Execute and Register file read/write
The subsequent task involves performing 'read' and 'write' operations on the registers. During this process, two read and write operations can occur simultaneously. The values from src1 and src2 are obtained from the two read registers, rf_read_data1 and rf_read_data2, and are passed to the ALU unit. Currently, the ADDI and ADD instructions are executed, with the result being stored in the rf_write_data register. The diagram below illustrates the input and output registers.


![7(Reg file Read)](https://github.com/user-attachments/assets/e41452bd-92ce-41c7-845f-37b29dd50b38)


![8(Ref read cont)](https://github.com/user-attachments/assets/76aae5e0-cff2-4b95-9ba7-db700896390f)

## Adding an ALU

![12 (ALU)](https://github.com/user-attachments/assets/8dfeeae1-db00-4e45-b27d-e2cc841b4807)


![12(ALU with Result)](https://github.com/user-attachments/assets/7e2da2de-48f7-4bc2-981b-7a7cb12509cf)


## Register File Write

![13(Reg file read)](https://github.com/user-attachments/assets/f1e26bc5-d199-4d71-a5aa-8aea1fd5eeb8)


![13(Reg file with waveform)](https://github.com/user-attachments/assets/2af1ac32-ffb7-4ba1-8382-aa4078386967)


## Implementing Branch Instructions

The next step in developing the RISC-V microarchitecture is incorporating branch instructions. Beyond immediate additions or simple arithmetic, certain conditions may need to be met to redirect the PC to a branch target address. At this stage, a few branch instructions have been added, and the PC has been updated accordingly. Some of these branch instructions include:

* BEQ: ==
* BNE: !=
* BLT: (x1 < x2) ^ (x1[31] != x2[31])
* BGE: (x1 >= x2) ^ (x1[31] != x2[31])
* BLTU: <
* BGEU: >=

![14(Branch inst)](https://github.com/user-attachments/assets/61ed15f0-c268-468f-8512-4427c2a2dafd)


![14(Branch inst with waveform)](https://github.com/user-attachments/assets/c35ea895-1eff-4454-8bed-ef2526c296a0)


## Applying Testbench

To pass the testbench use  *passed = |cpu/xreg[10]>>5$value == (1+2+3+4+5+6+7+8+9) ;

In the following snapshot we can see that the testbench has been successfully implemented. This can be confirmed by checking the LOG terminal for verification.

![log](https://github.com/user-attachments/assets/99e4d6cf-81ed-42d0-9efd-4f292d5bc4dc)

# Complete Pipelined RiscV CPU Micro-architecture

Pipelining the CPU

CPU core pipelining has now been implemented, enabling smoother retiming and significantly reducing functional bugs. Pipelining improves computation speed. To implement pipelining, we just need to add @1, @2, and so forth.




Final Pipelined Output:-

IT can be seen the values in the different registers on the viz tab. The following image shows the 2nd clock cycle.
![clk cycle2](https://github.com/user-attachments/assets/3523e08c-d3b3-4299-bc74-9511dcce9cd0)

Similar to the previous cycle, we can step through various clock cycles and observe the updated results in the registers. In our code, we are incrementally adding values from 1 to 9 and monitoring the final output in the registers. It took 53 cycles for the register r14 to get updated to the value 45.
![53th cycle](https://github.com/user-attachments/assets/8f883a2e-464f-4996-93f5-17c371473239)






The execution of the full code takes 59 cycles including the load and the store operations.
![59 cycles](https://github.com/user-attachments/assets/a74fe30b-bae9-4b0f-ab7a-154f67f00fe6)




The following image shows the clock signal which contains my name clk_tus
![Screenshot 2024-08-21 161946](https://github.com/user-attachments/assets/cc6659ac-1e98-44ca-a924-b2fd2bf7f7db)

The following image shows the reset signal
![Reset signal](https://github.com/user-attachments/assets/aeb29a56-9e69-492b-8327-f96c7506b0d2)



The following image shows the gradual addition of the in the r14 register
![reg14](https://github.com/user-attachments/assets/d8292e02-0f09-416b-845a-ea25ff8c391a)




The following is the final block diagram of the processor designed
![Screenshot 2024-08-21 162303](https://github.com/user-attachments/assets/d8145bf5-fc0a-47e1-b36c-a8b93af507d1)

Code-

```c
\m4_TLV_version 1d: tl-x.org
\SV
   // Template code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   m4_asm(SW, r0, r10, 10000)           // Store r10 result in dmem
   m4_asm(LW, r17, r0, 10000)           // Load contents of dmem to r17
   m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
         $clk_tus = *clk;
         
         //PC fetch - branch, jumps and loads introduce 2 cycle bubbles in this pipeline
         $pc[31:0] = >>1$reset ? '0 : (>>3$valid_taken_br ? >>3$br_tgt_pc :
                                       >>3$valid_load     ? >>3$inc_pc[31:0] :
                                       >>3$jal_valid      ? >>3$br_tgt_pc :
                                       >>3$jalr_valid     ? >>3$jalr_tgt_pc :
                                                     (>>1$inc_pc[31:0]));
         // Access instruction memory using PC
         $imem_rd_en = ~ $reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         
         
      @1
         //Getting instruction from IMem
         $instr[31:0] = $imem_rd_data[31:0];
         
         //Increment PC
         $inc_pc[31:0] = $pc[31:0] + 32'h4;
         
         //Decoding I,R,S,U,B,J type of instructions based on opcode [6:0]
         //Only [6:2] is used here because this implementation is for RV64I which does not use [1:0]
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] == 5'b11001;
         
         $is_r_instr = $instr[6:2] == 5'b01011 ||
                       $instr[6:2] ==? 5'b011x0 ||
                       $instr[6:2] == 5'b10100;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         
         $is_b_instr = $instr[6:2] == 5'b11000;
         
         $is_j_instr = $instr[6:2] == 5'b11011;
         
         //Immediate value decode
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}} , $instr[30:20]} :
                      $is_s_instr ? { {21{$instr[31]}} , $instr[30:25] , $instr[11:8] , $instr[7]} :
                      $is_b_instr ? { {20{$instr[31]}} , $instr[7] , $instr[30:25] , $instr[11:8] , 1'b0} :
                      $is_u_instr ? { $instr[31] , $instr[30:12] , { 12{1'b0}} } :
                      $is_j_instr ? { {12{$instr[31]}} , $instr[19:12] , $instr[20] , $instr[30:21] , 1'b0} :
                      >>1$imm[31:0];
         
         //Generate valid signals for each instruction fields
         $rs1_or_funct3_valid    = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         $rs2_valid              = $is_r_instr || $is_s_instr || $is_b_instr;
         $rd_valid               = $is_r_instr || $is_i_instr || $is_u_instr || $is_j_instr;
         $funct7_valid           = $is_r_instr;
         
         //Decode other fields of instruction - source and destination registers, funct, opcode
         ?$rs1_or_funct3_valid
            $rs1[4:0]    = $instr[19:15];
            $funct3[2:0] = $instr[14:12];
         
         ?$rs2_valid
            $rs2[4:0]    = $instr[24:20];
         
         ?$rd_valid
            $rd[4:0]     = $instr[11:7];
         
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
         
         $opcode[6:0] = $instr[6:0];
         
         //Decode instruction in subset of base instruction set based on RISC-V 32I
         $dec_bits[10:0] = {$funct7[5],$funct3,$opcode};
         
         //Branch instructions
         $is_beq   = $dec_bits ==? 11'bx_000_1100011;
         $is_bne   = $dec_bits ==? 11'bx_001_1100011;
         $is_blt   = $dec_bits ==? 11'bx_100_1100011;
         $is_bge   = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu  = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu  = $dec_bits ==? 11'bx_111_1100011;
         
         //Jump instructions
         $is_auipc = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal   = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr  = $dec_bits ==? 11'bx_000_1100111;
         
         //Arithmetic instructions
         $is_addi  = $dec_bits ==? 11'bx_000_0010011;
         $is_add   = $dec_bits ==  11'b0_000_0110011;
         $is_lui   = $dec_bits ==? 11'bx_xxx_0110111;
         $is_slti  = $dec_bits ==? 11'bx_010_0010011;
         $is_sltiu = $dec_bits ==? 11'bx_011_0010011;
         $is_xori  = $dec_bits ==? 11'bx_100_0010011;
         $is_ori   = $dec_bits ==? 11'bx_110_0010011;
         $is_andi  = $dec_bits ==? 11'bx_111_0010011;
         $is_slli  = $dec_bits ==? 11'b0_001_0010011;
         $is_srli  = $dec_bits ==? 11'b0_101_0010011;
         $is_srai  = $dec_bits ==? 11'b1_101_0010011;
         $is_sub   = $dec_bits ==? 11'b1_000_0110011;
         $is_sll   = $dec_bits ==? 11'b0_001_0110011;
         $is_slt   = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu  = $dec_bits ==? 11'b0_011_0110011;
         $is_xor   = $dec_bits ==? 11'b0_100_0110011;
         $is_srl   = $dec_bits ==? 11'b0_101_0110011;
         $is_sra   = $dec_bits ==? 11'b1_101_0110011;
         $is_or    = $dec_bits ==? 11'b0_110_0110011;
         $is_and   = $dec_bits ==? 11'b0_111_0110011;
         
         //Store instructions
         $is_sb    = $dec_bits ==? 11'bx_000_0100011;
         $is_sh    = $dec_bits ==? 11'bx_001_0100011;
         $is_sw    = $dec_bits ==? 11'bx_010_0100011;
         
         //Load instructions - support only 4 byte load
         $is_load  = $dec_bits ==? 11'bx_xxx_0000011;
         
         $is_jump = $is_jal || $is_jalr;
         
      @2
         //Get Source register values from reg file
         $rf_rd_en1 = $rs1_or_funct3_valid;
         $rf_rd_en2 = $rs2_valid;
         
         $rf_rd_index1[4:0] = $rs1[4:0];
         $rf_rd_index2[4:0] = $rs2[4:0];
         
         //Register file bypass logic - data forwarding from ALU to resolve RAW dependence
         $src1_value[31:0] = $rs1_bypass ? >>1$result[31:0] : $rf_rd_data1[31:0];
         $src2_value[31:0] = $rs2_bypass ? >>1$result[31:0] : $rf_rd_data2[31:0];
         
         //Branch target PC computation for branches and JAL
         $br_tgt_pc[31:0] = $imm[31:0] + $pc[31:0];
         
         //RAW dependence check for ALU data forwarding
         //If previous instruction was writing to reg file, and current instruction is reading from same register
         $rs1_bypass = >>1$rf_wr_en && (>>1$rd == $rs1);
         $rs2_bypass = >>1$rf_wr_en && (>>1$rd == $rs2);
         
      @3
         //ALU
         $result[31:0] = $is_addi  ? $src1_value +  $imm :
                         $is_add   ? $src1_value +  $src2_value :
                         $is_andi  ? $src1_value &  $imm :
                         $is_ori   ? $src1_value |  $imm :
                         $is_xori  ? $src1_value ^  $imm :
                         $is_slli  ? $src1_value << $imm[5:0]:
                         $is_srli  ? $src1_value >> $imm[5:0]:
                         $is_and   ? $src1_value &  $src2_value:
                         $is_or    ? $src1_value |  $src2_value:
                         $is_xor   ? $src1_value ^  $src2_value:
                         $is_sub   ? $src1_value -  $src2_value:
                         $is_sll   ? $src1_value << $src2_value:
                         $is_srl   ? $src1_value >> $src2_value:
                         $is_sltu  ? $sltu_rslt[31:0]:
                         $is_sltiu ? $sltiu_rslt[31:0]:
                         $is_lui   ? {$imm[31:12], 12'b0}:
                         $is_auipc ? $pc + $imm:
                         $is_jal   ? $pc + 4:
                         $is_jalr  ? $pc + 4:
                         $is_srai  ? ({ {32{$src1_value[31]}} , $src1_value} >> $imm[4:0]) :
                         $is_slt   ? (($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]}):
                         $is_slti  ? (($src1_value[31] == $imm[31]) ? $sltiu_rslt : {31'b0, $src1_value[31]}) :
                         $is_sra   ? ({ {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0]) :
                         $is_load  ? $src1_value +  $imm :
                         $is_s_instr ? $src1_value + $imm :
                                    32'bx;
         
         $sltu_rslt[31:0]  = $src1_value <  $src2_value;
         $sltiu_rslt[31:0] = $src1_value <  $imm;
         
         //Jump instruction target PC computation
         $jalr_tgt_pc[31:0] = $imm[31:0] + $src1_value[31:0]; 
         
         //Branch resolution
         $taken_br = $is_beq ? ($src1_value == $src2_value) :
                     $is_bne ? ($src1_value != $src2_value) :
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bge ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bltu ? ($src1_value < $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     1'b0;
         
         //Current instruction is valid if one of the previous 2 instructions were not (taken_branch or load or jump)
         $valid = ~(>>1$valid_taken_br || >>2$valid_taken_br || >>1$is_load || >>2$is_load || >>2$jump_valid || >>1$jump_valid);
         
         //Current instruction is valid & is a taken branch
         $valid_taken_br = $valid && $taken_br;
         
         //Current instruction is valid & is a load
         $valid_load = $valid && $is_load;
         
         //Current instruction is valid & is jump
         $jump_valid = $valid && $is_jump;
         $jal_valid  = $valid && $is_jal;
         $jalr_valid = $valid && $is_jalr;
         
         //Destination register update - ALU result or load result depending on instruction
         $rf_wr_en = (($rd != '0) && $rd_valid && $valid) || >>2$valid_load;
         $rf_wr_index[4:0] = $valid ? $rd[4:0] : >>2$rd[4:0];
         $rf_wr_data[31:0] = $valid ? $result[31:0] : >>2$ld_data[31:0];
         
      @4
         //Data memory access for load, store
         $dmem_addr[3:0]     =  $result[5:2];
         $dmem_wr_en         =  $valid && $is_s_instr;
         $dmem_wr_data[31:0] =  $src2_value[31:0];
         $dmem_rd_en         =  $valid_load;
         
      
         //Write back data read from load instruction to register
         $ld_data[31:0]      =  $dmem_rd_data[31:0];
         
      
      

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   //Checks if sum of numbers from 1 to 9 is obtained in reg[17] and runs 10 cycles extra after this is met
   *passed = |cpu/xreg[17]>>10$value == (1+2+3+4+5+6+7+8+9);
   //Run for 200 cycles without any checks
   //*passed = *cyc_cnt > 200;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)
   
   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic
                       // @4 would work for all labs
\SV
   endmodule
   ```
</details>

## Lab 6:Convert the TLV to verilog using Sandpiper and then use GTKWave pre-synthesis simulation to verify the design.

<details>
  <summary>Click to Open </summary>
  
### The RISC-V processor was developed using TL-Verilog within the Makerchip IDE. To deploy it on an FPGA, the design had to be translated into Verilog, a task accomplished using the Sandpiper-SaaS compiler. Afterward, pre-synthesis simulations were carried out utilizing the GTKWave simulator.


### 1]Install These Required Packages:

```c
python3-pip git iverilog gtkwave
cd ~
sudo apt-get install python3-venv
python3 -m venv .venv
source ~/.venv/bin/activate
pip3 install pyyaml click sandpiper-saas
```

### 2]Inorder to get verilog code of our TLV code ie, to translate .tlv definition of RISC-V into .v definition use the following code.
```c
$ sandpiper-saas -i ./src/module/rvmyth.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```

![Screenshot from 2024-08-26 22-11-38](https://github.com/user-attachments/assets/cac8a0bc-c436-481b-93e8-6f4a623bc351)


### 3]Now to compile and simulate RISC-V design run the following code.
![Screenshot from 2024-08-26 22-12-07](https://github.com/user-attachments/assets/8dc6ca3c-26be-4d0c-9fec-7663f27ee310)

![Screenshot from 2024-08-26 22-12-27](https://github.com/user-attachments/assets/3c904e1a-29fa-4ce2-aa40-52e1acf6d791)

### 4]To open the .vcd simulation file through GTKWave simulation tool use the below command
![Screenshot from 2024-08-26 23-10-55](https://github.com/user-attachments/assets/1d02bdd4-41f8-4106-9f6d-1bdd598a2867)

### 5]Pre-synthesis Simulation results: Signals to plot are the following:

  * clk_tus: This is the clock input to the RISC-V core.
  * reset: This is the input reset signal to the RISC-V core.
  * OUT[9:0]: This is the 10-bit output [9:0] OUT port of the RISC-V core. 

### 6]GTKWave Simulation waveforms:

* The following image shows the clock signal which contains my name clk_tus
![Screenshot from 2024-08-26 22-27-03](https://github.com/user-attachments/assets/cf7cba0b-5c4b-4f74-a5a9-050446541e09)

* The following image shows the reset signal
![Screenshot from 2024-08-26 22-27-19](https://github.com/user-attachments/assets/e97199a6-68c5-49fc-b3fc-7f003eedc6c3)

* The following image shows the gradual addition in OUT[9:0]
 ![Screenshot from 2024-08-26 22-27-41](https://github.com/user-attachments/assets/a4c7cb39-84fe-4206-99f1-e571766b4bfa)

 ![Screenshot from 2024-08-26 22-30-07](https://github.com/user-attachments/assets/b7b215ba-fb49-48c8-9bca-4e80c2578874)

* Makerchip IDE simulation result for comparison
![reg14](https://github.com/user-attachments/assets/d8292e02-0f09-416b-845a-ea25ff8c391a)

</details>

## Lab 7:Addition of Peripherals to convert the Digital output to analog output using DAC and PLL


<details>
  <summary>Click to Open </summary>

## In this task, we're integrating two peripherals to transform digital signals into analog outputs: the Phase-Locked Loop (PLL) and the Digital-to-Analog Converter (DAC).

* Phase-Locked Loop (PLL): The board features a crystal oscillator that provides a clock signal with a frequency ranging from 12 to 20 MHz. However, the processor operates at a frequency close to 100 MHz. To bridge this gap, we need a peripheral like the PLL to convert the low-frequency clock from the crystal oscillator into a higher frequency clock that matches the processor's requirements. Essentially, the PLL takes the input from the crystal oscillator and outputs a high-frequency clock signal suitable for the RISC-V core.This clock is then appended by my name CPU_clk_tus_a0

* Digital-to-Analog Converter (DAC): While the processor operates using digital signals, many communication systems require analog signals for transmission or reception. To address this, we use the Digital-to-Analog Converter (DAC) peripheral. This IP converts the digital output from our RISC-V core into an analog signal, allowing us to interface with systems that rely on analog communication.

Commands used to run the rvmyth.v file
```c
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
```

![Screenshot from 2024-09-02 10-12-15](https://github.com/user-attachments/assets/23f481b1-61fc-4670-8509-624f1594559c)

After this we dump the ./pre_synth_sim.out file to create the .vcd file using the following command
```c
./pre_synth_sim.out
```

![Screenshot from 2024-09-02 10-13-10](https://github.com/user-attachments/assets/1a6e680b-f446-4cc3-8f1e-94ee823828f9)

We then run this .vcd file on gtkwave to observe the output
```c
gtkwave pre_synth_sim.vcd
```

![Screenshot from 2024-09-02 10-33-42](https://github.com/user-attachments/assets/a3a0d707-d49f-40a5-b743-24cef4d6a200)


The output is observed as ashown below
![Screenshot from 2024-09-02 10-38-59](https://github.com/user-attachments/assets/1716c3c5-f0c5-4a1a-a64a-ebbda3877c7c)


After zooming out we can see the Analog waveform clearly
![Screenshot from 2024-09-03 19-25-25](https://github.com/user-attachments/assets/def69d7f-1546-410d-b526-3b4dcc335d10)

![Screenshot from 2024-09-03 19-25-36](https://github.com/user-attachments/assets/311d181b-946e-4f07-b9ad-db8e1c56717d)


</details>

## Lab8:Introduction to Verilog RTL Design and Synthesis

<details>
  <summary>Day1 </summary>
  
### Firstly we need to intall the required files and clone the git repository

## LAB 1:Installing the Files


![Screenshot from 2024-10-17 22-12-28](https://github.com/user-attachments/assets/1803f3c0-da0b-4edb-810f-2e214d93856e)

![Screenshot from 2024-10-17 22-13-08](https://github.com/user-attachments/assets/e09281a9-b3b7-4bd8-a69d-363afa77875b)


![Screenshot from 2024-10-17 22-13-24](https://github.com/user-attachments/assets/0b15913c-64fa-42e0-94da-86f46fc51843)


![Screenshot from 2024-10-17 22-33-50](https://github.com/user-attachments/assets/84370556-22fd-48bf-a273-6f01a44d66b5)

![Screenshot from 2024-10-17 22-39-14](https://github.com/user-attachments/assets/2866f9b6-867e-4c45-b832-8dc101842f50)

## LAB 2:Simulating one of the code using Iverilog and Gtkwave



Here we have simulated good_mux.v and viewed the waveform in gtkwave:
![Screenshot from 2024-10-17 22-55-54](https://github.com/user-attachments/assets/9f3681b9-70c5-413e-93b7-b00685cac79f)


Output Waveform:
![Screenshot from 2024-10-17 22-56-53](https://github.com/user-attachments/assets/8c123d3a-89de-4922-936f-1b2b10a8a43b)

## Following is the code and testbench
![Screenshot from 2024-10-17 23-41-20](https://github.com/user-attachments/assets/0078c2dc-d349-4304-a6b1-14dabfce38e2)

# Synthesizer:
A synthesizer plays a vital role in digital design by transforming RTL (Register Transfer Level) code into a gate-level netlist. This netlist provides a detailed blueprint of the circuit, outlining logical gates and their interconnections, preparing it for physical design steps such as place and route. In this process, Yosys serves as the synthesis tool, functioning as an open-source framework for synthesizing Verilog HDL. Yosys applies several optimization strategies to generate a more efficient gate-level representation from the RTL code.
![1](https://github.com/user-attachments/assets/99dd31d8-1471-4bc0-86d3-b32fb23efa3f)
![2](https://github.com/user-attachments/assets/b592d59b-3932-4c0e-bb08-916fbac4802b)




## Logic Synthesis:
* RTL code describes the design in terms of data flow and operations, providing a more abstract and human-friendly representation. To convert this abstract description into an actual circuit, a process called synthesis is used. During synthesis, the RTL code is transformed into a netlist, a detailed representation composed of basic logic gates like AND, OR, and NOT, along with their connections. This gate-level netlist outlines the circuit's structure, making it ready for physical implementation.


* Synthesis is essential because while RTL code is easy for humans to understand, it isn’t suitable for direct hardware fabrication. The netlist generated after synthesis can be utilized for subsequent steps such as place and route, where the logic gates are arranged on the chip and interconnected. Following synthesis, additional tools can verify whether the design satisfies timing requirements, area limitations, and power constraints. Without synthesis, transitioning from a high-level description to a manufacturable circuit would not be feasible.

## Need of Faster cells
* Faster cells are needed to reduce the combinational delay, which dictates the maximum operating speed of a digital circuit. By using faster cells, logic computations can be completed more quickly, ensuring that the output is ready before the arrival of the next clock cycle. This allows the circuit to function efficiently at higher frequencies.


* Reducing the delay also ensures that the required setup time is met, meaning the data is stable and valid before the clock edge, thus avoiding timing violations. Consequently, incorporating faster cells helps achieve better performance and higher clock speeds in the digital design.

## Setup time:
Setup time refers to the minimum duration before a clock edge during which the input signal (data) to a flip-flop or latch must stay constant. If the data changes during this interval, the flip-flop may fail to capture the correct value, resulting in timing violations. In essence, the data needs to be stable and available for a specified period before the clock activates the flip-flop.


![4](https://github.com/user-attachments/assets/8eb2e65c-6c3c-4c0b-bbf7-7e780d0f5b88)



## Need of Slower Cells
Slower cells are necessary to avoid hold time violations and ensure that the logic is captured correctly following the clock edge. The data must remain stable for a specified hold time, and if the gates operate too quickly, it can result in data changes occurring too soon after the clock signal, causing hold time issues. Thus, using slower cells helps maintain the required timing stability for proper circuit operation.

## Hold time:
Hold time refers to the minimum duration after the clock edge during which the input signal (data) must stay unchanged. If the data changes too quickly following the clock edge, the flip-flop may fail to latch the data correctly. Ensuring the data remains stable for this period prevents any premature alterations immediately after the clock triggers the latch or flip-flop.

![5](https://github.com/user-attachments/assets/2b30ed33-d50e-4c58-958e-471852807443)

## Lab-3: Introduction to Yosys:

To open the yosys give the command yosys
![Screenshot from 2024-10-18 21-59-29](https://github.com/user-attachments/assets/160202cc-5a9a-447b-943f-268031907528)


![Screenshot from 2024-10-18 21-59-46](https://github.com/user-attachments/assets/23358954-c331-4283-b4f3-591e7afa3955)


![Screenshot from 2024-10-18 22-00-29](https://github.com/user-attachments/assets/b761b9bc-4202-48ab-855e-314925ae32d2)


![Screenshot from 2024-10-18 22-00-47](https://github.com/user-attachments/assets/182b2c09-8c25-45d7-ad8f-6e15060619eb)

## To convert RTL into Netlist

use the command:    _abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib_
![Screenshot from 2024-10-19 11-03-51](https://github.com/user-attachments/assets/14a5e852-fdb3-43b1-92b3-9e39db1a78a5)




To view the netlist use the command show
![Screenshot from 2024-10-19 11-04-16](https://github.com/user-attachments/assets/1f6dd3c3-d735-4820-a81b-7cd3cd0e15d6)


After giving this command a new window will open showing Netlist:
![Screenshot from 2024-10-19 11-07-31](https://github.com/user-attachments/assets/522109be-0e06-4489-bb5e-d02ae8c9748f)

To observe the Netlist use the command:    _write_verilog good_mux_netlist.v_
![Screenshot from 2024-10-19 11-20-41](https://github.com/user-attachments/assets/4e50501d-05ac-403e-9460-586e0443ef95)


![Screenshot from 2024-10-19 11-21-25](https://github.com/user-attachments/assets/3a7343b8-3ad6-4171-a046-00df1e3a314e)



After giving:   _!gvim  good_mux_netlist.v_   command another window will open 
![Screenshot from 2024-10-19 11-21-39](https://github.com/user-attachments/assets/fa5cea39-64eb-4e86-be22-b7ac0e459874)

To view it more presicely use the command:   write_verilog -noattr good_mux_netlist.v
![Screenshot from 2024-10-19 11-43-02](https://github.com/user-attachments/assets/c2866f15-f609-4398-a359-22d13947369e)

Below window will open
![Screenshot from 2024-10-19 11-53-26](https://github.com/user-attachments/assets/7031bfa9-1efc-419b-8a6a-5f7161738e6b)




</details>

<details>
  <summary>Day2 </summary>
  
# Hierarchical synthesis and flat synthesis

* Hierarchical Netlist: The design is structured with different modules, where each module may contain other sub-modules, creating a tree-like hierarchy.
  
## Command Used are
  
```c 
sudo -i
cd /home/tushar-katole/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show multiple_modules
write_verilog -noattr multiple_modules_hier.v
!gvim multiple_modules_hier.v

```

Sequentially after giving above command we obtain the below results
![Screenshot from 2024-10-19 19-56-13](https://github.com/user-attachments/assets/0522e67e-4c65-44b1-af1e-deffc56ec140)

![Screenshot from 2024-10-19 19-56-50](https://github.com/user-attachments/assets/b1b9a222-a01c-420d-8b0f-aa1d21ef8630)

![Screenshot from 2024-10-19 19-56-57](https://github.com/user-attachments/assets/8db52675-cc1d-4a5f-8fbe-f48ab91bd99c)


![Screenshot from 2024-10-19 19-57-11](https://github.com/user-attachments/assets/2610d4d3-6bb6-41d8-88f1-3b5fac8a1dcd)

  
![Screenshot from 2024-10-19 19-57-38](https://github.com/user-attachments/assets/03e239b6-e557-43e2-8bc2-81d4f1f93013)


The generated Netlist is obtained as shown below
![Screenshot from 2024-10-19 20-02-12](https://github.com/user-attachments/assets/1f3c3e79-577c-466a-868f-0dde3d14feb5)


![Screenshot from 2024-10-19 19-57-49](https://github.com/user-attachments/assets/889909de-c498-418f-b0ac-9443e3ea9707)


After giving the command  ``!gvim multiple_modules_hier.v`` below window is obtained
![Screenshot from 2024-10-19 20-01-42](https://github.com/user-attachments/assets/207cf20a-afe9-4231-9abf-5f1cf5a38716)

![Screenshot from 2024-10-19 20-01-50](https://github.com/user-attachments/assets/9ea05dfd-f13e-4ce9-a1aa-52906ec8c06f)

## Flatten

* Flat Netlist: All the modules and sub-modules are merged into a single level, and all connections between modules are explicitly defined without any hierarchy.

Use the command ``flatten`` as shown below
![Screenshot from 2024-10-19 20-30-40](https://github.com/user-attachments/assets/fb138397-7916-40e3-beeb-6f3845a58fb7)


Netlist can be generated using ``write_verilog multiple_modules_flat.v``
![Screenshot from 2024-10-19 20-30-57](https://github.com/user-attachments/assets/0a9294e1-2d48-4209-9758-0d1d8e6f6f38)


![Screenshot from 2024-10-19 20-31-25](https://github.com/user-attachments/assets/b4c67581-7327-4883-ba6e-6b049ced5e2e)


![Screenshot from 2024-10-19 20-31-31](https://github.com/user-attachments/assets/35b29990-33a6-4370-82bb-7ae69370fe2c)


## Comparing Hierarchical vs. Flat Netlist

We can observe that sub-module1 and sub-module2 are not generated in flatten netlist
![Screenshot from 2024-10-19 20-32-58](https://github.com/user-attachments/assets/e6412d46-93ab-4a74-9ed0-61ec0059aea6)

The structure after flatten is shown below (use command ``show``)

![Screenshot from 2024-10-19 23-40-14](https://github.com/user-attachments/assets/f19aa877-c15a-42bc-a224-a50d6515ac1f)

## Module Level Synthesis

### Below are the benifis of module level synthesis

* Improved Design Management: Allows easier debugging, optimization, and maintenance by breaking down complex designs into smaller, manageable parts.
* Enhanced Reusability: Enables reuse of independently synthesized modules across multiple projects, saving time and effort.
* Faster Synthesis Times: Reduces synthesis time by handling smaller, individual modules rather than the entire design at once.
* Optimized Resource Usage: Allows targeted optimization of individual modules for performance or area constraints, improving overall efficiency.
* Enables Incremental Synthesis: Only modified modules need to be resynthesized after changes, speeding up iterative development.

Read the files similar to the earlier steps and use ``synth -top sub_module1``
![Screenshot from 2024-10-19 23-58-10](https://github.com/user-attachments/assets/66658a11-d6e4-4877-b730-1e9c8d3303bf)

Use the command ``show`` to view the structure(it shows only AND gate i.e only one module)
![Screenshot from 2024-10-20 00-00-36](https://github.com/user-attachments/assets/ae284800-7161-4803-a7a1-1d0f77a328b3)


# Usage of Flops: Synchronous and Asynchronous D_FFs

## Asynchronous Reset

Simulating using iverilog and Gtkwave
Command used are
```c
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
gtkwave tb_dff_asyncres.vcd
```

![Screenshot from 2024-10-20 00-53-34](https://github.com/user-attachments/assets/29bb7869-177d-40bb-b177-fd080e8363af)

### GtkWave output:We can see that here q changes to zero when reset goes high irrespective of clock edge
![Screenshot from 2024-10-20 00-53-55](https://github.com/user-attachments/assets/452a1034-a4e7-4a30-8f69-bf51b109c2ba)


## Asynchronous Set

Simulating using iverilog and Gtkwave
Command used are
```c
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
gtkwave tb_dff_async_set.vcd
```

![Screenshot from 2024-10-20 01-08-01](https://github.com/user-attachments/assets/cd96b46a-9cc1-4385-b9ec-b16646332a15)



### GtkWave output:We can see that here q changes to one when asynchronous set goes high irrespective of clock edge 
![Screenshot from 2024-10-20 01-08-52](https://github.com/user-attachments/assets/c7f9ba5b-eae4-484b-81d8-21720f6aab41)


## Synchronous Reset

Simulating using iverilog and Gtkwave
Command used are
```c
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
gtkwave tb_dff_syncres.vcd
```

![Screenshot from 2024-10-20 01-18-15](https://github.com/user-attachments/assets/4f9a30d9-89f9-48a1-b1bc-7a6566cfbb6e)


### GtkWave output:We can see that here q changes to one when synchronous reset goes high w.r.t positive edge of clock
![Screenshot from 2024-10-20 01-18-55](https://github.com/user-attachments/assets/633c46d7-e82c-4829-8a96-43a35ef158e1)


# Synthesis of D-Flipflop using Yosys: Synthesized 3 types of D-Flipflops - Asynchronous Reset, Asynchronous Set and Synchronous Reset. 
## Asynchronous Reset
Synthesis using yosys commands used are
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_asyncres.v
4. synth -top dff_asyncres
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
8. write_verilog -noattr dff_asyncres_netlist.v
9. gvim dff_asyncres_netlist.v
```

![Screenshot from 2024-10-20 11-29-41](https://github.com/user-attachments/assets/2b94360f-4189-4b49-9d54-1326c2edb3af)


![Screenshot from 2024-10-20 11-30-01](https://github.com/user-attachments/assets/095cd86c-c65b-40ac-9209-09eaa6774b6d)

Generated Structure is shown below by using command ``show``
![Screenshot from 2024-10-20 11-30-13](https://github.com/user-attachments/assets/fc36b417-f27a-483d-abb8-fedfc26b94af)


![Screenshot from 2024-10-20 11-30-59](https://github.com/user-attachments/assets/6025f3eb-33eb-477b-805f-c19f77bace4b)

## Asynchronous Set
Synthesis using yosys commands used are
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_async_set.v
4. synth -top dff_async_set
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
8. write_verilog -noattr dff_async_set_netlist.v
9. gvim dff_async_set_netlist.v
```
![Screenshot from 2024-10-20 11-36-12](https://github.com/user-attachments/assets/5a85af44-7f29-44dd-b320-27641cbc14e0)


![Screenshot from 2024-10-20 11-36-33](https://github.com/user-attachments/assets/89097ec9-3934-437c-b4c9-b4e4b0bb73b1)

Generated Structure is shown below by using command ``show``
![Screenshot from 2024-10-20 11-36-49](https://github.com/user-attachments/assets/215d02a1-eaec-4281-8ad5-7d3021f77485)
![Screenshot from 2024-10-20 11-37-19](https://github.com/user-attachments/assets/9e9ac2c1-0e62-4619-a2c6-d85ea4c062ff)


## Synchronous Reset
Synthesis using yosys commands used are

```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_syncres.v
4. synth -top dff_syncres
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
8. write_verilog -noattr dff_syncres_netlist.v
9. gvim dff_syncres_netlist.v
```

![Screenshot from 2024-10-20 11-43-16](https://github.com/user-attachments/assets/94245328-c340-4285-8140-fe858f3a0d20)

![Screenshot from 2024-10-20 11-43-28](https://github.com/user-attachments/assets/dad0bccc-44f0-4daf-bde4-d1d2e3b68b3d)

Generated Structure is shown below by using command ``show``
![Screenshot from 2024-10-20 11-43-35](https://github.com/user-attachments/assets/e74ecf39-fcc5-43dc-b5b4-6f4ff90c64f8)
![Screenshot from 2024-10-20 11-44-02](https://github.com/user-attachments/assets/c6122e1c-ad71-4f88-b4c2-d9a104b5ce1d)

## Multiplication by 2: In this tutorial, we learn that multiplying a number by 2 doesn’t require specialized multiplier hardware. This operation can be easily accomplished by appending a zero to the least significant bit (LSB) of the number, effectively shifting it to the left.
Commands Used are

```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog mult_2.v
4. synth -top mul2
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. show
7. write_verilog -noattr mul2_net.v
8. gvim mul2_net.v
```
![Screenshot from 2024-10-20 11-51-40](https://github.com/user-attachments/assets/2036bb65-0284-4c25-8a47-daec7f07871d)
![Screenshot from 2024-10-20 11-51-55](https://github.com/user-attachments/assets/32a12b59-bc07-4319-ae76-91a76eea483f)
![Screenshot from 2024-10-20 11-52-10](https://github.com/user-attachments/assets/dfe89ae8-dcf0-4568-99c1-67d1c0f114c9)
![Screenshot from 2024-10-20 11-52-45](https://github.com/user-attachments/assets/22b0f6c3-3424-464f-8bc8-6d2c0984f68a)



## Multiplication by 9: In this tutorial, we discover that multiplying a number by 9 doesn’t need dedicated multiplier hardware. This can be done by simply concatenating the number with itself, which effectively achieves the desired result.

Commands Used are
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog mult_9.v
4. synth -top mult9
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. show
7. write_verilog -noattr mul9_net.v
8. gvim mul9_net.v
```

![Screenshot from 2024-10-20 12-01-12](https://github.com/user-attachments/assets/71e140d8-13ac-4aee-9840-b05929923a63)
![Screenshot from 2024-10-20 12-01-28](https://github.com/user-attachments/assets/46b206c9-a0c9-4da1-ba06-760f834cc400)
![Screenshot from 2024-10-20 12-02-00](https://github.com/user-attachments/assets/1e94af32-be63-47cc-b7ad-d63567d8b085)
![Screenshot from 2024-10-20 12-02-14](https://github.com/user-attachments/assets/56d4c16e-fc0e-4fce-b2a2-950d6800cfd5)



  </details>




  <details>
  <summary>Day3 </summary>

  # Design Optimization techniques

  ## Design infers 2 input AND Gate:
  Commands Used are:
  ```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check2.v
4. synth -top opt_check2
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. opt_clean -purge
7. show
```
code:
```c
//Design
module opt_check(input a, input b, output y);
	assign y = a?b:0;
endmodule
```

![Screenshot from 2024-10-20 12-10-53](https://github.com/user-attachments/assets/71df7650-b647-4b34-81e3-cd5520649ad1)
![Screenshot from 2024-10-20 12-11-15](https://github.com/user-attachments/assets/c59c05f5-bbb4-4c1a-bb8d-643b52bbbcc9)
![Screenshot from 2024-10-20 12-11-26](https://github.com/user-attachments/assets/5a89b18a-c2ff-417b-9a13-f1f8f12c10b7)

## Design infers 2 input OR Gate
  Commands Used are:
  ```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check2.v
4. synth -top opt_check2
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. opt_clean -purge
7. show
```
code:
```c
//Design
module opt_check2(input a, input b, output y);
	assign y = a?1:b;
endmodule
```

![Screenshot from 2024-10-20 12-16-33](https://github.com/user-attachments/assets/37efef12-fe87-43d0-8885-2eff594f983c)
![Screenshot from 2024-10-20 12-16-44](https://github.com/user-attachments/assets/40292864-cf27-45c6-b790-e32d1134ed7a)
![Screenshot from 2024-10-20 12-17-02](https://github.com/user-attachments/assets/b77eb80d-1e13-41a0-8408-df75066a7f28)



## Design infers 3 input AND Gate
  Commands Used are:
  ```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check3.v
4. synth -top opt_check3
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. opt_clean -purge
7. show
```

code:
```c
//Design
module opt_check2(input a, input b, input c, output y);
	assign y = a?(b?c:0):0;
endmodule
```

![Screenshot from 2024-10-20 12-19-00](https://github.com/user-attachments/assets/67dbc049-31e6-4adc-9c69-3452a3f68de1)
![Screenshot from 2024-10-20 12-19-07](https://github.com/user-attachments/assets/9d488d8b-8977-4e35-8c56-2b301939d2cc)
![Screenshot from 2024-10-20 12-19-11](https://github.com/user-attachments/assets/4c19d71c-7340-4b0b-8c1a-4871641bd75a)


# Optimization Using Multiple Modules

## Multiple Module Optimization1 Using Flatten

Commands Used are:
```c
1.flatten
2. yosys
3. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
4. read_verilog multiple_module_opt.v
5. synth -top multiple_module_opt
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. opt_clean -purge
8. show multiple_module_opt
```
Code:
```c
//Design

module sub_module1(input a, input b, output y);
	assign y = a & b;
endmodule

module sub_module2 (input a, input b output y);
	assign y = a^b;
endmodule

module multiple_module_opt(input a, input b input c, input d output y);
	wire n1,n2, n3;

	sub_module1 U1 (.a(a), .b(1'b1), .y(n1));
	sub_module2 U2 (.a(n1), .b(1'b0), .y(n));
	sub_module2 U3 (.a(b), .b(d), .y(n3));

	assign y = c | (b & n1);
endmodule
```

![Screenshot from 2024-10-20 12-58-13](https://github.com/user-attachments/assets/488c0904-3dac-4642-8f2e-4e111aeca9db)
![Screenshot from 2024-10-20 12-58-31](https://github.com/user-attachments/assets/b406f55e-322f-44ce-9a02-7ee4740d6213)
![Screenshot from 2024-10-20 12-58-38](https://github.com/user-attachments/assets/53c4eeda-55cd-4ab1-ab98-b59f6e938366)


## Multiple Module Optimization-2

Commands Used are:
```c
1.flatten
2. yosys
3. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
4. read_verilog multiple_module_opt2.v
5. synth -top multiple_module_opt2
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. opt_clean -purge
8. show multiple_module_opt2
```

Code:
```c
//Design
module sub_module(input a input b output y);
	assign y = a & b;
endmodule

module multiple_module_opt2(input a, input b input c, input d, output y);
	wire n1,n2, n3;

	sub_module U1 (.a(a), .b(1'b0), y(n));
	sub_module U2 (.a(b), .b(c), .y(n2));
	sub_module U3 (.a(n2), .b(d), .y(n));
	sub_module U4 (.a(n3), .b(n1), .y(y));
endmodule

```
![Screenshot from 2024-10-20 13-01-20](https://github.com/user-attachments/assets/2e2b9f16-b184-4a03-93e7-f7e1bd3c6c9b)
![Screenshot from 2024-10-20 13-01-40](https://github.com/user-attachments/assets/b1b1e7ae-973f-4cd0-8f37-c80c478c4e13)
![Screenshot from 2024-10-20 13-01-47](https://github.com/user-attachments/assets/d31d4d13-dea4-4079-abbd-eff401d7dca8)

## D-Flipflop Constant 1 with Asynchronous Reset (active low)

Commands for Simulation using iverilog and gtkwave:
```c
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```
![Screenshot from 2024-10-20 13-16-05](https://github.com/user-attachments/assets/1917abbc-87ca-478a-b981-616589482c56)

Gtkwave Output: We can observe that the q is high when reset is zero and it does not depend on clock edge
![Screenshot from 2024-10-20 13-16-17](https://github.com/user-attachments/assets/76570cdc-7d9d-491c-bf1b-bc332b4b0e05)

### Yosys Synthesis
Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const1.v
4. synth -top dff_const1
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Code:
```c
//Design
module dff_const1(input clk, input reset, output reg q); 
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
//Testbench
module tb_dff_const1; 
	reg clk, reset;
	wire q;

	dff_const1 uut (.clk(clk),.reset(reset),.q(q));

	initial begin
		$dumpfile("tb_dff_const1.vcd");
		$dumpvars(0,tb_dff_const1);
		// Initialize Inputs
		clk = 0;
		reset = 1;
		#3000 $finish;
	end

	always #10 clk = ~clk;
	always #1547 reset=~reset;
endmodule
```


![Screenshot from 2024-10-20 13-23-38](https://github.com/user-attachments/assets/c119c57d-a4f0-40fe-bc89-7b7c30740a83)
![Screenshot from 2024-10-20 13-24-10](https://github.com/user-attachments/assets/66823c46-2a27-4050-afc4-867f866ee061)


## D-Flipflop Constant 2 with Asynchronous Reset (active high) 


Commands for Simulation using iverilog and gtkwave:
```c
iverilog dff_const2.v tb_dff_const2.v
./a.out
gtkwave tb_dff_const2.vcd
```

![Screenshot from 2024-10-20 13-32-50](https://github.com/user-attachments/assets/44feeb37-440a-4a75-9cf3-c1e4cefbb011)

Gtkwave Output: We can observe that the q is always high irrespective of reset signal
![Screenshot from 2024-10-20 13-32-59](https://github.com/user-attachments/assets/f34db80c-b0c0-41e5-801a-de529137ec4c)


### Yosys Synthesis
Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const2.v
4. synth -top dff_const2
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Code:
```c
//Design
module dff_const2(input clk, input reset, output reg q); 
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
//Testbench
module tb_dff_const2; 
	reg clk, reset;
	wire q;

	dff_const2 uut (.clk(clk),.reset(reset),.q(q));

	initial begin
		$dumpfile("tb_dff_const1.vcd");
		$dumpvars(0,tb_dff_const1);
		// Initialize Inputs
		clk = 0;
		reset = 1;
		#3000 $finish;
	end

	always #10 clk = ~clk;
	always #1547 reset=~reset;
endmodule
```


![Screenshot from 2024-10-20 13-36-12](https://github.com/user-attachments/assets/7fa7a444-60a3-4147-99cc-c6c507cdd92d)
![Screenshot from 2024-10-20 13-36-44](https://github.com/user-attachments/assets/ff354331-4ea3-4921-912b-a73f38ede405)



## D-Flipflop Constant 3 with Asynchronous Reset (active low) 

Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const3.v
4. synth -top dff_const3
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```
Code:

```c
//Design
module dff_const3(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b1;
			q1 <= 1'b0;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```


![Screenshot from 2024-10-20 13-41-59](https://github.com/user-attachments/assets/bca2cd53-ee1f-4119-ac95-e8212c4d6de8)
![Screenshot from 2024-10-20 13-42-05](https://github.com/user-attachments/assets/dc05ffe1-3ce8-4d76-b8e8-073129f2054b)





## D-Flipflop Constant 4 with Asynchronous Reset (active high) 


Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const4.v
4. synth -top dff_const4
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```
Code:

```c
//Design
module dff_const4(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b1;
			q1 <= 1'b1;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```

![Screenshot from 2024-10-20 13-43-47](https://github.com/user-attachments/assets/2d2fd54c-2c72-4dfc-8996-63ceb78cd6d7)
![Screenshot from 2024-10-20 13-43-33](https://github.com/user-attachments/assets/7dc92b44-c6f3-440a-ac19-e81bb0dac859)


## D-Flipflop Constant 5 with Asynchronous Reset 

Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const5.v
4. synth -top dff_const5
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```
Code:

```c
//Design
module dff_const5(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b0;
			q1 <= 1'b0;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```
![Screenshot from 2024-10-20 14-24-20](https://github.com/user-attachments/assets/ff02f77f-b74b-4eca-94a7-c3eaa0adad98)
![Screenshot from 2024-10-20 14-24-42](https://github.com/user-attachments/assets/694fe788-0222-4f0b-883b-febcc0315155)


## Counter Optimization 1: 


Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog counter_opt.v
4. synth -top counter_opt
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```
Code:

```c
//Design	
module counter_opt (input clk, input reset, output q);
	reg [2:0] count;
	assign q = count[0];
	
	always @(posedge clk,posedge reset)
	begin
		if(reset)
			count <= 3'b000;
		else
			count <= count + 1;
	end
endmodule
```
![Screenshot from 2024-10-20 14-29-08](https://github.com/user-attachments/assets/086fea8c-d614-4f3b-8fc4-c84399776616)
![Screenshot from 2024-10-20 14-29-17](https://github.com/user-attachments/assets/307371df-6cb7-4ea1-b1e2-7d1b1f9f2f9d)





## Counter Optimization 2: 


Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog counter_opt2.v
4. synth -top counter_opt
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```
Code:

```c
//Design	
module counter_opt2 (input clk, input reset, output q);
	reg [2:0] count;
	assign q = (count[2:0] == 3'b100);
	
	always @(posedge clk,posedge reset)
	begin
		if(reset)
			count <= 3'b000;
		else
			count <= count + 1;
	end
endmodule
```

![Screenshot from 2024-10-20 14-37-27](https://github.com/user-attachments/assets/08878738-79fa-49fc-ac35-0a78412c31bd)
![Screenshot from 2024-10-20 14-37-44](https://github.com/user-attachments/assets/d75524ee-de54-4c03-8022-40fb3d8b66a0)





</details>


  <details>
  <summary>Day4 </summary>
  


# GLS , blocking vs non blocking and Synthesis-Simulation mismatch

## Design of 2x1 MUX using Ternary Operator: 
Commands for Simulation using iverilog and gtkwave:
```c
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
code:
```c
//Design
module ternary_operator_mux(input i0, input i1, input sel, output y);
	assign y = sel?i1:i0;
endmodule
```
![Screenshot from 2024-10-20 15-01-35](https://github.com/user-attachments/assets/e9407a80-1d2b-4d68-b51b-0b1b3e307110)

Gtkwave Output
![Screenshot from 2024-10-20 15-01-44](https://github.com/user-attachments/assets/213ee08c-a520-4f79-a10a-2fd1a06a83ed)


### Yosys
Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog ternary_operator_mux.v
4. synth -top ternary_operator_mux
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. write_verilog -noattr ternary_operator_mux_net.v
7. !gvim ternary_operator_mux_net.v
8. show
```

![Screenshot from 2024-10-20 15-05-45](https://github.com/user-attachments/assets/f0bff3d5-7b75-4f45-bdc0-a4cae6463a8b)
![Screenshot from 2024-10-20 15-05-58](https://github.com/user-attachments/assets/0d0938b1-0098-40de-b93a-f3a6b5ea2ab2)


Netlist Generated:

```c
//Generated Netlist
module ternary_operator_mux(i0, il, sel, y);
	wire _0_;
	wire _1_;
	wire _2_;
	wire _3_;
	input i0; wire i0;
	input il; wire il;
	input sel; wire sel;
	output y; wire y;
	
	sky130_fd_sc_hd_mux2_1 _4_ (.AO(_0_),.A1(_1_),.S(_2_),.X(_3_));

	assign _0_ = i0;
	assign _1_ = il;
	assign _2_ = sel;
	assign y = _3_;
endmodule
```


Gate Level Synthesis Command:
```c
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
![Screenshot from 2024-10-20 15-40-05](https://github.com/user-attachments/assets/feb19f53-3755-4531-bb5b-ebcca13af4bb)


We can observe that more no of signals are generated using GLS
![Screenshot from 2024-10-20 15-42-27](https://github.com/user-attachments/assets/eceab4e3-91b6-40cb-b3f6-b464ea34ed1f)

## Design of a Bad 2x1 MUX:

Commands for Simulation using iverilog and gtkwave:
```c
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
code:
```c
//Design
module bad_mux(input i0, input i1, input sel, output reg y);
	always@(sel)
	begin
		if(sel)
			y <= i1;
		else
			y <= i0;
	end
endmodule
```
![Screenshot from 2024-10-20 15-48-26](https://github.com/user-attachments/assets/7fabc1e7-11b8-4165-a97f-b497bced2fd6)


Gtkwave Output
![Screenshot from 2024-10-20 15-48-49](https://github.com/user-attachments/assets/275a4e63-62a9-4b30-9e44-3951d9f25da3)






### Yosys
Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog bad_mux.v
4. synth -top bad_mux
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. write_verilog -noattr bad_mux_net.v
7. !gvim bad_mux_net.v
8. show
```

![Screenshot from 2024-10-20 15-53-31](https://github.com/user-attachments/assets/c47de5c0-762e-4876-8ed5-13e6d553f1c1)

![Screenshot from 2024-10-20 15-54-19](https://github.com/user-attachments/assets/ff554584-5d3a-49b6-83ce-a6e8d71afa3f)

Netlist Generated:

```c
//Generated Netlist
module bad_mux(i0, il, sel, y);
	wire _0_;
	wire _1_;
	wire _2_;
	wire _3_;
	input i0; wire i0;
	input il; wire il;
	input sel; wire sel;
	output y; wire y;
	
	sky130_fd_sc_hd_mux2_1 _4_ (.AO(_0_),.A1(_1_),.S(_2_),.X(_3_));

	assign _0_ = i0;
	assign _1_ = il;
	assign _2_ = sel;
	assign y = _3_;
endmodule
```


Gate Level Synthesis Command:
```c
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```

![Screenshot from 2024-10-20 15-58-04](https://github.com/user-attachments/assets/b92eb8b5-0d13-45cc-8d8b-697a3052b067)


We can observe that more no of signals are generated for GLS
![Screenshot from 2024-10-20 15-58-12](https://github.com/user-attachments/assets/d961dbae-4290-44bd-bc62-b02a5403952b)


## Blocking Caveat: 

Commands for Simulation using iverilog and gtkwave:
```c
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
code:
```c
//Design
module blocking_caveat(input a, input b, input c, output reg d);
	reg x;

	always@(*)
	begin
		d = x & c;
		x = a | b;
	end
endmodule
```
![Screenshot from 2024-10-20 16-26-29](https://github.com/user-attachments/assets/31d7a34b-4cc4-48d3-afe3-cdd974ba7ca7)

### Gtkwave Output: We can observe that when a=1 , b=0 , c=1 , d is 0 which is incorrect it should equal to 1 this occurs due to usage of blocking statement(logic is x=a|b , d = x&c where x is intermidiate variable)
![Screenshot from 2024-10-20 16-28-34](https://github.com/user-attachments/assets/2d524b76-17f3-47b2-87a4-8e8786d47d16)



### Yosys
Commands Used are:
```c
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog blocking_caveat.v
4. synth -top blocking_caveat
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. write_verilog -noattr blocking_caveat_net.v
7. !gvim blocking_caveat_net.v
8. show
```
![Screenshot from 2024-10-20 16-40-05](https://github.com/user-attachments/assets/b216bc0b-ee53-4a36-a3ac-3539e0c99b78)
![Screenshot from 2024-10-20 16-40-18](https://github.com/user-attachments/assets/3c981214-95cf-44d7-8920-625953a99a6c)



Netlist Generated:

```c
//Generated Netlist
module blocking_caveat(a,b,c,d);
	wire _0_;
	wire _1_;
	wire _2_;
	wire _3_;
	wire _4_;
	input a; wire a;
	input b; wire b;
	input c; wire c;
	input d; wire d;
	output d; wire d;
	
	sky130_fd_sc_hd__o21a_1 _5_ (.A1(_2_),.A2(_1_),.B1(_3_),.X(_4_));

	assign _2_ = b;
	assign _1_ = a;
	assign _3_ = c;
	assign d = _4_;
endmodule
```

Gate Level Synthesis Command:
```c
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```

![Screenshot from 2024-10-20 16-44-53](https://github.com/user-attachments/assets/3e35b46b-4cdf-49c4-b138-f0172deb3fb8)

We can observe the more no of signals are generated using GLS and no occurence of mismatched 
![Screenshot from 2024-10-20 16-50-23](https://github.com/user-attachments/assets/c211c589-26de-4024-9c17-5ee37b1cbb30)

### Conclusion: It is observed that when a=0, b=0 ,c=1 obtained d=0 which is correct , so the mismatch error is solved here using GLS



</details>


## Lab9:Synthesize RISC-V and compare output with functional simulations, and show the following 

  <details>
  <summary>Click to open </summary>

###  Performing Yosys

Command Used are

```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty -lib ../lib/avsddac.lib
read_liberty -lib ../lib/avsdpll.lib
read_verilog vsdbabysoc.v
read_verilog rvmyth.v
read_verilog clk_gate.v
synth -top vsdbabysoc
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show vsdbabysoc
write_verilog -noattr vsdbabysoc.synth.v
!gvim vsdbabysoc.synth.v
```


![Screenshot from 2024-10-24 01-04-51](https://github.com/user-attachments/assets/113557f2-c1c6-4d73-b727-62c25ca95a2a)
![Screenshot from 2024-10-24 01-05-00](https://github.com/user-attachments/assets/f5e16f87-c2ad-4d4a-ad27-b8fac45fe051)

### Generated Netlist:

![Screenshot from 2024-10-24 01-22-41](https://github.com/user-attachments/assets/5903c911-0099-449f-b7aa-1925a89527ca)
![Screenshot from 2024-10-24 01-23-15](https://github.com/user-attachments/assets/34a985c9-1293-46d6-8b11-0853a78ccea2)
![Screenshot from 2024-10-24 01-30-51](https://github.com/user-attachments/assets/29f66f54-963c-410e-8d9c-e11b8b7978b6)
only few snaps are shared

### Synthesised Circuit Diagram using standard cells in the library:

![Screenshot from 2024-10-24 01-03-12](https://github.com/user-attachments/assets/ddf4bfe6-4c5a-49d8-bd24-dc2187f2e536)



### Post Synthesis Similation (GLS):

Commands Used are:

```c
cd VSDBabySoC
mkdir -p output/post_synth_sim && iverilog -o output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM -DFUNCTIONAL -DUNIT_DELAY=#1 -I src/module/include -I src/module -I src/gls_model src/module/testbench.v && cd output/post_synth_sim && ./post_synth_sim.out
gtkwave post_synth_sim.vcd

```
![Screenshot from 2024-10-24 02-07-47](https://github.com/user-attachments/assets/3edc4500-11ce-4a5b-b82a-c7a497a854cd)


## Generated Waveform post Gate Level Synthesis simulation:

![Screenshot from 2024-10-24 01-16-57](https://github.com/user-attachments/assets/df3d96d3-bcce-48a1-98fc-f8e2e47e6c2a)

zoom out view
![Screenshot from 2024-10-24 01-17-18](https://github.com/user-attachments/assets/bbb4568f-f379-4e9e-9ef5-88de601a99c2)



### To perform iverilog compilation for rvmyth.v file generated from TL Verilog using Sandpiper tool, completed in previous Lab
  
  Commands Used are:
  ```c
1.iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
2. ./pre_synth_sim.out
3. gtkwave pre_synth_sim.vcd
```
![pre_syn](https://github.com/user-attachments/assets/ce4b957b-78fe-4dd7-9f31-ae4db5b289b1)
![Screenshot from 2024-10-23 20-14-02](https://github.com/user-attachments/assets/74a91886-eeb2-4c24-ae58-296b9c57030b)

zoom out view
![Screenshot from 2024-10-23 20-15-54](https://github.com/user-attachments/assets/5c7758f2-ec6d-4b53-8194-f6409bec82b0)


#### Conclusion: From the above comparison of waveforms from both the labs we can conclude that the acheived output matches the expectation i.e., the sum of numbers from 1 to 9 which is 45 in decimal or 2D in hexadecimal format. Stating that O1=O2



</details>

## Lab10:Static Timing Analysis for Synthesized Risc-V Core using OpenSTA

 <details>
  <summary>Click to open </summary>

## STA:
Static Timing Analysis (STA) is essential in ASIC design for ensuring that the digital circuit meets the required timing constraints without requiring dynamic simulation of actual data. The focus of STA is to validate that all timing paths within the design meet specific constraints, which ensures the circuit will function correctly across all operational conditions.

* Timing Paths: In STA, timing paths are analyzed to ensure data can travel from one point to another within a defined time. The main types are:

* Setup Paths: Ensure data arrives at the next stage before the clock edge.
* Hold Paths: Ensure data is stable for a certain period after the clock edge.
* Clock Domains: STA divides the design into different clock domains to verify timing between elements synchronized to the same or different clocks. For multiple clocks, STA verifies the timing paths between each clock domain, focusing on:

* Synchronous Domains: Where clocks are related and can be analyzed for setup and hold constraints.
* Asynchronous Domains: Where clocks are unrelated, requiring special handling, often with synchronizers or FIFO buffers.
Clock Skew and Jitter:

* Clock Skew: The difference in arrival times of a clock signal at different flip-flops. STA checks skew impact since it affects timing paths and data setup/hold requirements.
* Clock Jitter: Variation in clock edge timing due to noise or other factors. STA incorporates jitter in timing analysis to ensure that jitter doesn’t cause timing violations.


### Timing Checks:
* Setup Check: Ensures data arrives before the clock edge, allowing sufficient time for stabilization.
* Hold Check: Ensures data remains stable long enough after the clock edge.

### Timing Margins and Slack:

* Slack: The difference between the required time and the actual arrival time of signals. Positive slack means timing constraints are met, while negative slack indicates a timing violation.
* Setup Slack: Time margin for setup constraints.
* Hold Slack: Time margin for hold constraints.
* Static Timing Tools: STA tools, like Synopsys PrimeTime and Cadence Tempus, perform analysis by creating and traversing timing graphs that represent all paths in the design. These tools provide reports on slack, critical paths, and timing violations.

Process, Voltage, and Temperature (PVT) Corners: STA includes PVT analysis to account for variations in manufacturing, operational voltages, and temperature ranges. STA ensures that timing constraints are met across worst-case PVT corners.

## Optimization Techniques:

* Buffer Insertion: Adds buffers to reduce delay in long paths.
* Gate Sizing: Resizes gates to improve timing on critical paths.
* Clock Tree Optimization (CTO): Minimizes skew and jitter in the clock distribution network. By ensuring that timing analysis is thorough and covers all potential scenarios, STA plays a crucial role in achieving reliable and high-performance ASIC designs.

### reg2reg Path:
A reg2reg path (register-to-register path) refers to a timing path in a digital circuit that connects two sequential elements, specifically flip-flops or registers. This path is crucial in the context of Static Timing Analysis (STA) because it represents the flow of data from one register to another through combinational logic.

Reg2reg paths are essential for ensuring proper data flow and synchronization in digital circuits, especially in designs with pipelining or sequential operations. Analyzing these paths helps in verifying that the data processing occurs correctly across clock cycles, thereby ensuring the overall functionality and reliability of the circuit.

### clk2reg Path:
A clk2reg path (clock-to-register path) refers to a timing path in a digital circuit that connects the clock signal to a register (flip-flop). This path is crucial for ensuring that the register operates correctly in response to clock events.


## STA for the synthesized RISC-V Core:
After installing OpenSTA use the following command
```c
read_liberty /home/tushar-katole/Downloads/VSDBabySoC-main/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog /home/tushar-katole/VSDBabySoC/src/module/vsdbabysoc.synth.v
link_design rvmyth
create_clock -name CLK -period 10 [get_ports CLK]
set_clock_uncertainty [expr 0.05 * 10] -setup [get_clocks CLK]
set_clock_uncertainty [expr 0.08 * 10] -hold [get_clocks CLK]
set_clock_transition [expr 0.05 * 10] [get_clocks CLK]
set_input_transition [expr 0.08 * 10] [all_inputs]
report_checks -path_delay max
report_checks -path_delay min
```
* Clock period:10 nanoseconds
* Setup uncertainty: 5% of clock period
* Clock transition: 5% of clock period
* Hold uncertainty: 8% of clock period
* Input transition: 8% of clock period

The following screenshots illustrate timing reports:

![Screenshot from 2024-10-28 18-36-21](https://github.com/user-attachments/assets/6c541262-1265-4c51-a83b-b16338837d99)

reg2reg Setup report:
![Screenshot from 2024-10-28 18-36-50](https://github.com/user-attachments/assets/6813a809-9b5e-4210-8bfa-c17a2bafa273)

reg2reg Hold report:
![Screenshot from 2024-10-28 18-37-28](https://github.com/user-attachments/assets/432c713f-42a9-4e66-b75d-f9fe8d3f7f94)

### The max path report indicates Setup Slack while the min path report shows Hold Slack measurements.




</details>
  


</details>



## Lab11: PVT Corner Analysis for Synthesized VSDBabySoC using OpenSTA
 <details>
  <summary>Click to open </summary>

The PVT corner refers to the combination of Process, Voltage, and Temperature variations that a semiconductor chip might encounter during its operation. These variations can affect the performance, power consumption, and reliability of the chip, so they are simulated to ensure the chip functions correctly under different conditions
The below tcl script sta_pvt.tcl can be run to performt the STA across the PVT corners for which the sky130 lib files are available:

### The below tcl script sta_pvt.tcl can be run to performt the STA across the PVT corners for which the sky130 lib files are available:
```c
set list_of_lib_files(1) "sky130_fd_sc_hd__ff_100C_1v65.lib"
set list_of_lib_files(2) "sky130_fd_sc_hd__ff_100C_1v95.lib"
set list_of_lib_files(3) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
set list_of_lib_files(4) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v95.lib"
set list_of_lib_files(7) "sky130_fd_sc_hd__ss_100C_1v40.lib"
set list_of_lib_files(8) "sky130_fd_sc_hd__ss_100C_1v60.lib"
set list_of_lib_files(9) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
set list_of_lib_files(10) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v60.lib"
set list_of_lib_files(14) "sky130_fd_sc_hd__ss_n40C_1v76.lib"
set list_of_lib_files(15) "sky130_fd_sc_hd__tt_025C_1v80.lib"
set list_of_lib_files(16) "sky130_fd_sc_hd__tt_100C_1v80.lib"

for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
read_liberty /home/tushar-katole/VSDBabySoC/src/timing_libs/$list_of_lib_files($i)
read_verilog /home/tushar-katole/VSDBabySoC/src/module/vsdbabysoc.synth.v
read_liberty -min /home/tushar-katole/VSDBabySoC/src/lib/avsdpll.lib
read_liberty -max /home/tushar-katole/VSDBabySoC/src/lib/avsdpll.lib
read_liberty -min /home/tushar-katole/VSDBabySoC/src/lib/avsddac.lib
read_liberty -max /home/tushar-katole/VSDBabySoC/src/lib/avsddac.lib
link_design rvmyth
read_sdc /home/tushar-katole/VSDBabySoC/src/sdc/vsdbabysoc_synthesis.sdc
check_setup -verbose
report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > /home/tushar-katole/VSDBabySoC/src/sta_output/min_max_$list_of_lib_files($i).txt

exec echo "$list_of_lib_files($i)" >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_worst_max_slack.txt
report_worst_slack -max -digits {4} >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_worst_max_slack.txt

exec echo "$list_of_lib_files($i)" >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_worst_min_slack.txt
report_worst_slack -min -digits {4} >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_worst_min_slack.txt

exec echo "$list_of_lib_files($i)" >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_tns.txt
report_tns -digits {4} >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_tns.txt

exec echo "$list_of_lib_files($i)" >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_wns.txt
report_wns -digits {4} >> /home/tushar-katole/VSDBabySoC/src/sta_output/sta_wns.txt

}

```


The SDC file used for generating clock and data constraints is given below:
```c

# Create clock with new period
create_clock [get_pins pll/CLK] -name clk -period 10 -waveform {0 5.000}

# Set loads
set_load -pin_load 0.5 [get_ports OUT]
set_load -min -pin_load 0.5 [get_ports OUT]

# Set clock latency
set_clock_latency 1 [get_clocks clk]
set_clock_latency -source 2 [get_clocks clk]

# Set clock uncertainty
set_clock_uncertainty 0.5 [get_clocks clk]  ; # 5% of clock period for setup
set_clock_uncertainty -hold 0.8 [get_clocks clk] ; # 8% of clock period for hold

# Set maximum delay
set_max_delay 10.05 -from [get_pins dac/OUT] -to [get_ports OUT]

# Set input delay for VCO_IN
set_input_delay -clock clk -max 4 [get_ports VCO_IN]
set_input_delay -clock clk -min 1 [get_ports VCO_IN]

# Set input delay for ENb_VCO
set_input_delay -clock clk -max 4 [get_ports ENb_VCO]
set_input_delay -clock clk -min 1 [get_ports ENb_VCO]

# Set input delay for ENb_CP
set_input_delay -clock clk -max 4 [get_ports ENb_CP]
set_input_delay -clock clk -min 1 [get_ports ENb_CP]

# Set input transition for VCO_IN
set_input_transition -max 0.5 [get_ports VCO_IN] ; # 5% of clock
set_input_transition -min 0.8 [get_ports VCO_IN] ; # adjust if needed

# Set input transition for ENb_VCO
set_input_transition -max 0.5 [get_ports ENb_VCO] ; # 5% of clock
set_input_transition -min 0.8 [get_ports ENb_VCO] ; # adjust if needed

# Set input transition for ENb_CP
set_input_transition -max 0.5 [get_ports ENb_CP] ; # 5% of clock
set_input_transition -min 0.8 [get_ports ENb_CP] ; # adjust if needed

```

Run below commands on terminal to source the sta_pvt.tcl file

![Screenshot from 2024-11-03 14-34-21](https://github.com/user-attachments/assets/885a3b4e-692e-4565-8e12-f6e72ae0b772)


A table comprising of the slacks report is shown below:

| Library Name                             | TNS       | WNS       | Worst Max Slack | Worst Min Slack |
|------------------------------------------|-----------|-----------|-----------------|-----------------|
| sky130_fd_sc_hd__tt_025C_1v80.lib        | 0         | 0         | 0.4392          | -0.4904         |
| sky130_fd_sc_hd__tt_100C_1v80.lib        | 0         | 0         | 0.5935          | -0.4855         |
| sky130_fd_sc_hd__ff_100C_1v65.lib        | 0         | 0         | 2.5545          | -0.5509         |
| sky130_fd_sc_hd__ff_100C_1v95.lib        | 0         | 0         | 4.0668          | -0.6040         |
| sky130_fd_sc_hd__ff_n40C_1v56.lib        | 0         | 0         | 0.7781          | -0.5085         |
| sky130_fd_sc_hd__ff_n40C_1v65.lib        | 0         | 0         | 1.9112          | -0.5449         |
| sky130_fd_sc_hd__ff_n40C_1v76.lib        | 0         | 0         | 2.9301          | -0.5757         |
| sky130_fd_sc_hd__ff_n40C_1v95.lib        | 0         | 0         | 4.0919          | -0.6125         |
| sky130_fd_sc_hd__ss_100C_1v40.lib        | -3106.4377| -18.6216  | -18.6216        | 0.1053          |
| sky130_fd_sc_hd__ss_100C_1v60.lib        | -1220.8483| -9.374    | -9.374          | -0.1580         |
| sky130_fd_sc_hd__ss_n40C_1v28.lib        | -14832.0938| -64.0632 | -64.0632        | 1.0296          |
| sky130_fd_sc_hd__ss_n40C_1v35.lib        | -8798.0049| -41.197   | -41.197         | 0.5475          |
| sky130_fd_sc_hd__ss_n40C_1v40.lib        | -6195.0615| -31.1937  | -31.1937        | 0.3249          |
| sky130_fd_sc_hd__ss_n40C_1v44.lib        | -4749.9995| -25.4079  | -25.4079        | 0.1909          |
| sky130_fd_sc_hd__ss_n40C_1v60.lib        | -1730.8564| -12.109   | -12.109         | -0.1372         |
| sky130_fd_sc_hd__ss_n40C_1v76.lib        | -630.0898 | -5.8819   | -5.8819         | -0.2962         |

Notr:-Worst Max slack = Worst Setup slack
      Worst Min slck = Worst hold slack

      
![TNS_plot](https://github.com/user-attachments/assets/694514d5-ca60-40c6-ac7d-9c6a4ff65fa4)

![WNS_plot](https://github.com/user-attachments/assets/ff392763-25f5-4291-9ea4-ca83037f2b20)

![Worst_Max_Slack_plot](https://github.com/user-attachments/assets/9b6f0356-e0b6-4ee6-bf04-ad23deead10c)

![Worst_Min_Slack_plot](https://github.com/user-attachments/assets/97260ad9-04a5-4e4c-ae13-9076cd502b26)

### Colnclusion:

From the above analysis we can conclude that

1. sky130_fd_sc_hd__ss_n40C_1v28.lib Library file has the worst setup slack
2. sky130_fd_sc_hd__ff_100C_1v95.lib Library file has the worst hold slack


</details>



## Lab12: Advanced Physical Design Using Openlane/Sky130 Wokshop
 <details>
  <summary>Day1 </summary>
	 
## Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
Tasks:

### 1.Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.



Commands to invoke the OpenLANE flow and perform synthesis

```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit

```

Terminal Snapshots:


![Screenshot from 2024-11-11 00-14-39](https://github.com/user-attachments/assets/91e84336-62d9-49ef-87ae-ccd5bc509ca2)

![Screenshot from 2024-11-11 00-23-27](https://github.com/user-attachments/assets/1c3f8e0c-1311-4f12-a999-29e0d04a6520)



Below snap shows the generated file on particular date 

![Screenshot 2024-11-11 004058](https://github.com/user-attachments/assets/b2e06c97-fc2d-476f-8e64-7832f57a7dce)

![Screenshot 2024-11-11 004810](https://github.com/user-attachments/assets/ef3cd85a-3638-49d4-bc63-04c87629b620)



### 2. Calculate the flop ratio.

![Screenshot 2024-11-11 004917](https://github.com/user-attachments/assets/9462f2e2-f5b1-4400-893a-b7a01154dc16)


![Screenshot 2024-11-11 004941](https://github.com/user-attachments/assets/9b92f47c-d4cb-4d94-b966-c96d0b945efa)



#### Calculation of Flop Ratio and DFF % from synthesis statistics report file

Flop Ratio = Number of D Flip-Flops/Total Number of Cells

The percentage of Flop Ratio = Flop Ratio * 100

```
Flop Ratio = 1613/14876 = 0.108429685
    
Percentage of Flip Flops = 0.108429685 ∗ 100 = 10.84296854%
```

  </details>

  





 <details>
  <summary>Day2 </summary>

  ## Good Floorpan vs Bad Floorplan and Introduction to Library Cell
  
### Implementation
1.Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
2.Calculate the die area in microns from the values in floorplan def.

3.Load generated floorplan def in magic tool and explore the floorplan.

4.Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.

5.Load generated placement def in magic tool and explore the placement. Area of Die in microns = Die width in microns ∗ Die height in microns

## 1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs

Commands to invoke the OpenLANE flow and perform floorplan
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```

Snapshots:

![Screenshot 2024-11-11 224246](https://github.com/user-attachments/assets/215ce76f-3587-40fd-b1ee-383df09c2508)

![Screenshot 2024-11-11 224453](https://github.com/user-attachments/assets/5e6382a0-4c51-4abf-8144-3863e53945db)

floorplan complete

![Screenshot 2024-11-11 224548](https://github.com/user-attachments/assets/589e572e-fa58-4b9a-8545-5ad13925bbc6)



## 2. Calculate the die area in microns from the values in floorplan def.

![Screenshot 2024-11-11 225119](https://github.com/user-attachments/assets/bf8ab0e0-5db0-4de4-8d57-8e16d0f8b003)

![Screenshot 2024-11-11 225406](https://github.com/user-attachments/assets/1b423c03-7b23-49dd-9299-80c785ed8adf)

![Screenshot 2024-11-11 225611](https://github.com/user-attachments/assets/68b4357f-2c51-4188-891e-d26599a5a40a)

According to floorplan def 1000 Unit Distance = 1 micron Die
Die width in unit distance = 660685 − 0 = 660685
Die height in unit distance = 671405 − 0 = 671405
Distance in microns = Value in unit distance / 1000 
Die width in microns = 660685/1000 = 660.685 microns 
Dieheight in microns = 671405/1000 = 671.405 microns 
Area of die in microns = 660.685 ∗ 671.405 = 443587.212425 square microns

## 3. Load generated floorplan def in magic tool and explore the floorplan.

Commands to load floorplan def in magic in another terminal
```
# Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/floorplan/

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

Snapshot:

![Screenshot 2024-11-12 004604](https://github.com/user-attachments/assets/e6da9f81-1a3c-47e4-9a78-f84b7002b6e7)

![Screenshot 2024-11-12 000448](https://github.com/user-attachments/assets/5daeda33-be56-411a-8c72-4b72659dabec)

![Screenshot 2024-11-12 000647](https://github.com/user-attachments/assets/1f9afa22-149b-4359-8a0c-fb368d30408f)


Equidistant placement of ports: 
![Screenshot from 2024-11-12 00-18-35](https://github.com/user-attachments/assets/df9abda4-8020-419c-ab70-099117ceb01e)


Port layer as set through config.tcl 
![Screenshot from 2024-11-12 00-26-04](https://github.com/user-attachments/assets/2d0817d7-f9c8-4af1-a438-2773fe70ee0f)
![Screenshot from 2024-11-12 00-29-10](https://github.com/user-attachments/assets/fbddcc40-e273-4d6a-9638-9251b8d8101b)



Decap Cells and Tap Cells
![Screenshot from 2024-11-12 00-34-03](https://github.com/user-attachments/assets/0e25bee0-b587-4ea9-bd55-c4dfc0ab3a72)


Diogonally equidistant Tap cells
![Screenshot from 2024-11-12 00-39-32](https://github.com/user-attachments/assets/5223d5d2-2713-48b1-957d-98808d7301df)



Unplaced standard cells at the origin
![Screenshot from 2024-11-12 00-40-48](https://github.com/user-attachments/assets/c3b9e9e0-2e20-4359-b403-aafc5d6be06e)




## 4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs. Command to run placement

```
# Congestion aware placement by default
run_placement
```
![Screenshot from 2024-11-12 01-10-46](https://github.com/user-attachments/assets/f6950154-e31f-4166-9c6a-5f21f96f16f9)

![Screenshot from 2024-11-12 01-11-54](https://github.com/user-attachments/assets/2b6021b3-2ae3-469e-8209-f6f4e5d4dfa8)





5. Load generated placement def in magic tool and explore the placement. Commands to load placement def in magic in another terminal

   
```
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```


![Screenshot from 2024-11-12 01-18-34](https://github.com/user-attachments/assets/0e04adda-bff1-40fa-9955-575da9261751)

![Screenshot from 2024-11-12 01-19-36](https://github.com/user-attachments/assets/9b3bec25-be46-4ce9-852c-6f20393e4960)


Standard cells legally placed 
![Screenshot from 2024-11-12 01-23-40](https://github.com/user-attachments/assets/2393d0ca-16b9-4369-9db4-fd02cff38515)


Commands to exit from current run

```
# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```


  </details>






 <details>
  <summary>Day3 </summary>

  ## Design Library Cell Using Magic Layout and Cell characterization:
Tasks:

1.Clone custom inverter standard cell design from github repository: Standard cell design and characterization using OpenLANE flow.
2.Load the custom inverter layout in magic and explore.
3.Spice extraction of inverter in magic.
4.Editing the spice model file for analysis through simulation.
5.Post-layout ngspice simulations.
6.Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

1. Clone custom inverter standard cell design from github repository
```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_tusinv.mag &
```
![Screenshot from 2024-11-14 11-53-26](https://github.com/user-attachments/assets/3cae3f6d-40e9-4e3f-aab4-5e77b345805e)



2.Load the custom inverter layout in magic and explore.

Screenshot of custom inverter layout in magic
![Screenshot from 2024-11-14 11-59-16](https://github.com/user-attachments/assets/cd4905d9-f4d3-4789-9d72-cb30f715fbd8)




PMOS identified
![Screenshot from 2024-11-13 11-24-02](https://github.com/user-attachments/assets/2293c389-058d-44a6-9c15-3c6406564921)


NMOS identified
![Screenshot from 2024-11-13 11-24-36](https://github.com/user-attachments/assets/527ebab9-e84e-41bd-a375-aad4caea3dba)


Output Y connectivity to PMOS and NMOS drain verified 
![Screenshot from 2024-11-14 12-12-08](https://github.com/user-attachments/assets/f841e4c5-e036-4cb5-b93c-9d700b9510e0)




PMOS source connectivity to VDD (here VPWR) verified
![Screenshot from 2024-11-14 12-12-38](https://github.com/user-attachments/assets/0c816b35-5eaf-4c50-bfb6-241c9e3f9e1d)



NMOS source connectivity to VSS (here VGND) verified
![Screenshot from 2024-11-14 12-14-05](https://github.com/user-attachments/assets/d21e6f7f-1c00-4f85-b7be-5b9da23dca82)



Deleting necessary layout part to see DRC error
![Screenshot from 2024-11-13 12-02-59](https://github.com/user-attachments/assets/9abbc77b-e3e4-439d-8d1d-5d068a97106e)


3.Spice extraction of inverter in magic.

Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic
```
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```

Screenshot of tkcon window after running above commands

![Screenshot 2024-11-14 121824](https://github.com/user-attachments/assets/3b49db8d-7687-4200-ba44-fdabe45b1079)

Screenshot of created spice file and its content in next screenshot

![Screenshot 2024-11-14 122230](https://github.com/user-attachments/assets/b04910ba-96d5-4df4-84cf-35f65f2aa457)


![Screenshot 2024-11-14 122353](https://github.com/user-attachments/assets/9a68683b-0d16-4ff1-b618-f860923ec7fb)


4.Editing the spice model file for analysis through simulation.

Measuring unit distance in layout grid
![Screenshot from 2024-11-13 12-39-15](https://github.com/user-attachments/assets/22ec0108-b9c6-451e-9a06-8e611b238ef8)


Final edited spice file ready for ngspice simulation

![Screenshot 2024-11-14 123701](https://github.com/user-attachments/assets/399c4f5f-b084-486a-b2d8-7dc2d31fe942)

5.Post-layout ngspice simulations.

Commands for ngspice simulation
```
# Command to directly load spice file for simulation to ngspice
ngspice sky130_tusinv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
```

Screenshots of ngspice run

![Screenshot 2024-11-14 123816](https://github.com/user-attachments/assets/a4d43b00-27b0-4266-97eb-73f0ba92ceeb)

![Screenshot 2024-11-14 123921](https://github.com/user-attachments/assets/467d950c-32c4-4ff2-9c73-4547b136811e)


Screenshot of generated plot

![Screenshot 2024-11-14 124956](https://github.com/user-attachments/assets/a840dda8-9979-4c56-9bf8-1ca733c56659)

* Rise transition time calculation Rise Transition Time = Time taken for output to rise to 80% − Time taken for output to rise to 20%
* 20% of output (3.3V) = 0.66V 80% of output (3.3V) = 2.64V


20% Screenshots

![Screenshot 2024-11-14 125326](https://github.com/user-attachments/assets/9ee22c2c-5323-420b-b050-4d23557b4811)

80% Screenshot 

![Screenshot 2024-11-14 125504](https://github.com/user-attachments/assets/545cc2e3-ca30-4541-9c9a-92c2fcf78817)


### Rise Transition Time = 2.248 - 2.18206 = 0.06594 ns = 65.94 ps

* Fall Transition Time = Time taken for output to fall to 80% − Time taken for output to fall to 20% 
* 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

20% Screenshots

![Screenshot 2024-11-14 125727](https://github.com/user-attachments/assets/22668895-5d6a-4daf-8e6c-1230f811d1af)

80% Screenshot 

![Screenshot 2024-11-14 125855](https://github.com/user-attachments/assets/cd4247e1-429a-4d4a-bdfa-b1261dca90fa)


### Fall Transition Time = 4.094 - 4.054 = 0.04 ns = 40 ps

* Rise Cell Delay Calculation Rise cell delay = Time taken by output to rise to 50% − Time taken by input to fall to 50% 
* 50 % of 3.3V = 1.65V

50% Screenshots


![Screenshot 2024-11-14 130020](https://github.com/user-attachments/assets/e98276ea-ef15-4afb-a905-dd915df6c96e)


![Screenshot 2024-11-14 130144](https://github.com/user-attachments/assets/b03a6a14-3fe1-481b-9191-75cb934638e8)

### Rise cell delay = 2.21 - 2.1489 = 0.0611 ns = 61.1 ps

* Fall Cell Delay Calculation Fall cell delay = Time taken by output to fall to 50% − Time taken by input to rise to 50% 
* 50 % of 3.3V = 1.65V

50% Screenshots


![Screenshot 2024-11-14 130307](https://github.com/user-attachments/assets/faa49019-1388-4edd-9d6c-6cdc309ac372)

### Fall cell delay = 4.0727−4.05 = 0.0227 ns = 22.7 ps

6.Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Link to Sky130 Periphery rules: https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections
```
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
```

Screenshots of commands run
![Screenshot from 2024-11-13 15-23-06](https://github.com/user-attachments/assets/a1c23949-2b4c-4b54-93f7-d9700f876130)


Screenshot of .magicrc file 
![Screenshot from 2024-11-13 15-23-27](https://github.com/user-attachments/assets/ffe1fda2-5260-41ce-a8ae-b0e5386206a2)



Incorrectly implemented poly.9 simple rule correction

Screenshot of poly rules
![Screenshot from 2024-11-13 15-29-31](https://github.com/user-attachments/assets/c39d49ab-07a1-40b4-b6a1-f07c6276df79)

Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u
![Screenshot from 2024-11-13 18-23-47](https://github.com/user-attachments/assets/10aafd85-b40c-40f6-b902-c7fc28be4919)

![Screenshot from 2024-11-13 15-52-18](https://github.com/user-attachments/assets/d4eecd11-20d7-4edb-9bdf-a41b6f59617c)


New commands inserted in sky130A.tech file to update drc
![Screenshot from 2024-11-13 16-06-31](https://github.com/user-attachments/assets/fbcce407-f21b-4787-a5b2-98166763343d)
![Screenshot from 2024-11-13 16-08-48](https://github.com/user-attachments/assets/461779c2-c5e1-4591-bb45-bebd35980baa)

Commands to run in tkcon window
```
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented
![Screenshot from 2024-11-13 16-34-05](https://github.com/user-attachments/assets/bf21f89d-2795-4a4d-957b-aa53b78b47a0)

Incorrectly implemented difftap.2 simple rule correction

Screenshot of difftap rules
![Screenshot from 2024-11-13 17-18-36](https://github.com/user-attachments/assets/2fd8de30-0e76-400a-bb4b-eaddc7c66981)



Screenshot of difftap rules
![Screenshot from 2024-11-13 16-41-44](https://github.com/user-attachments/assets/d17f05d7-27b9-4029-a7d4-102ac77bd3f0)

Incorrectly implemented
![Screenshot from 2024-11-13 18-35-39](https://github.com/user-attachments/assets/cfa65c5d-2e23-4ee4-8fb4-083a42afd35c)


Commands to run in tkcon window
```
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented showing no errors found 
![Screenshot from 2024-11-13 18-42-30](https://github.com/user-attachments/assets/e3bd8f45-44dd-4210-a316-1d3fa3900368)












  </details>







 <details>
  <summary>Day4 </summary>

  ## Pre-Layout timing analysis and Importance of good clock tree:
## Final steps for RTL2GDS using tritonRoute and openSTA:
1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.

Conditions to be verified before moving forward with custom designed cell layout:

    Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
    Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
    Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.

Commands to open the custom inverter layout
```
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd
![Screenshot from 2024-11-13 19-07-41](https://github.com/user-attachments/assets/5b624a55-1a8d-414c-b78f-3830e6ba36f6)

Commands for tkcon window to set grid as tracks of locali layer
```
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```
Screenshot of commands run
![Screenshot from 2024-11-13 19-12-45](https://github.com/user-attachments/assets/aaaa6449-2bf3-4dc3-b226-3f123a91f527)

Condition 1 verified
![Screenshot from 2024-11-13 19-12-03](https://github.com/user-attachments/assets/39f519a6-2d1f-49d8-827b-34f0076f880b)




Condition 2 verified
 Horizontal track pitch=0.46 u m 
 
![Screenshot from 2024-11-13 19-04-10](https://github.com/user-attachments/assets/a0bdba9f-1229-4940-9740-62b5442f5884)
 Widh  of standard   cell=1.38 um = 0.46 ∗ 3 

 



 



Condition 3 verified

 Vertical   track   pitch = 0.34 u m 
 ![Screenshot from 2024-11-13 19-19-52](https://github.com/user-attachments/assets/7751fe42-5bd2-43ea-af55-9be018dec508)

  Height   of   standard   cell = 2.72 um = 0.34 ∗ 8 

2. Save the finalized layout with custom name and open it.

Command for tkcon window to save the layout with custom name
```
# Command to save as
save sky130_vsdinv.mag

Command to open the newly saved layout

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_tusinv.mag &
```

Screenshot of newly saved layout
![Screenshot from 2024-11-13 19-32-43](https://github.com/user-attachments/assets/df94e90d-cb64-4d31-91f7-5f0d9aa5d589)

3. Generate lef from the layout.

Command for tkcon window to write lef
```
# lef command
lef write
```
Screenshot of command run
![Screenshot from 2024-11-13 19-36-11](https://github.com/user-attachments/assets/efa04423-8899-4ffa-b019-f27e5d5c4ebb)

Screenshot of newly created lef file
![Screenshot from 2024-11-13 19-37-17](https://github.com/user-attachments/assets/c118ec5d-4407-4bfa-9125-a8f52fbd2026)

4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory

```
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
Screenshot of commands run
![Screenshot from 2024-11-13 20-13-06](https://github.com/user-attachments/assets/ec3eea23-c38c-43fa-b231-d0515df19a59)

5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow
```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory
![Screenshot from 2024-11-13 19-46-35](https://github.com/user-attachments/assets/d08a998f-3644-429b-9bc0-57655f781312)

6. Run openlane flow synthesis with newly inserted custom inverter cell.
```
Commands to invoke the OpenLANE flow include new lef and perform synthesis

# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshots of commands run
![Screenshot from 2024-11-13 19-50-05](https://github.com/user-attachments/assets/6487d234-18a3-4448-a189-126672d3f1a0)

![Screenshot from 2024-11-13 20-27-06](https://github.com/user-attachments/assets/9c1eaa6e-1370-44c2-904a-e5c21c62d53a)

![Screenshot from 2024-11-13 20-51-58](https://github.com/user-attachments/assets/be48e367-3a10-4039-bf6d-92afa9a88354)

7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
Noting down current design values generated before modifying parameters to improve timing

![Screenshot from 2024-11-13 20-53-16](https://github.com/user-attachments/assets/4362087c-06f9-4243-a500-49a740ad56c4)

![Screenshot from 2024-11-13 20-53-47](https://github.com/user-attachments/assets/281863b4-7f13-4811-9a7f-c4c5f5ede95e)

Commands to view and change parameters to improve timing and run synthesis
```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshot of merged.lef in tmp directory with our custom inverter as macro

![Screenshot from 2024-11-13 20-59-32](https://github.com/user-attachments/assets/7e6bbd3f-d0a4-49f2-a948-7973fbb9bbeb)


Screenshots of commands run
![Screenshot from 2024-11-13 21-27-22](https://github.com/user-attachments/assets/ae01ba0b-dc82-41ba-b0a9-cd100962c1ec)

Comparing to previously noted run values area has increased and worst negative slack has become 0
![Screenshot from 2024-11-13 21-28-57](https://github.com/user-attachments/assets/fb5e38f0-939e-4db8-a0d1-4fb5408dab02)

![Screenshot from 2024-11-13 21-29-04](https://github.com/user-attachments/assets/2855bd92-aea0-4a26-8047-7d7389d02b37)


8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command
```
# Now we can run floorplan
run_floorplan
```

Screenshots of command run
![Screenshot from 2024-11-13 21-32-23](https://github.com/user-attachments/assets/c162c17d-02e8-42e8-af9d-e2e015cce849)


Since we are facing unexpected un-explainable error while using run_floorplan command, we can instead use the following set of commands available based on information from Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl and also based on Floorplan Commands section in Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md

```
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```


Screenshots of commands run
![Screenshot from 2024-11-13 21-33-36](https://github.com/user-attachments/assets/f86cb491-c4fe-4671-adb1-3eff37435b26)


Now that floorplan is done we can do placement using following command
```
# Now we are ready to run placement
run_placement
```


Screenshots of command run
![Screenshot from 2024-11-13 21-34-05](https://github.com/user-attachments/assets/1a9ec92f-b01a-4fd8-8580-772b519ccc74)

![Screenshot from 2024-11-13 21-35-08](https://github.com/user-attachments/assets/4316c983-93e2-4f55-9265-ed6edc5c32f8)


Commands to load placement def in magic in another terminal
```
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_15-13/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

Screenshot of placement def in magic
![Screenshot from 2024-11-13 21-43-28](https://github.com/user-attachments/assets/a98b6af6-330e-4b8a-817d-91a27c5d7e9d)


Screenshot of custom inverter inserted in placement def with proper abutment
![Screenshot from 2024-11-13 22-39-12](https://github.com/user-attachments/assets/f0908cf4-dbed-4e4c-b71b-b6e0bfc7744e)


![Screenshot from 2024-11-13 22-37-31](https://github.com/user-attachments/assets/fac5abd8-f737-4d0f-8c4b-12b720ace959)


9. Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot
![Screenshot from 2024-11-13 23-17-43](https://github.com/user-attachments/assets/e8fcbdd4-d257-4ca3-83fd-62cc27de210e)

![Screenshot from 2024-11-13 23-19-30](https://github.com/user-attachments/assets/54988377-68ec-4eb3-8afc-28506a42f946)

Newly created pre_sta.conf for STA analysis in openlane directory
![Screenshot from 2024-11-13 23-31-39](https://github.com/user-attachments/assets/a404d03b-4c17-4ace-b656-e676908609ed)

Newly created my_base.sdc for STA analysis in openlane/designs/picorv32a/src directory based on the file openlane/scripts/base.sdc
![Screenshot from 2024-11-13 23-32-04](https://github.com/user-attachments/assets/a3013a8a-0a2a-4248-8f80-b101ba8c8090)



Commands to run STA in another terminal
```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```
Screenshots of commands run
![Screenshot from 2024-11-13 23-37-02](https://github.com/user-attachments/assets/25dafc0f-dcd2-426c-9436-25ffbdb2332d)

![Screenshot from 2024-11-13 23-37-39](https://github.com/user-attachments/assets/18c460ea-694a-451d-acac-11a77f86a4bd)

![Screenshot from 2024-11-13 23-37-43](https://github.com/user-attachments/assets/36e4c598-e433-4625-8c45-44725dabf638)

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis
```
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 13-11_17-46 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
Commands run final screenshot

![Screenshot from 2024-11-13 23-47-37](https://github.com/user-attachments/assets/b00b9f1a-5489-41ef-90b2-89750eb6ae4f)

![Screenshot from 2024-11-13 23-48-45](https://github.com/user-attachments/assets/cd036857-30ee-4cdc-968f-3222311c20db)

![Screenshot from 2024-11-13 23-48-51](https://github.com/user-attachments/assets/95c5565f-b190-4f66-bffc-7be6e0349056)

![Screenshot from 2024-11-13 23-49-06](https://github.com/user-attachments/assets/da362063-3917-4dfc-860f-c8bc91878764)

10. Make timing ECO fixes to remove all violations.

OR gate of drive strength 2 is driving 4 fanouts

![Screenshot from 2024-11-13 23-51-10](https://github.com/user-attachments/assets/390cbbbe-7fa3-4fc6-969c-7006946171ef)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-11-13 23-59-57](https://github.com/user-attachments/assets/ff0d68aa-e470-4508-afb2-d3e56ddbdf56)

![Screenshot from 2024-11-14 00-00-18](https://github.com/user-attachments/assets/96fb275c-12be-4704-ab32-788e3f0b3406)

![Screenshot from 2024-11-14 00-01-07](https://github.com/user-attachments/assets/90c08213-dbeb-409f-85c3-25ab5b91adb3)

![Screenshot from 2024-11-14 00-01-19](https://github.com/user-attachments/assets/f2e031fe-3738-49c6-bbc9-60740195c2fb)

OR gate of drive strength 2 is driving 4 fanouts
![Screenshot from 2024-11-14 00-03-02](https://github.com/user-attachments/assets/ddc58d95-5865-40ea-97c3-11de2e877668)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Result - slack reduced
![Screenshot from 2024-11-14 00-05-44](https://github.com/user-attachments/assets/ce7286e2-a1d9-4a99-abed-935b14445900)

![Screenshot from 2024-11-14 00-06-02](https://github.com/user-attachments/assets/d2b8d38c-b960-4dd8-830b-6e2388d5f42a)

![Screenshot from 2024-11-14 00-06-13](https://github.com/user-attachments/assets/448acb61-7700-480d-a2ac-a3b79069564f)

OR gate of drive strength 2 driving OA gate has more delay
![Screenshot from 2024-11-14 00-07-33](https://github.com/user-attachments/assets/5471721e-1467-4c8b-9da5-ac8244bd92d4)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11643_

# Replacing cell
replace_cell _14481_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Result - slack reduced
![Screenshot from 2024-11-14 00-12-53](https://github.com/user-attachments/assets/dc21725c-f9b3-406e-821b-5bee2510cab2)

OR gate of drive strength 2 driving OA gate has more delay

Screenshot from 2024-03-26 10-32-27

![Screenshot from 2024-11-14 00-13-44](https://github.com/user-attachments/assets/7eb26c49-afa4-4831-9bac-dc54cbe20bf1)

![Screenshot from 2024-11-14 00-14-53](https://github.com/user-attachments/assets/1723c0a4-fc16-4cb0-93b1-205dbe169713)

![Screenshot from 2024-11-14 00-15-29](https://github.com/user-attachments/assets/b2a25ec5-9e30-49c3-bbe6-b0ba7decb8cd)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Result - slack reduced
![Screenshot from 2024-11-14 00-15-29](https://github.com/user-attachments/assets/16e4c2c0-7bbc-4f28-ac9d-71a0e411cf0a)


Commands to verify instance _14506_ is replaced with sky130_fd_sc_hd__or4_4
```
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```
Screenshot of replaced instance
![Screenshot from 2024-11-14 00-17-25](https://github.com/user-attachments/assets/ff7e1c3f-b3f5-475b-b271-41b062d3c547)

11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use write_verilog and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist
```
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_17-46/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```

Screenshot of commands run
![Screenshot from 2024-11-14 00-22-26](https://github.com/user-attachments/assets/363a78c0-63d3-406d-82c9-bf96b2b9be8d)

Commands to write verilog
```
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_17-46/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

Screenshot of commands run
![Screenshot from 2024-11-14 00-28-13](https://github.com/user-attachments/assets/45ae7228-c07f-4029-a849-dccd3d3e756e)

Verified that the netlist is overwritten by checking that instance _14506_ is replaced with sky130_fd_sc_hd__or4_4
![Screenshot from 2024-11-14 00-33-38](https://github.com/user-attachments/assets/ebe9cfe9-ae4c-4956-9222-1e9043ab8a5d)


Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages
```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```

Screenshots of commands run
![Screenshot from 2024-11-14 00-37-21](https://github.com/user-attachments/assets/a27b6652-db92-4efe-91ce-079765d0c97b)

![Screenshot from 2024-11-14 00-40-26](https://github.com/user-attachments/assets/96d23e86-4fd8-4e71-8149-4c8885cd3f9e)

![Screenshot from 2024-11-14 00-41-43](https://github.com/user-attachments/assets/248c1f0f-78ac-476c-a853-bde9d09d11ad)

![Screenshot from 2024-11-14 01-04-26](https://github.com/user-attachments/assets/7ecccfeb-ae43-4550-804c-8fe60ece8806)



12. Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD
```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```
Screenshots of commands run and timing report generated
![Screenshot from 2024-11-14 01-45-52](https://github.com/user-attachments/assets/3f98118a-bbcf-48f1-9be4-d1cec82e8112)

![Screenshot from 2024-11-14 01-50-24](https://github.com/user-attachments/assets/827bdc26-92fd-4da2-819a-096127da8325)


13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing CTS_CLK_BUFFER_LIST
```
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```
Screenshots of commands run and timing report generated
![Screenshot from 2024-11-14 02-24-00](https://github.com/user-attachments/assets/d3b99526-f270-49b4-aced-330d8574c290)

![Screenshot from 2024-11-14 02-27-37](https://github.com/user-attachments/assets/2947f3dd-6c63-431c-be2c-3548be5185d8)


</details>



 <details>
  <summary>Day5 </summary>

##  Final steps for RTL2GDS using tritonRoute and openSTA 

1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 
```

Screenshots of power distribution network run
![Screenshot from 2024-11-14 02-31-41](https://github.com/user-attachments/assets/00382a5e-c25d-425a-a9d6-ca4530aa0ef3)

![Screenshot from 2024-11-14 02-33-37](https://github.com/user-attachments/assets/bd143c9f-94ed-4fdc-9a67-620c93952df5)

![Screenshot from 2024-11-14 02-41-46](https://github.com/user-attachments/assets/c019ff9b-3ecf-4780-b7d2-dc7b3394e74f)

Commands to load PDN def in magic in another terminal
```
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_21-01/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```
Screenshots of PDN def
![Screenshot from 2024-11-14 02-45-23](https://github.com/user-attachments/assets/28fdf1ac-c878-46b0-ac1d-f3b1aa161207)

![Screenshot from 2024-11-14 02-47-05](https://github.com/user-attachments/assets/cb33d79c-2f80-4dff-bbb2-78883e0966ac)

![Screenshot from 2024-11-14 02-47-31](https://github.com/user-attachments/assets/b9729a61-926f-4fe7-9698-1d5197ddad81)

![Screenshot from 2024-11-14 02-48-39](https://github.com/user-attachments/assets/a7c767d7-eb08-4153-9b9c-d367798137ec)

2. Perfrom detailed routing using TritonRoute and explore the routed layout.

Command to perform routing
```
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```
Screenshots of routing run

![Screenshot from 2024-11-14 02-52-32](https://github.com/user-attachments/assets/23cbd99a-ec5c-4c8d-9467-98a240c319f9)

![Screenshot from 2024-11-14 03-05-31](https://github.com/user-attachments/assets/a27d7b2d-ea51-4263-b42d-9168bc06f164)

![Screenshot from 2024-11-14 03-05-49](https://github.com/user-attachments/assets/749f3a4b-abe5-4c94-9549-e79cbaf7acc4)

Commands to load routed def in magic in another terminal
```
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_21-01/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
Screenshots of routed def
![Screenshot from 2024-11-14 03-09-59](https://github.com/user-attachments/assets/713e339f-c2ff-4d4d-a1b5-704a0e451c0d)

![Screenshot from 2024-11-14 03-10-23](https://github.com/user-attachments/assets/7bb00ff3-c032-4028-8d2b-1c00cb0639af)

![Screenshot from 2024-11-14 03-11-38](https://github.com/user-attachments/assets/9af6de56-9dee-4f20-af55-87d4f8822e40)

![Screenshot from 2024-11-14 03-14-56](https://github.com/user-attachments/assets/88bfc151-e6ba-4e77-bf0e-d12a2fe90879)

Screenshot of fast route guide present in openlane/designs/picorv32a/runs/13-11_21-01/tmp/routing directory
![Screenshot from 2024-11-14 03-19-55](https://github.com/user-attachments/assets/3bec9efa-2568-4254-9913-e200fb6db1c5)

3. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD
```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/13-11_21-01/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/13-11_21-01/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/13-11_21-01/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/13-11_21-01/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![Screenshot from 2024-11-14 03-34-13](https://github.com/user-attachments/assets/f82c494b-88c1-4236-b3c9-0282e50d85cd)

![Screenshot from 2024-11-14 03-34-58](https://github.com/user-attachments/assets/12230a30-5d78-48bb-8c98-e2b15944788c)

![Screenshot from 2024-11-14 03-35-04](https://github.com/user-attachments/assets/918cc29a-67f7-4707-b692-0aa4158e9f37)

![Screenshot from 2024-11-14 03-35-08](https://github.com/user-attachments/assets/75cb03ff-222c-488a-9ac4-3a3d55a3d4fe)


</details>
