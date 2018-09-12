Memory is divided into four different segments: text, static, heap and stack. 

| Segment | Starting Address |
| ------- | ---------------- |
| text*   | `0x0000_0000`    |
| static  | `0x1000_0000`    |
| heap    | `0x1000_8000`    |
| stack** | `0x7fff_fff0`    |

\* You can adjust the text starting address in the settings tab in the Simulator. Most RISC-V systems have the text start at `0x0000_1000`

\*\* Unlike other memory segments, the stack grows towards smaller addresses.