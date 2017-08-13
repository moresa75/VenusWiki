To use an environmental call, load the ID into register `a0`, and load any arguments into `a1` - `a7`. Any return values will be stored in argument registers.

The following environmental calls are currently supported.

| ID (`a0`)  | Name            | Description                                                         |
| ---------- | --------------- | ------------------------------------------------------------------- |
| 1          | print_int       | prints integer in `a1`                                              |
| 4          | print_string    | prints the null-terminated string whose address is in `a1`          |
| 9          | sbrk            | allocates `a1` bytes on the heap, returns pointer to start in `a0`  |
| 10         | exit            | ends the program                                                    |
| 11         | print_character | prints ASCII character in `a1`                                      |
| 17         | exit2           | ends the program with return code in `a1`                           |

The environmental calls are intended to be somewhat backwards compatible with [SPIM's syscalls](https://www.doc.ic.ac.uk/lab/secondyear/spim/node8.html).

As an example, the following code prints the integer `42` to the console:

    addi a0 x0 1        # print_int ecall
    addi a1 x0 42       # integer 42
    ecall

