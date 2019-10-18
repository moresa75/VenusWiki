This page is a work in progress.

I have been working on adding a vlib which will hold most of the functionality of some standard clib functions except that they will be optimized (written in kotlin instead of risc-v while still only using the memory) so that the ops can operate faster. This also allows for me to separate ecall to actually act more of an environment call.  To use any of the following functions, you will put `0x3CC` in the `where` register (currently `a0` though will eventually be `a7`). Then you will put in `a6` the following to run each vlib function:

| ID (`a6`)  | Name             | Description                                                         |
| ---------- | ---------------  | ------------------------------------------------------------------- |
| 1          | malloc           | Allocates exactly `a1` bytes to the heap. Returns the pointer to that block in `a0` |
| 2          | calloc           | Takes in `a1` nitems and `a2` size of each item. Zeros out the allocated memory. Returns a pointer to that block in `a0` |
| 3          | realloc          | Takes in a pointer to the block to realloc in `a1` and the new size you want to reallocate to in `a2`. Returns a pointer in `a0` to the newly allocated data. Note if you request a size smaller than the pointer, it will create a new block and copy only `size` bytes to the new location. |
| 4          | free             | frees the pointer given in `a1`. It will merge other free blocks around it if any exist. Does not return anything. |
| 5          | num_alloc_blocks | returns to `a0` the number of not free blocks or -1 if an error occurred. Errors may involve a modification of the backend structure so a link was not able to be read properly.|