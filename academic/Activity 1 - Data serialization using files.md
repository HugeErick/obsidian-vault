
## Team members

Erick Gonzalez Parada ID: 178145
Andre Francois Duhamel Gutierrez ID: 177315
Emiliano Ruiz Plancarte ID: 177478
Antonio Gutiérrez Blanco ID: 177442
Emilio Zavala Miceli 176895

## Abstract

This project implements two simple C programs, `marshall.c` and `unmarshall.c`, that demonstrate data serialization and deserialization. The objective is to learn concepts of computer architecture, particularly memory representation, endianness, and data alignment, by storing and retrieving structured data from a binary file.

## Keywords

- Marshalling
- Unmarshalling
- Endianness
- Data Alignment
- Computer Architecture

## Objective

The primary objective of this work is to gain hands-on experience with memory representation and data management in C. By explicitly converting between little-endian and big-endian formats, we as a team learn how computer architecture influences data storage and portability.

## Theoretical Framework

### Glossary

- **Little Endian**: A memory storage scheme where the least significant byte of a word is stored at the lowest memory address. Common on x86 processors.
- **Big Endian**: A storage scheme where the most significant byte of a word is stored at the lowest memory address. Often used in network protocols and some RISC architectures.
- **Data Alignment**: The organization of data in memory according to hardware constraints, typically requiring certain data types to begin at addresses divisible by their size (e.g., a 4-byte integer aligned to a 4-byte boundary).

## Examples


### Byte ordering formats (i.e big endian and small endian)

![[archbits1.png]]

### Memory alignment
![[padding.png]]
## Methodology

1. Define global variables (`c1`, `c2`, `i`, `c3`, `c4`).
2. Implement `marshall.c` to:
   - Write characters and integers to a file in the specified order.
   - Convert the integer to big-endian format manually.
3. Implement `unmarshall.c` to:
   - Read the data back.
   - Convert the integer from big-endian to the host’s format.
   - Store the result in 64-bit variables.
4. Verify correctness by dumping the file with e.g `hexdump -C data.bin`.

## Implementation

- A Makefile was written for Linux and Windows builds.
- The `marshall` program creates `data.bin` with data in big-endian representation.
- The `unmarshall` program reads and adapts the data, printing it to the screen.

## Conclusion

This exercise highlights the importance of understanding memory representation and system architecture when exchanging binary data. Endianness and alignment are crucial factors in cross-platform development. Practical exercises such as this one help bridge the gap between theoretical computer architecture and real-world programming.

## References

- [GeeksforGeeks: Endianness in Computer Architecture](https://www.geeksforgeeks.org/little-and-big-endian-mystery/)
- [Intel Developer Zone: Data Alignment](https://www.intel.com/content/www/us/en/docs/intrinsics-guide/index.html)
- [ISO/IEC 9899:2018 C Standard](https://www.iso.org/standard/74528.html)
- [MSI Knowledge Base: Understanding Data Alignment](https://www.msi.com)
- [IETF RFC 1700: Network Byte Order (Big Endian)](https://www.rfc-editor.org/rfc/rfc1700)

