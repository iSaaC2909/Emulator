# MOS 6502 CPU Emulator


## Key Features
- Complete MOS 6502 instruction set implementation
- Cycle-accurate emulation
- Interrupt handling (IRQ, NMI, Reset)
- Memory read/write callback system
- Easy integration with other projects

## Project Files
- `mos6502.h` - CPU emulator header
- `mos6502.cpp` - Core implementation
- `other.py` - Utility functions

A complete MOS 6502 CPU emulator implementation written in C++. This emulator provides accurate emulation of the iconic MOS Technology 6502 processor, which was used in many classic computers and gaming systems including the Apple II, Commodore 64, and Nintendo Entertainment System (NES).

## Features

- Full implementation of all official 6502 opcodes
- Accurate CPU cycle counting
- Support for all addressing modes
- Interrupt handling (IRQ, NMI)
- Configurable memory read/write callbacks
- Clock cycle callback support
- Register state access and control
- Flexible execution control (cycle-based or instruction-based)

## Requirements

- C++ compiler with C++11 support
- Standard C++ libraries

## Project Structure

- `mos6502.h` - Header file containing the CPU class definition and interface
- `mos6502.cpp` - Implementation of the CPU emulator
- `other.py` - Additional utilities and tools

## Usage

### Basic Integration

```cpp
#include "mos6502.h"

// Define memory read callback
uint8_t ReadMemory(uint16_t address) {
    // Implement your memory read logic here
    return memory[address];
}

// Define memory write callback
void WriteMemory(uint16_t address, uint8_t value) {
    // Implement your memory write logic here
    memory[address] = value;
}

// Optional clock cycle callback
void ClockTick(mos6502* cpu) {
    // Called for each clock cycle
}

// Create CPU instance
mos6502 cpu(ReadMemory, WriteMemory, ClockTick);

// Reset the CPU
cpu.Reset();

// Run for specific number of cycles
uint64_t cycleCount = 0;
cpu.Run(1000000, cycleCount, mos6502::CYCLE_COUNT);
```

### Register Access

The emulator provides methods to access and modify CPU registers:

```cpp
uint8_t accumulator = cpu.GetA();  // Get accumulator value
uint8_t xRegister = cpu.GetX();    // Get X register value
uint8_t yRegister = cpu.GetY();    // Get Y register value
uint8_t status = cpu.GetP();       // Get status register
uint8_t stackPtr = cpu.GetS();     // Get stack pointer
uint16_t programCounter = cpu.GetPC(); // Get program counter
```

## Technical Details

### Addressing Modes

The emulator supports all 6502 addressing modes:
- Accumulator
- Immediate
- Zero Page
- Zero Page,X
- Zero Page,Y
- Absolute
- Absolute,X
- Absolute,Y
- Indirect
- Indexed Indirect (X)
- Indirect Indexed (Y)
- Relative

### Interrupts

The emulator handles the following interrupts:
- Reset (RST)
- Non-Maskable Interrupt (NMI)
- Interrupt Request (IRQ)

## License

[License information to be added]

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Version History

- Version 1.0: Initial release
  - Complete implementation of MOS 6502 CPU
  - Full instruction set support
  - Cycle-accurate emulation 
