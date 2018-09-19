The following assembler directives are supported:

| Directive | Effect |
| --------- | ------ |
| `.data`   | Store subsequent items in the [[static segment\|Memory Segments]] at the next available address. |
| `.text`   | Store subsequent instructions in the [[text segment\|Memory Segments]] at the next available address. |
| `.byte`   | Store listed values as 8-bit bytes. |
| `.asciiz` | Store subsequent string in the data segment and add null-terminator. |
| `.word`   | Store listed values as unaligned 32-bit words. |
| `.globl`  | Makes the given label global. |
| `.float`  | Reserved. |
| `.double` | Reserved. |
| `.align`  | Reserved. |