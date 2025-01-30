# 6502-Emulator
An emulator for a modified 6502 assembly with a build in compiler and editor  
- 64K Memory Addresses
- A, X and Y Registers
- 52 OpCodes
- Text Output

# Instructions and Syntax:
All instructions begin with an mnemonic, a 3-letter code such as - `lda`  
After each mnemonic, depending on the type will be followed by a value, either an immediate, repsented by the `$` prefix or a memory address, represented by the `#$` prefix. Values can be is decimal, hex `0x` or binary `0b`.  
Instructions which have a value that can be an immediate or memory adress may also be followed by `X` or `Y`, at runtime their value will be ofset by the corresponding register  
**Example Code:**  
```
lda $0x50    ;Loads 80 into A register
ldx $4       ;Loads 4 into X register
sta #$0x2 X  ;Stores A(50) at memory address 6, 4+X(2)
```
**Other Syntax:**  
To load data directly into memory on load type the `$` prefix followed by a memory address, `=` and then you data, separated by spaces. This will load the data into memory starting at the specified address, each value or charactor(for strings) will be loaded into a separate location  
**Example Code:**  
```
$2 = 5 8 "Hi"
```
The value 5 is stored at address 2, 8 at address 3, 72(H in ASCII) at 4, and 105(i in ASCII) at 5  
**Labels:**  
Labels are writen startign with `.` , ending with `:` and are one world. Jump Instructions can used them as a replacement for the line number. Along with values direcly put into memory labels do not get executed and therefor do not count as a line when giving a jump instruction a line value. Jump instructions include: `jmp` `beq` `bne` `bcc` `bcs` `bmi` `mne` `bvc` `bvc` and `jsr`.  
**Example Code:**  
```
.loop:   ;This is a label
inx      ;Increment X register
cmx $12  ;Compare X register to 12
bne loop ;Continue to loop until X equals 12
```
# Full Instruction Set:
| Instruction | Value | Description |
|------------|-------|-------------|
| nop        | No    | Does nothing (NOP) |
| lda        | Yes   | Load a value into the accumulator (LDA) |
| ldx        | Yes   | Load a value into the X register (LDX) |
| ldy        | Yes   | Load a value into the Y register (LDY) |
| sta        | Yes   | Store the accumulator value in memory (STA) |
| stx        | Yes   | Store the X register value in memory (STX) |
| sty        | Yes   | Store the Y register value in memory (STY) |
| adc        | Yes   | Add a value to the accumulator with the carry (ADC) |
| sbc        | Yes   | Subtract a value from the accumulator with the carry (SBC) |
| and        | Yes   | Perform a bitwise AND on the accumulator (AND) |
| ora        | Yes   | Perform a bitwise OR on the accumulator (ORA) |
| eor        | Yes   | Perform a bitwise XOR on the accumulator (EOR) |
| cmp        | Yes   | Compare accumulator with value (CMP) |
| cpx        | Yes   | Compare X register with value (CPX) |
| cpy        | Yes   | Compare Y register with value (CPY) |
| bit        | Yes   | Test bits in a memory location against the accumulator (BIT) |
| inc        | Yes   | Increment the value at the memory location by 1 (INC) |
| inx        | No    | Increment the X register by 1 (INX) |
| iny        | No    | Increment the Y register by 1 (INY) |
| dec        | Yes   | Decrement the value at the memory location by 1 (DEC) |
| dex        | No    | Decrement the X register by 1 (DEX) |
| dey        | No    | Decrement the Y register by 1 (DEY) |
| bcc        | Yes   | Branch if carry is clear (BCC) |
| bcs        | Yes   | Branch if carry is set (BCS) |
| beq        | Yes   | Branch if zero flag is set (BEQ) |
| bmi        | Yes   | Branch if negative flag is set (BMI) |
| bne        | Yes   | Branch if zero flag is clear (BNE) |
| bpl        | Yes   | Branch if negative flag is clear (BPL) |
| bvc        | Yes   | Branch if overflow flag is clear (BVC) |
| bvs        | Yes   | Branch if overflow flag is set (BVS) |
| jmp        | Yes   | Jump to a specified address (JMP) |
| jsr        | Yes   | Jump to a subroutine (JSR) |
| rts        | No    | Return from subroutine (RTS) |
| pha        | No    | Push accumulator onto the stack (PHA) |
| php        | No    | Push processor status onto the stack (PHP) |
| pla        | No    | Pull accumulator from the stack (PLA) |
| plp        | No    | Pull processor status from the stack (PLP) |
| tax        | No    | Transfer accumulator to X register (TAX) |
| tay        | No    | Transfer accumulator to Y register (TAY) |
| txa        | No    | Transfer X register to accumulator (TXA) |
| tya        | No    | Transfer Y register to accumulator (TYA) |
| tsx        | No    | Transfer stack pointer to X register (TSX) |
| txs        | No    | Transfer X register to stack pointer (TXS) |
| rol        | No    | Rotate left (ROL) |
| ror        | No    | Rotate right (ROR) |
| lsr        | No    | Logical shift right (LSR) |
| lsl        | No    | Logical shift left (LSL) |
| wrt        | Yes   | Output direct |
| wrb        | Yes   | Output buffer |
| dsb        | No    | Display buffer |
| clb        | No    | Clear screen buffer |
| cls        | No    | Clear screen |
| ssb        | No    | Set screen buffer |

