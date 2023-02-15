# Homework Assignment 2 (due Feb 22)

The goal of this assignment is to practice **opening/reading binary files**, **casting**, and  **pointers and memory** in `C`.  The assignment is worth a total of 100 points.  If you have any questions or need any help, please visit us during office hours and/or post questions on `EdStem`.


## `1. Decoding Instructions (50 pts)`
In this problem, your program will take as input a binary file containing instructions from a very small `instruction set`.  The goal of your program is to read through the file and print every instruction and its operands.  The instruction set is very simple, and all instructions follow a uniform encoding:

- 2 bits for the opcode
- 2 bits for a target register
- 2 bits for a source register 1
- 2 bits for a source register 2

The following table shows the available instructions and their corresponding opcodes in binary:

| instruction  | opcode |
| ------------- | ------------- |
| `mul` | 00 |
| `div` | 01 |
| `add` | 10 |
| `sub` | 11 |

You can also assume that all registers are available to the instructions.  There are 4 registers using the following names:

| register  | name | encoding |
| --------- | ---- | -------- |
| x0 | `t0` | 0 |
| x1 | `t1` | 1 |
| x2 | `s0` | 2 |
| x3 | `s1` | 3 |

### Input
Your program will receive the following command line arguments:
```text
<fname> File name for the binary file encoding the instructions
```
The line below shows an example of using your program:
```bash
$ ./decode-inst cases/file-1.bin
```

### Output
Your program should write each instruction to the `stdout` separated by a new line.  

For example, the byte `0x4D` encodes the instruction `div t0, s1, t1`, as it has the corresponding bitstring `01001101`.  

Using a binary file with a single instruction like the example above, your program should output the following values:

```bash
$ ./decode-inst cases/file-1.bin
mul t1, t0, s1
```

## `2. Integer hunter (50 pts)`

The goal of your program is to read through an input binary file and print all occurrences of an integer value `key`, assuming all bytes in the file are encoded using a corresponding `data_type`.

### Input

Your program will receive the following command line arguments:

```text
<fname>      File name for an input binary file
<key>        An integer value (decimal) to be found in the file
<data_type>  The expected byte encoding in the file
    - `1b` or `1l` looks for an unsigned integer stored using 1 byte
    - `2l` looks for an unsigned integer stored using 2 bytes and little-endian encoding
    - `2b` looks for an unsigned integer stored using 2 bytes and big-endian encoding
    - `4l` looks for an unsigned integer stored using 4 bytes and little-endian encoding
    - `4b` looks for an unsigned integer stored using 4 bytes and big-endian encoding
    - `8l` looks for an unsigned integer stored using 8 bytes and little-endian encoding
    - `8b` looks for an unsigned integer stored using 8 bytes and big-endian encoding
```

The line below shows an example of using your program:
```bash
$ ./int-hunter cases/file-16.bin 207 1b
```

### Output

Your program should write each occurrence of `key` to the `stdout` separated by a new line, following the format shown in the example below.  The three columns shown in the example are: 

- offset of the occurrence relative to 0, using 8 hexadecimal digits
- value of the occurrence in hexadecimal, using the corresponding number of digits
- value of the occurrence as an unsigned integer

```bash
$ ./int-hunter cases/file-16.bin 207 1b
0x00000008    0xCF    207
0x00000009    0xCF    207
```


## Submission and Grading
You will submit two files named `decode-inst.c` and `int-hunter.c`.  Each file/program should include its own `main` function.  You are required to provide meaningful comments in all your functions and use proper coding style and indentation.  Your submission will be tested and graded by an autograder using `gcc` on a `linux` machine, for this reason it cannot be stressed enough that your program must follow the exact specifications for input and output upon submission, including the number of whitespaces.

For each of the questions you either pass the test cases (full points) or not (zero points).  To submit your solution to Gradescope, simply select the three required files and use the `drag and drop` option.

> :heavy_exclamation_mark: You must be reminded that students caught cheating or plagiarizing will receive `no credit`. Additional actions, including a failing grade in the class or referring the case for disciplinary action, may also be taken.
