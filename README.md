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


![14(Branch inst)](https://github.com/user-attachments/assets/61ed15f0-c268-468f-8512-4427c2a2dafd)


![14(Branch inst with waveform)](https://github.com/user-attachments/assets/c35ea895-1eff-4454-8bed-ef2526c296a0)

 



