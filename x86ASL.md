## x86 Assembly Language
The general form of an assembly instruction is *mnemonic operand(s)*

An ```assembler``` is a program that reads a text file with assembly instructions and converts the assembly into machine code.

### Instruction Operands
- ```register```: These operands refer directly to the contents of the CPU's register.
- ```memory```: These refer to data in memory. The address of the data maybe a constant hard-coded into the instruction pr maybe computed using values of registers.
- ```immediate```: These are fixed values that are listed in the instruction itself. They are stored in the **code segment** not the data segment.
- ```implied```: These operands are not explicitly shown. For example, the increment instruction adds one to a register or memory. The **one** is implied.

### Basic Instructions
The most basic instruction is the ```MOV``` instruction. It moves data from one location to another (like the assignment operator).

```console
mov dest, src
```

#### Rules/Restrictions:
 - Both operands may not be memory operands.
 - Both operands must also be the same size.


 Example:

 ```console
 mov  eax, 3    ; store 3 into EAX register (3 is immediate operand)
 mov  bx, ax    ; store the value of AX into BX register
 ```

 The ADD instruction is used to add integers.

 ```console
 add  eax, 4    ; eax = eax + 4
 add  al, ah    ; al = al + ah
 ```

 The SUB instruction subtracts integers

 ```console
 sub  bx, 10    ; bx = bx - 10
 sub  ebx, edi  ; ebx = ebx - edi
 ```

 The INC and DEC instructions increment or decrement values by one.

 ```console
 inc  ecx   ; ecx++
 dec  dl    ; dl--
 ```     

 ### Directives
 - A **directive** is an artifact of the assembler not the CPU.
 - They are used to either instruct the assembler to do something or inform the assembler of something.
 - They are no translated into machine code.

 Common uses:
  - Define constants
  - Define memory to store dat instruction
  - Group memory into segments
  - Conditionally include source code
  - Include other files

  #### **equ directive**
  Used to define a ***symbol***. Symbols are named constants that can be used in the assembly program.

  - ```symbol equ value```

  #### **%define directive**
  Used to define constant macros just as in C.

  ```console
  %define SIZE 100
      mov  eax, size
  ```

  #### Data Directives
  **Data directives** are used in data segments to define room for memory. There are two ways memory can be reserved.  

  The first way only defines room for data; the second way defines room and an initial value. The first method uses one of the ```RESX``` directives. The *X* is replaced with a letter that determines the size of the object (or objects) that will be stored.

  The second method (that defines an initial value, too) uses one of the ```DX``` directives. The *X* letters are the same as those in the ```RESX``` directives.

  Table showing the letter for ```RESX``` and ```DX``` directives:

  | Unit | Letter|
  | ---- | ---- |
  | byte | B |
  | word | W |
  | double word | D |
  | quad word | Q |
  | ten bytes | T |

  It is very common to mark memory locations with **labels**. Labels allow one to easily refer to memory locations in code.

  Below are several examples:

  ```console
  L1  db  0       ; byte labeled L1 with initial value 0
  L2  dw  1000    ; word labeled L2 with initial value 1000
  L3  db  110101b ; byte initialized to binary 110101 (53 in decimal)
  L4  db  12h     ; byte initialized to hex 12 (18 in decimal)
  L5  db  17o     ; byte initialized to octal 17 (15 in decimal)
  L6  dd  1A92h   ; double word initialized to hex 1A92
  L7  resb  1     ; 1 uninitialized byte
  L8  db  "A"     ; byte initialized to ASCII code for A (65)
  ```

  Sequences of memory may also be defined:

  ```console
  L9   db   0, 1, 2 , 3             ; defines 4 bytes
  L10  db   "w", "o", "r", 'd', 0   ; defines a C string = "word"
  L11  db   'word', 0               ; same as L10
  ```

  The ```DD``` directive can be used to define both integer and single precision floating point constants.

  The ```DQ``` directive can only be used to define double precision floating point constants.
