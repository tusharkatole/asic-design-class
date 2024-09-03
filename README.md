# ASIC-Design-class
# Lab 1A: Create a small C program and compile it using gcc compiler.Verify the output of the C program after execution.
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

 
# Lab 2: Execution of the object file created by the RISC-V GCC compiler using Spike Simulator.

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





# Lab 3 :Identify various RISC-V instruction types and running assembly instructions according to the provided Verilog code in a RISC-V processor.

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

# Lab 4: To write an Application in C and compile it with gcc and Risc-v gcc
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

# Lab 5:To design a Baisc Risc-V processor core using TL-Verilog on Makerchip.

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

# Lab 6:Convert the TLV to verilog using Sandpiper and then use GTKWave pre-synthesis simulation to verify the design.

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

# Lab 7:Addition of Peripherals to convert the Digital output to analog output using DAC and PLL


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








