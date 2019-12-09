# vscode-debug-repro
This is a minimal reproduction of a vscode same filename debugging bug

## Description of the bug
The bug occurs when debuggin C++ code with VSCode. When a source files name is not unique (there are more than 1 files with the same name) putting a breakpoint in that file will put the breakpoint in each file.

I have only tested this bug on OSX with lldb.

## How to reproduce the bug
1. Compile the program: clang++ main.cpp other_folder/main.cpp -Iother_folder -g
2. Open ./main.cpp in VSCode (not other_folder/main.cpp).
3. Put a breakpoint on line 7.
4. Start debugging the program.

The debugger will break in other_folder/main.cpp on line 7.
