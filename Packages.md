Venus now has a package management system! It allows for any user to make a package which piggybacks on the current Venus architecture. Am working on improving it to make it work properly. To build your own package, take a look here:
[Example Package](https://github.com/ThaumicMekanism/venus/blob/master/src/main/frontend/packages/examplepackage.js)
All you have to do is go to the Simulator -> Settings -> Packages and then add the link to your new package.

Packages must be written in javascript and can be a simple shell interface to hook into some backend as well if you wish.

Some packages I have made can be found here (note that I am working on porting them to be better as they were initially written before the packages system was created):

[RISC-V Disassembler](https://github.com/ThaumicMekanism/venus/blob/master/src/main/frontend/packages/disassembler.js)
[RISC-V Code Tester](https://github.com/ThaumicMekanism/venus/blob/master/src/main/frontend/packages/tester.js)