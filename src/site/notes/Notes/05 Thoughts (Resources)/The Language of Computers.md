---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/notes/05-thoughts-resources/the-language-of-computers/","dgPassFrontmatter":true,"updated":"2026-10-13T18:16:15.379+05:30"}
---

# The Language of Computers
## A Complete Guide to Binary, Hexadecimal (HEX), and Base64

---

# Introduction

Computers do not understand English, Spanish, Hindi, or any human language directly. Every piece of information inside a computer—text, numbers, images, videos, music, and programs—is ultimately represented as **binary digits (bits)**.

Humans use numbering systems like decimal (Base-10), but computers use **Binary (Base-2)** because electronic circuits have only two stable states:

- ON (1)
- OFF (0)

To make binary easier for humans to read and write, engineers created systems such as **Hexadecimal (Base-16)** and **Base64**.

---

# Number Systems Overview

| Name | Base | Symbols Used |
|------|------|--------------|
| Binary | 2 | 0–1 |
| Octal | 8 | 0–7 |
| Decimal | 10 | 0–9 |
| Hexadecimal | 16 | 0–9, A–F |
| Base64 | 64 | A–Z, a–z, 0–9, +, / |

---

# 1. Binary (Base-2)

## Definition

Binary is the fundamental language of every digital computer.

Only two digits exist:

```
0
1
```

Each digit is called a **bit**.

---

## Why Computers Use Binary

Electronic devices use transistors.

A transistor has two states:

```
OFF = 0
ON  = 1
```

Modern processors contain billions of these tiny switches.

---

## Bit

A bit is the smallest unit of data.

Example:

```
0
1
```

---

## Nibble

A nibble contains:

```
4 bits
```

Example:

```
1010
```

---

## Byte

A byte contains:

```
8 bits
```

Example:

```
01000001
```

One byte usually stores one character.

---

## Larger Units

| Unit | Size |
|------|------|
| Bit | 1 bit |
| Nibble | 4 bits |
| Byte | 8 bits |
| Kilobyte | 1024 bytes |
| Megabyte | 1024 KB |
| Gigabyte | 1024 MB |
| Terabyte | 1024 GB |

---

# Binary Place Values

```
128 64 32 16 8 4 2 1
```

Example

```
10101100
```

Calculation

```
128 + 32 + 8 + 4

= 172
```

---

# Decimal to Binary

Example

```
13
```

Repeated division

```
13 ÷ 2 = 6 remainder 1

6 ÷ 2 = 3 remainder 0

3 ÷ 2 = 1 remainder 1

1 ÷ 2 = 0 remainder 1
```

Read upward

```
1101
```

---

# Binary to Decimal

Example

```
1101
```

```
1×8

1×4

0×2

1×1

=13
```

---

# Binary Arithmetic

## Addition

```
0+0=0

0+1=1

1+0=1

1+1=10

1+1+1=11
```

Example

```
1010
0011
----
1101
```

---

## Subtraction

```
1-0=1

1-1=0

10-1=1
```

---

## Multiplication

```
0×0=0

0×1=0

1×0=0

1×1=1
```

---

# Binary Logical Operations

## AND

```
1 AND 1 = 1
```

Otherwise

```
0
```

---

## OR

```
1 OR 0 = 1

0 OR 1 = 1

1 OR 1 = 1

0 OR 0 = 0
```

---

## XOR

```
1 XOR 1 = 0

0 XOR 0 = 0

1 XOR 0 = 1

0 XOR 1 = 1
```

---

## NOT

```
NOT 1 = 0

NOT 0 = 1
```

---

# ASCII Example

Letter

```
A
```

ASCII

```
65
```

Binary

```
01000001
```

---

# Unicode Example

Emoji

```
😀
```

Requires multiple bytes using UTF-8.

---

# Binary in Memory

Suppose memory stores

```
01101010
```

This could represent

- Number
- Letter
- Image pixel
- Machine instruction

Interpretation depends on context.

---

# Binary in Images

Black

```
0
```

White

```
1
```

Example

```
11111111
00000000
10101010
```

Color images use multiple bytes.

---

# Binary in Audio

Audio is stored as binary samples.

Example

```
10010101

01100110

11110000
```

---

# Binary in Networking

IP

```
192.168.1.1
```

Binary

```
11000000

10101000

00000001

00000001
```

---

# 2. Hexadecimal (HEX)

## Definition

Hexadecimal is Base-16.

Digits

```
0

1

2

3

4

5

6

7

8

9

A

B

C

D

E

F
```

Where

```
A=10

B=11

C=12

D=13

E=14

F=15
```

---

# Why HEX Exists

Binary becomes very long.

Example

```
1111111111111111
```

HEX

```
FFFF
```

Much easier to read.

---

# Binary to HEX

Group into four bits.

Example

```
110101101111
```

Groups

```
1101

0110

1111
```

Convert

```
1101=D

0110=6

1111=F
```

Answer

```
D6F
```

---

# HEX Table

| Binary | HEX |
|---------|-----|
|0000|0|
|0001|1|
|0010|2|
|0011|3|
|0100|4|
|0101|5|
|0110|6|
|0111|7|
|1000|8|
|1001|9|
|1010|A|
|1011|B|
|1100|C|
|1101|D|
|1110|E|
|1111|F|

---

# HEX to Decimal

Example

```
2F
```

Calculation

```
2×16

+

15

=

47
```

---

# Decimal to HEX

Example

```
255
```

```
255 ÷16

=15 remainder15
```

```
F

F
```

Answer

```
FF
```

---

# Common HEX Prefixes

```
0xFF

#FF0000

0XABCD
```

---

# HEX Color Codes

Red

```
#FF0000
```

Green

```
#00FF00
```

Blue

```
#0000FF
```

White

```
#FFFFFF
```

Black

```
#000000
```

---

# Memory Addresses

Example

```
0x7FFF12AB
```

---

# Machine Code

Assembly debuggers usually display

```
90

B8

FF

E8
```

instead of binary.

---

# 3. Base64

## Definition

Base64 converts binary data into printable text.

It is **an encoding**, not encryption.

---

# Why Base64 Exists

Some systems originally allowed only text.

Binary files had to be converted into printable characters.

---

# Base64 Alphabet

```
ABCDEFGHIJKLMNOPQRSTUVWXYZ

abcdefghijklmnopqrstuvwxyz

0123456789

+

/
```

Padding

```
=
```

---

# Encoding Process

Original text

```
Cat
```

ASCII

```
67

97

116
```

Binary

```
01000011

01100001

01110100
```

Split into 6-bit groups

Convert each group

Final

```
Q2F0
```

---

# Example

Text

```
Hello
```

Base64

```
SGVsbG8=
```

---

# Decoding

```
SGVsbG8=
```

↓

```
Hello
```

---

# Padding

Sometimes

```
=
```

or

```
==
```

is added.

Example

```
QQ==
```

means

```
A
```

---

# Where Base64 is Used

- Email attachments
- HTML images
- JSON APIs
- XML
- JWT Tokens
- OAuth
- QR Codes
- REST APIs
- MIME
- Certificates

---

# Data URI Example

```
data:image/png;base64,
iVBORw0KGgoAAAANSUhEUgAA...
```

---

# Base64 Is NOT Encryption

Wrong

```
Base64 hides data.
```

Correct

```
Base64 only changes representation.

Anyone can decode it.
```

---

# Binary vs HEX vs Base64

| Feature | Binary | HEX | Base64 |
|----------|---------|------|---------|
|Base|2|16|64|
|Readable|Very Low|High|Medium|
|Used by CPU|Yes|No|No|
|Storage|Native|Representation|Representation|
|Compression|No|No|No|
|Encryption|No|No|No|
|Encoding|No|No|Yes|

---

# Comparison Example

Decimal

```
72
```

Binary

```
01001000
```

HEX

```
48
```

ASCII

```
H
```

Base64

```
SA==
```

---

# Real-World Uses

## Binary

- CPU Instructions
- RAM
- SSD
- HDD
- Operating Systems
- Digital Electronics

---

## HEX

- Memory addresses
- Machine code
- Debugging
- CSS colors
- Networking
- Cryptography

---

## Base64

- Web APIs
- Images
- Email
- Authentication
- Data transfer
- Certificates

---

# Advantages

## Binary

- Native computer language
- Reliable
- Electronic simplicity

---

## HEX

- Compact
- Human-readable
- Easy debugging

---

## Base64

- Safe text transport
- Cross-platform
- Internet-friendly

---

# Limitations

## Binary

- Very long
- Difficult to read

---

## HEX

- Only a representation
- Not directly executed

---

## Base64

- Increases data size by approximately 33%
- Not secure
- Not compressed

---

# Summary

| System | Purpose |
|---------|----------|
| Binary | Native language of computers and digital electronics |
| HEX | Human-friendly representation of binary |
| Base64 | Text-safe encoding of binary data for communication and storage |

Together, Binary, Hexadecimal, and Base64 form the foundation of modern computing, enabling everything from CPU instructions and memory management to web communication, networking, multimedia storage, and secure data exchange.