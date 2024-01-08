# 32-Bit CPU Project

## 1-bit ALU

The 32-bit CPU project utilizes a modular architecture with a main file and interconnected subfiles. The foundational block is a 1-bit Arithmetic Logic Unit (ALU), featuring AND, OR, NAND, NOR, ADD, SUBTRACT, and SET LESS THAN operations. The ALU employs a 4-bit control signal, with 2 bits for the result multiplexer and 2 for inverting either input. Detailed logic is integrated into the ALU for operations such as equality checking, negative result determination, and the detection of signed and unsigned overflow.
![image](https://github.com/Mikeantabian/Logisim-CPU/assets/119545472/e02c0412-809c-4c62-aee2-c257356f9a6d)

## 32-Bit ALU

Subsequently, 32 instances of the 1-bit ALU are connected to form a 32-bit ALU, with carry-out connections between blocks. The design includes additional logic for equality checking, negative result determination, and overflow detection. Equality checking involves subtracting inputs and verifying the result is zero. Negative result determination is based on examining the most significant bit of the output. For overflow, the architecture checks for unsigned overflow by examining the final carry-out, while signed overflow is determined by comparing the signs of inputs and outputs.

## Register System

Another subfile focuses on registers, consisting of 32 synchronous D flip-flops arranged in series to handle 32-bit inputs and outputs. This register block is utilized in a "register group" subfile, where 32 register blocks are interconnected. Muxes facilitate the reading of data from specific registers based on 5-bit select lines. A write mechanism employs a decoder to determine the target register.

## Control Logic

The project also includes a separate control block subfile for interpreting instruction sets, determining the operation type, and generating select lines for subsequent stages. An additional subfile, the ALU control block, is implemented to determine the ALU operation based on its inputs.
![image](https://github.com/Mikeantabian/Logisim-CPU/assets/119545472/ff2e2cfe-9f4f-4432-bfc2-028ebad55440)
![image](https://github.com/Mikeantabian/Logisim-CPU/assets/119545472/91803f7e-8486-402e-a002-7fdb4154bed8)

## Integration and Execution

All these subfiles, along with other necessary components, are integrated into the main file to form a complete 32-bit processor. The processor follows a fetch-decode-execute cycle: it fetches a 32-bit instruction, decodes it using the ALU control and control blocks, performs the corresponding operation, which involves registers in adherence to a RISC-based approach, and updates the program counter—a 32-bit register—to fetch the next instruction based on the type of instruction executed.
