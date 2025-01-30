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
