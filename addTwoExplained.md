The bytecode output of the compiler will echo the following into the console 600f8060093d393df36000356020350160005260206000f3.

When you deploy this contract code it will have the runtime bytecode of the main macro we just created! 
In the above snippet you will find it after the first f3 (the preceding bytecode is boilerplate constructor logic.) 
That leaves us with this: 6000356020350160005260206000f3 Below, this example dissembles what you have just created!

BYTECODE          MNEMONIC         STACK                 ACTION
60 00          // PUSH1 0x00       // [0x00]
35             // CALLDATALOAD     // [number1]          Store the first 32 bytes on the stack
60 20          // PUSH1 0x20       // [0x20, number1]
35             // CALLDATALOAD     // [number2, number1] Store the second 32 bytes on the stack
01             // ADD              // [number2+number1]  Take two stack inputs and add the result
60 00          // PUSH1 0x00       // [0x0, (n2+n1)]
52             // MSTORE           // []                 Store (n2+n1) in the first 32 bytes of memory
60 20          // PUSH1 0x20       // [0x20]
60 00          // PUSH1 0x00       // [0x00, 0x20]
f3             // RETURN           // []                 Return the first 32 bytes of memory