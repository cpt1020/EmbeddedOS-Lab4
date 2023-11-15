# Analysis and Implementation of Embedded Operating Systems Lab 4

嵌入式作業系統分析與實作 Analysis and Implementation of Embedded Operating Systems [CSIE7618] @ NCKU 2022 Spring

## Development Environment

- Development Board
    - STM32F407G-DISC1
- Real-Time Operating System (RTOS)
    - [FreeRTOS v10.2.1](https://github.com/FreeRTOS/FreeRTOS/tree/V10.2.1)
- IDE
    - STM32CubeIDE

## Report

https://hackmd.io/@cpt/embeddedOS_lab4

## Introduction

The `heap_2.c` in FreeRTOS uses a link list to record free memory block and uses best-fit to allocate memory. However, `heap_2.c` doesn't merge contiguous free memory block.

In this lab, students are required to modify the `prvInsertBlockIntoFreeList` macro in `FreeRTOS/portable/MemMang/heap_2.c` to make it perform merge if free memory block are contiguous.

Also, students have to write a `vPrintFreeList` function in `FreeRTOS/portable/MemMang/heap_2.c` that will iterate through the list and print out the information of each free memory block, such as start address, end address, and block size.

## Requirement

- Part 0
    - Create 6 tasks:
        - `red_LED_task`
        - `green_LED_task`
        - `task1`
        - `task2`
        - `task3`
        - `print_task`
    - `task1`, `task2`, and `task3` will delete themselves
    - `print_task` will call `vPrintFreeList` function to show free list information
- Part 1
    - Use UART to show free memory list
    - Create a task to call `vPrintFreeList`, that is, the `print_task` task
    - Implement your `vPrintFreeList` function in `FreeRTOS/portable/MemMang/heap_2.c`
- Part 2
    - Modify `prvInsertBlockIntoFreeList` macro in `heap_2.c` to implement memory merging