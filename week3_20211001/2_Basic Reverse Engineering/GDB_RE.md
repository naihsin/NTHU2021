# GDB
- [GDB簡介](#GDB簡介)
- [gdb-gef](#gdb-gef)
- [gdb-peda](#gdb-peda)
- [gdb常用指令](#gdb常用指令)
- [示範解題](#示範解題)
- [學習資源](#學習資源)
## GDB簡介
- [GDB: The GNU Project Debugger](https://www.gnu.org/software/gdb/)
- GDB allows you to see what is going on `inside' another program while it executes -- or what another program was doing at the moment it crashed.
- GDB can do four main kinds of things (plus other things in support of these) to help you catch bugs in the act:
  - Start your program, specifying anything that might affect its behavior.
  - Breakpoint:Make your program stop on specified conditions.
  - Examine what has happened, when your program has stopped.
  - Binary Patch:Change things in your program, so you can experiment with correcting the effects of one bug and go on to learn about another.
- Many Ehancements
  - [PEDA - Python Exploit Development Assistance for GDB](https://github.com/longld/peda)
  - [GEF - GDB Enhanced Features](https://gef.readthedocs.io/en/master/)
  - [pwndbg](https://github.com/pwndbg/pwndbg)
  - [Pwngdb:GDB for pwn(angelboy)](https://github.com/scwuaptx/Pwngdb)
  - [Pwndbg + GEF + Peda — One for all, and all for one](https://infosecwriteups.com/pwndbg-gef-peda-one-for-all-and-all-for-one-714d71bf36b8)

## [gdb-peda]
- PEDA is a Python GDB script with many handy commands to help speed up exploit development process on Linux/Unix. 
- PEDA is also a framework for writing custom interactive Python GDB commands.
- [PEDA - Python Exploit Development Assistance for GDB](https://github.com/longld/peda)

### 安裝peda
```
git clone https://github.com/longld/peda.git ~/peda
echo "source ~/peda/peda.py" >> ~/.gdbinit
```
### Usage
    - List of available commands:
        gdb-peda$ peda help

    - Search for some commands:
        gdb-peda$ apropos <keyword>
        gdb-peda$ help <keyword>

    - Get usage manual of specific command:
        gdb-peda$ phelp <command>
        gdb-peda$ help <command>

    - Get/set config option:
        gdb-peda$ pshow option
        gdb-peda$ pset option <name> <value>

### Key Features:[資料來源:github網址](https://github.com/longld/peda)
- Enhance the display of gdb: colorize and display disassembly codes, registers, memory information during debugging.
- Add commands to support debugging and exploit development (for a full list of commands use peda help):
  - aslr -- Show/set ASLR setting of GDB
  - checksec -- Check for various security options of binary
  - dumpargs -- Display arguments passed to a function when stopped at a call instruction
  - dumprop -- Dump all ROP gadgets in specific memory range
  - elfheader -- Get headers information from debugged ELF file
  - elfsymbol -- Get non-debugging symbol information from an ELF file
  - lookup -- Search for all addresses/references to addresses which belong to a memory range
  - patch -- Patch memory start at an address with string/hexstring/int
  - pattern -- Generate, search, or write a cyclic pattern to memory
  - procinfo -- Display various info from /proc/pid/
  - pshow -- Show various PEDA options and other settings
  - pset -- Set various PEDA options and other settings
  - readelf -- Get headers information from an ELF file
  - ropgadget -- Get common ROP gadgets of binary or library
  - ropsearch -- Search for ROP gadgets in memory
  - searchmem|find -- Search for a pattern in memory; support regex search
  - shellcode -- Generate or download common shellcodes.
  - skeleton -- Generate python exploit code template
  - vmmap -- Get virtual mapping address ranges of section(s) in debugged process
  - xormem -- XOR a memory region with a key

## gdb-gef
- [GEF - GDB Enhanced Features](https://gef.readthedocs.io/en/master/)
- GEF is a set of commands for X86, ARM, MIPS, PowerPC and SPARC to make GDB cool again for exploit dev. 
- aimed to be used mostly by exploit developers and reverse-engineers, to provide additional features to GDB using the Python API to assist during the process of dynamic analysis and exploit development.
- full support for both Python2 and Python3 indifferently (as more and more distros start pushing gdb compiled with Python3 support).
- [官方說明文件](https://gef.readthedocs.io/en/master/)

### [Key Features](https://gef.readthedocs.io/en/master/)
- One single GDB script
- Entirely OS Agnostic, NO dependencies: GEF is battery-included and is installable instantly
- Fast limiting the number of dependencies and optimizing code to make the commands as fast as possible
- Provides a great variety of commands to drastically change your experience in GDB.
- Easily extensible to create other commands by providing more comprehensible layout to GDB Python API.
- Full Python3 support (Python2 support was dropped - see gef-legacy).
- Built around an architecture abstraction layer, so all commands work in any GDB-supported architecture such as x86-32/64, ARMv5/6/7,AARCH64, SPARC, MIPS, PowerPC, etc.
-Suited for real-life apps debugging, exploit development, just as much as CTF

## [安裝](https://gef.readthedocs.io/en/master/config/)
```
$ git clone https://github.com/hugsy/gef.git  # or git pull to update
$ echo 'source /path/to/gef.py' >> ~/.gdbinit
```

### ![#1589F0](https://via.placeholder.com/15/1589F0/000000?text=+)`常用指令`

```gdb
$ gdb-gef ./a.out ==> 需要設定
gef➤ gef help
gef➤ run  ==> 會開啟漂亮視窗
```
- [gef➤ checksec](https://gef.readthedocs.io/en/master/commands/checksec/)
- [gef➤ canary](https://gef.readthedocs.io/en/master/commands/canary/)
- [gef➤ aslr](https://gef.readthedocs.io/en/master/commands/aslr/)
- [gef➤ elf](https://gef.readthedocs.io/en/master/commands/elf-info/)
- [gef➤ vmmap -- Display a comprehensive layout of the virtual memory mapping.](https://gef.readthedocs.io/en/master/commands/vmmap/)
- [gef➤ registers ==>print all the registers and dereference any pointers](https://gef.readthedocs.io/en/master/commands/registers/)
- [gef➤ memory watch XXX](https://gef.readthedocs.io/en/master/commands/memory/)
- [gef➤ heap <sub_commands>](https://gef.readthedocs.io/en/master/commands/heap/)
- [gef➤ got](https://gef.readthedocs.io/en/master/commands/got/)
- [gef➤ dereference](https://gef.readthedocs.io/en/master/commands/dereference/)
- [gef➤ cs main [capstone-disassemble]](https://gef.readthedocs.io/en/master/commands/capstone-disassemble/)


## gdb常用指令
- [官方龐大文件Debugging with GDB](https://sourceware.org/gdb/current/onlinedocs/gdb/)
- [GDB Cheat Sheet](https://darkdust.net/files/GDB%20Cheat%20Sheet.pdf)
- run ==> 執行(簡寫:r)
- q 離開
- disassemble <func>  反組譯 (簡寫:disas)
  - disassemble 敲敲兩下tab，會列出程式用到的所有func 

- 設置斷點 break (簡寫: b)
  - break * <0x809030>
  - break * <func_name>
    -* 用func_name可省略

- info查看各種資訊
  - info breakpoint ==>查看已設定斷點 (簡寫: i b)
  - info registers  ==> 顯示所有暫存器
  - info registers eax ==>  顯示eax暫存器 (簡寫: i r eax)

- 執行程式
  - ni  ==>下一個指令 {func直接執行完畢}   (簡寫: n)
  - si  ==>下一個指令 {逐步執行func中的指令} (簡寫: s)
  - continue ==> 執行到斷點(簡寫: c)

- set 設定與修改
  - set * address = value
  - set $register = value
```
將address中的值設成value
* 默認4bytes
可換成
{char} 1byte
{short} 2bytes
{long} 8bytes
```

- x/nfu <address> ==> Print memory.檢視記憶體的資料
  - n: How many units to print (default 1).
  - f: Format character (like „print“).
    - d Integer, signed decimal.
    - t Integer, print as binary (t = „two“).
    - o Integer, print as octal.
    - u Integer, unsigned decimal.
    - x Integer, print as hexadecimal.
    - f Floating point number.
    - c Read as integer, print as character.
    - s Try to treat as C string.
  - u: Unit.
    Unit is one of:
    - b: Byte/1 byte (8-bit)
    - h: Half-word (two bytes)
    - w: Word (four bytes)
    - g: Giant word (eight bytes))

- vmmap ==>查看⽬前程式的記憶體分佈，以及 rwx 權限設定
- p <register> 查看某暫存器
- j *<0x809030> 跳到某個位址 (jump)

## 示範解題

## 學習資源
