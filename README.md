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
```

## State Table
```text
STATE        | ACTION (DATAPATH OPERATION)                          | NEXT STATE
------------------------------------------------------------------------------------
IDLE         | Wait for start signal                                | LOAD

LOAD         | Load plaintext into state register                    | ROUND_0

ROUND_0      | state = state XOR round_key[0]                        | ROUND_1

ROUND_1      | SubBytes → ShiftRows → MixColumns → AddRoundKey[1]   | ROUND_2

ROUND_2      | SubBytes → ShiftRows → MixColumns → AddRoundKey[2]   | ROUND_3

ROUND_3      | SubBytes → ShiftRows → MixColumns → AddRoundKey[3]   | ROUND_4

ROUND_4      | SubBytes → ShiftRows → MixColumns → AddRoundKey[4]   | ROUND_5

ROUND_5      | SubBytes → ShiftRows → MixColumns → AddRoundKey[5]   | ROUND_6

ROUND_6      | SubBytes → ShiftRows → MixColumns → AddRoundKey[6]   | ROUND_7

ROUND_7      | SubBytes → ShiftRows → MixColumns → AddRoundKey[7]   | ROUND_8

ROUND_8      | SubBytes → ShiftRows → MixColumns → AddRoundKey[8]   | ROUND_9

ROUND_9      | SubBytes → ShiftRows → MixColumns → AddRoundKey[9]   | ROUND_10

ROUND_10     | SubBytes → ShiftRows → AddRoundKey[10] (NO MixColumns) | DONE

DONE         | Output ciphertext, assert done signal                 | IDLE

```

