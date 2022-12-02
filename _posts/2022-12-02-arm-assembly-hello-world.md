---
layout: post
title: ARM Assembly - Hello World!
date: '2022-12-02 08:49:07 +0800'
categories: [Code, ArmAssembly]
tags: [code, arm, assembly, armassembly]     # TAG names should always be lowercase
author: dev1
math: true
---


# Installation
I'm using WSL to build and run the ARM assembly code, these are the installation packages I used:

```bash
sudo apt install gcc-arm-linux-gnueabi make git-core ncurses-dev qemu qemu-user
```
{:file="Installation on Windows WSL"}

# Code

## Simple program to return a number to shell
```armasm
.global _start
.section .text

_start:
    mov r7, #0x1    @ System call number for exit (0x1)
    mov r0, #32     @ Exit code 32 (Returns 32 to the shell)
    swi 0           @ Software interrupt

.section .data
```
{:file="test.s"}

This returns

```bash
echo $?
32
```
{:file="Shell output"}

The `echo $?` command returns the exit code of the last command.

The ARM systemcall table is available [here](https://chromium.googlesource.com/chromiumos/docs/+/master/constants/syscalls.md#arm-32_bit_EABI). I've used the `exit` system call, which is `0x1`.

## Hello World

```armasm
.global _start
.section .text

_start:
    mov r7, #0x4        @ System call number for write (0x4)
    mov r0, #0x1        @ File descriptor (stdout)

    ldr r1, =message    @ Load address of message into r1
    ldr r2, =len        @ Load length of message into r2
    swi 0               @ Software interrupt

    mov r7, #0x1        @ System call number for exit (0x1)
    swi 0               @ Software interrupt

.section .data
message:                
    .ascii "Welcome to DevBlog!\n" 

len = . - message       @ Length of message

```
{:file="armasm.s"}

This returns

```bash
$ qemu-arm ./armasm.elf
Welcome to DevBlog!
```
{:file="Shell output"}

The `swi` instruction is a software interrupt instruction that allows the program to call the kernel, where it will use register `r7` to determine which system call to use and registers `r0` to `r4` to pass parameters to the system call.

Using the system call table, loading `0x4` into `r7` calls the `write` system call. 

The `write` system call takes 3 arguments:
- `r0` is the [file descriptor](#file-descriptors) for STDOUT (1)
- `r1` is the address of the message
- `r2` is the length of the message. 

Loading the address of the message into `r1` and the length of the message into `r2` is done using the `ldr` instruction and `r0` is loaded with the [file descriptor](#file-descriptors) 1 for `STDOUT`. This directly outputs the message to STDOUT.

## File Descriptors
These are the file descriptors for the standard input, output and error:

| File Descriptor | Description |
|-----------------|-------------|
| 0               | STDIN       |
| 1               | STDOUT      |
| 2               | STDERR      |


# Compilation
To compile the code(s), I'm using the following command:

```bash
arm-linux-gnueabi-as armasm.s -o armasm.o
arm-linux-gnueabi-gcc-9 armasm.o -o armasm.elf -nostdlib
```
{:file="Compilation"}

The `arm-linux-gnueabi-as` command compiles the assembly code into an object file, which is then linked with the `arm-linux-gnueabi-gcc-9` command to create an executable file. 

The `-nostdlib` flag is used to prevent the compiler from linking the [standard libraries](https://en.wikipedia.org/wiki/C_standard_library), which is not needed for this program.

## Makefile
Alternatively, you can use a `Makefile` to compile the code(s):

```makefile
CFLAGS  = -nostdlib
NAME = armasm

$(NAME): $(NAME).o
	arm-linux-gnueabi-gcc-9 $(NAME).o -o $(NAME).elf $(CFLAGS)

$(NAME).o: $(NAME).s
	arm-linux-gnueabi-as $(NAME).s -o $(NAME).o

clean:
	rm -f *.o
```

This allows you to compile the code(s) using the command `make` and clean the object files using the command `make clean`.

# Running
To run the code, I'm using the following command:

```bash
qemu-arm ./armasm.elf
```

Using the qemu emulator, you can run the code on your computer without having to use a Raspberry Pi or other ARM device.


# References
- [ARM System Call Table](https://chromium.googlesource.com/chromiumos/docs/+/master/constants/syscalls.md#arm-32_bit_EABI)
- This Wonderful [Tutorial](https://www.youtube.com/watch?v=FV6P5eRmMh8)
