# ASIC-Design-class
# Lab1A: Create a small C program and compile it using gcc compiler.Verify the output of the C program after execution.

Step1: Write the C Code in a file Using any text editor and save it as sum1ton.c(source code).


![2024-07-17 (14)](https://github.com/user-attachments/assets/4d2d6965-6021-4712-b226-601d0c1e8c5d)
![2024-07-17 (16)](https://github.com/user-attachments/assets/cdc76027-8f42-42c8-97b9-a337e80b36dc)

Step2: Now compile the source code using gcc compiler,this will generate the executable code.

![2024-07-17 (17)](https://github.com/user-attachments/assets/0ccf1314-7811-4a9b-b827-bb39adaa89bd)

Step3: Lastly run the executable code to see the output.

![2024-07-17 (18)](https://github.com/user-attachments/assets/a91a1be2-d6d0-4998-9c0a-187adf80448d)




# Lab1B: Compiling a c code with RISC-V compiler and using O1 and Ofast.

step1: Compile the code using RISC-V GCC

![2024-07-17 (20)](https://github.com/user-attachments/assets/1524a9d4-8bac-4ddc-96bc-3d236a49f10b)

![2024-07-17 (21)](https://github.com/user-attachments/assets/dd8ec7b2-d473-49d4-8728-270074c34124)

Step2: Now put the O1 and Ofast Command and observe the output 


![2024-07-18](https://github.com/user-attachments/assets/7baa5530-8ae6-446e-881e-2f8ca4569655)

![2024-07-18 (6)](https://github.com/user-attachments/assets/0e0290ff-883f-40a4-b84e-4fee7cca445e)

![2024-07-18 (7)](https://github.com/user-attachments/assets/dfbc48ec-27b1-4ee0-96f3-945888665c7b)

![2024-07-18 (9)](https://github.com/user-attachments/assets/b35835eb-7a65-4a8d-a907-02f0262091fe)

# Lab2: Execution of the object file created by the RISC-V GCC compiler using Spike Simulator.

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





# Task3 :

Task A] Identify various RISC V instruction types
        
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

**Various RISC V instruction types are**

R-type (Register): Encodes arithmetic and logical operations. The format is funct7 rs2 rs1 funct3 rd opcode.

I-type (Immediate): Used for immediate operations and loads. The format is imm[11:0] rs1 funct3 rd opcode.

S-type (Store): Used for store operations. The format is imm[11:5] rs2 rs1 funct3 imm[4:0] opcode.

B-type (Branch): Used for branch operations. The format is imm[12] imm[10:5] rs2 rs1 funct3 imm[4:1] imm[11] opcode.

U-type (Upper immediate): Used for immediate values for upper immediate operations. The format is imm[31:12] rd opcode.

J-type (Jump): Used for jump operations. The format is imm[20] imm[10:1] imm[11] imm[19:12] rd opcode.




Decoding the given instruction type wise, the tabular representation of Hexadecial and 32 bit decimal equivalent is shown below.


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




# Task B]: Running assembly instructions according to the provided Verilog code in a RISC=V processor.

For the given verilog code and the instructions, the Bit pattern and the ISA according to the code can be viwed as below

<img width="304" alt="329132362-24cc896a-7817-4941-be7f-95d44c35d4d8" src="https://github.com/user-attachments/assets/1bfc8217-fb15-406f-bf7d-fabd327becde">

Download the two files iiitb_rv32i.v and iiitb_rv32i_tb.v , save them in same folder and put the below command to execute and run the code.After that put the gtkwave command to get the waveforms
(for simplicity5 )




| Operation          | Hardcoded ISA | Binary Equivalent                  |
|--------------------|---------------|-----------------------------------|
| ADD R6, R2, R1    | 32'h02208300   | 0000 0010 0010 0000 1000 0011 0000 0000 |
| SUB R7, R1, R2    | 32'h02209380   | 0000 0010 0010 0000 1001 0011 1000 0000 |
| AND R8, R1, R3    | 32'h0230a400   | 0000 0010 0011 0000 1010 0100 0000 0000 |
| OR R9, R2, R5     | 32'h02513480   | 0000 0010 0101 0001 0011 0100 1000 0000 |
| XOR R10, R1, R4   | 32'h0240c500   | 0000 0010 0100 0000 1100 0101 0000 0000 |
| SLT R1, R2, R4    | 32'h02415580   | 0000 0010 0100 0001 0101 0101 1000 0000 |
| ADDI R12, R4, 5   | 32'h00520600   | 0000 0000 0101 0010 0000 0110 0000 0000 |
| BEQ R0, R0, 15    | 32'h00f00002   | 0000 0000 1111 0000 0000 0000 0000 0010 |
| SW R3, R1, 2      | 32'h00209181   | 0000 0000 0010 0000 1001 0001 1000 0001 |
| LW R13, R1, 2     | 32'h00208681   | 0000 0000 0010 0000 1000 0110 1000 0001 |
| SRL R16, R14, R2  | 32'h00271803   | 0000 0000 0010 0111 0001 1000 0000 0011 |
| SLL R15, R1, R2   | 32'h00208783   | 0000 0000 0010 0000 1000 0111 1000 0011 |

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





The custom instructions given for individual are:


| Instruction       | Hexadecimal Encoding | 32-bit Binary Encoding                           |
|-------------------|-----------------------|---------------------------------------------------|
| ADD r9, r10, r11  | `0x00B292B3`          | `0000000 01010 01011 000 01001 0110011`         |
| SUB r11, r9, r10  | `0x400292B3`          | `0100000 01010 01001 000 01011 0110011`         |
| AND r10, r9, r11  | `0x00B292B3`          | `0000000 01001 01011 111 01010 0110011`         |
| OR  r8, r10, r5   | `0x00A292B3`          | `0000000 01010 00101 110 01000 0110011`         |
| XOR r8, r9, r4    | `0x00A292B3`          | `0000000 01001 00100 100 01000 0110011`         |
| SLT r00, r1, r4   | `0x00129233`          | `0000000 00001 00100 010 00000 0110011`         |
| ADDI r02, r2, 5   | `0x0002 0203`         | `000000000101 00010 000 00010 0010011`         |
| LW   r03, r01, 2  | `0x0001 0323`         | `000000000010 00001 010 00011 0000011`         |
| SRL r06, r01, r1  | `0x0001 5653`         | `0000000 00001 00001 101 00110 0010011`         |
| BNE r0, r0, 20    | `0x0000 A0E3`         | `00000000010100 00000 001 00000 1100011`       |
| BEQ r0, r0, 15    | `0x0000 0003`         | `00000000001111 00000 000 00000 1100011`       |
| SLL r05, r01, r1  | `0x0001 2523`         | `0000000 00001 00001 001 00101 0110011`         |








 



