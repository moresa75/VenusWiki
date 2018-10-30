To use an environmental call, load the ID into register `a0`, and load any arguments into `a1` - `a7`. Any return values will be stored in argument registers.

The following environmental calls are currently supported.

| ID (`a0`)  | Name            | Description                                                         |
| ---------- | --------------- | ------------------------------------------------------------------- |
| 1          | print_int       | prints integer in `a1`                                              |
| 4          | print_string    | prints the null-terminated string whose address is in `a1`          |
| 9          | sbrk            | allocates `a1` bytes on the heap, returns pointer to start in `a0`  |
| 10         | exit            | ends the program                                                    |
| 11         | print_character | prints ASCII character in `a1`                                      |
| 13         | openFile        | Opens the file in the VFS where a pointer to the path is in `a1` and the permission bits are in `a2`. Returns to a0 an integer representing the file descriptor.|
| 14         | readFile        | Takes in: `a1` = FileDescriptor, `a2` = Where to store the data (an array), `a3` = the amount you want to read from the file. Returns `a0` = Number of items which were read and put to the given array. If it is less than `a3` it is either an error or EOF. You will have to use another ecall to determine what was the cause. |
| 15         | writeFile       | Takes in: `a1` = FileDescriptor, `a2` = Buffer to read data from, `a3` = amount of the buffer you want to read, `a4` = Size of each item. Returns `a0` = Number of items written. If it is less than `a3` it is either an error or EOF. You will have to use another ecall to determine what was the cause. |
| 16         | closeFile       | Closes a file WIP                                                   |
| 17         | exit2           | ends the program with return code in `a1`                           |
| 18         | fflush          |                            |
| 19         | feof            |                            |
| 20         | ferror          |                            |
| 34         | printHex        | prints hex in `a1`                                                  |

The environmental calls are intended to be somewhat backwards compatible with [SPIM's syscalls](https://www.doc.ic.ac.uk/lab/secondyear/spim/node8.html).

As an example, the following code prints the integer `42` to the console:

    addi a0 x0 1        # print_int ecall
    addi a1 x0 42       # integer 42
    ecall

