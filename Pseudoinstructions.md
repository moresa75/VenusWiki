venus currently supports the following [standard RISC-V pseudoinstructions](https://riscv.org/specifications/):

* `la rd, symbol`: load address
* `l{b|h|w} rd, symbol`: load global
* `nop`: no operation
* `li rd, immediate`: load immediate
* `mv rd, rs`: copy register
* `j label`: jump to label
* `jal label`: jump and link
* `jr rs`: jump register
* `jalr rs`: jump and link register
* `ret`: return from subroutine 
