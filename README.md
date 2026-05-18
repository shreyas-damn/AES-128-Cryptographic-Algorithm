# AES-128 Encryptor in Verilog

A hardware implementation of the AES-128 encryption algorithm using Verilog HDL.  
This project focuses on building a modular RTL-based AES encryptor for FPGA implementation and digital design learning.

---

## Project Overview

AES (Advanced Encryption Standard) is a symmetric block cipher used for secure data encryption.

This project implements:

- AES-128 encryption
- 128-bit plaintext input
- 128-bit key input
- 10-round AES architecture
- Modular RTL design
- FSM-controlled datapath

The design is intended for:
- RTL learning
- FPGA experimentation
- Digital design practice
- Cryptography hardware understanding

---

## AES Encryption Flow

The AES encryptor performs the following steps:

1. AddRoundKey
2. SubBytes
3. ShiftRows
4. MixColumns
5. Repeat for 10 rounds

The final round excludes MixColumns.

---

## RTL Blocks

- State Register
- SubBytes (S-box)
- ShiftRows
- MixColumns
- AddRoundKey
- Key Expansion
- FSM Controller
- Round Counter

---

## Project Structure

```text
aes_128/
│
├── README.md
├── encryptor/
│   ├── docs/
│   ├── rtl/
│   ├── scripts/
│   ├── sim/
│   └── tb/
│
└── decryptor/
    ├── docs/
    ├── rtl/
    ├── scripts/
    ├── sim/
    └── tb/
