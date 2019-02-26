The Simulator is the main component of venus.

# Simulator Controls

The following controls are available:

* __Run__ / __Stop__: runs the program until it terminates or a breakpoint is hit. While running, the program can be stopped by clicking it again.
* __Step__: executes the highlighted instruction.
* __Prev__: undo the previously executed instruction.
* __Reset__: resets the simulator to its initial state (equivalent to reassembling the program).

# Program View

The program view displays the assembled program. It contains three columns:

* __Machine Code__: the machine code of the instruction in hexadecimal.
* __Basic Code__: the assembly code after pseudoinstruction expansion and linking.
* __Original Code__: the original code in the program.

## Debugging

The instruction which is about to be executed is highlighted in green.

In order to add a breakpoint, simply click on the instruction. This will cause the row to be highlighted red, indicating that a breakpoint has been set. To remove the breakpoint, click it again.

Another option is if you always want to break at a certain point in the code, you can just put an `ebreak` where you want the debugger to stop at. The debugger will stop just before it executes the instruction after the `ebreak`.

# Sidebar View

## Registers

The register tab displays the values of the current registers. The most recently changed register is highlighted in blue. In addition, the registers values can be edited.

## Memory

The memory tab shows the bytes currently in memory.

### Memory Controls

The __Jump to__ select box allows jumping to a [[memory segment|Memory Segments]].

The __Up / Down__ buttons scroll the memory view. __Up__ moves towards higher addresses, and __down__ moves towards lower addresses.

The __Address__ box allows you to jump to a specific address of memory.

## Display Settings

The display settings can be used to change how values are displayed. By default, values are displayed in unsigned hexadecimal.

* __Hex__ (default) - display as unsigned hexadecimal.
* __Decimal__ - display as signed decimal.
* __Unsigned__ - display as unsigned decimal.
* __ASCII__ - display as ASCII character, surrounded by single quotes.
    * If the number is too big (not between 0 and 255), it is displayed as hex instead.
    * Anything which is in ASCII but not printable is displayed as the unicode replacement glyph: �

# Console Output

The console output is used for [[ecalls|Environmental Calls]] and displaying any errors which occur.

# Exit Code

The web version will now display an exit code when the program finishes. This may be due to the program calling an ecall or the PC counter going beyond the loaded text section. If your program goes beyond the program’s text, it will determine the exit code from the register `a0`. You can think of it as returning an int from main. The JV version will actually cause Venus to exit with that error code. Note that Venus jvm currently exits with a `-1` error code when an internal error occurs (aka. Assembly error).