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

# Lab10:Static Timing Analysis for Synthesized Risc-V Core using OpenSTA

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


![Screenshot from 2024-10-28 18-36-50](https://github.com/user-attachments/assets/6813a809-9b5e-4210-8bfa-c17a2bafa273)


![Screenshot from 2024-10-28 18-37-28](https://github.com/user-attachments/assets/432c713f-42a9-4e66-b75d-f9fe8d3f7f94)

### The max path report indicates Setup Slack while the min path report shows Hold Slack measurements.




</details>
  


