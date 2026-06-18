# 目錄

- [[#1. 課程總覽比較表|1. 課程總覽比較表]]
    
- [[#2. 課程定位|2. 課程定位]]
    
    - [[#21 課程特色|2.1 課程特色]]
        
    - [[#22 適合對象|2.2 適合對象]]
        
- [[#3. 上課重點|3. 上課重點]]
    
- [[#4. 課程主要綱要|4. 課程主要綱要]]
    
- [[#5. Important Keywords|5. Important Keywords]]
    
- [[#6. 技術能力地圖|6. 技術能力地圖]]
    
- [[#7. 可做的專題|7. 可做的專題]]
    
- [[#8. 對 AI Engineer 的價值|8. 對 AI Engineer 的價值]]
    
- [[#9. 對 Cybersecurity 的價值|9. 對 Cybersecurity 的價值]]
    
- [[#10. 對 Embedded Systems 的價值|10. 對 Embedded Systems 的價值]]
    
- [[#11. 對研究與論文的價值|11. 對研究與論文的價值]]
    
- [[#12. 學習順序建議|12. 學習順序建議]]
    
- [[#13. 履歷與學習歷程價值|13. 履歷與學習歷程價值]]
    
- [[#14. 一句話總結|14. 一句話總結]]
    
- [[#15. 最終評價|15. 最終評價]]
    

# Embedded Systems Programming on ARM Cortex-M3/M4 Processor

# 1. 課程總覽比較表

|項目|內容|
|---|---|
|課程名稱|Embedded Systems Programming on ARM Cortex-M3/M4 Processor|
|領域|Embedded Systems、ARM Architecture、Firmware Engineering|
|難度|★★★★☆|
|核心定位|ARM Cortex-M Processor 底層架構與系統程式設計|
|適合對象|Embedded Engineer、Firmware Engineer、RTOS Developer|
|先備知識|C語言、基本 MCU 概念|
|實務價值|★★★★★|
|作品集價值|★★★★★|
|推薦程度|★★★★★|

本課程是 ARM Cortex-M3/M4 處理器架構的核心課程，重點不在 Peripheral，而是在 Processor 本身。課程深入解析 Memory Map、Bus Interface、NVIC、Exception、Interrupt、Context Switch、Startup File、Linker Script、Fault Handling 等重要主題。學完後可以真正理解 FreeRTOS、DMA、Bootloader、TrustZone 等技術背後的運作原理。

# 2. 課程定位

## 2.1 課程特色

- 深入 ARM Cortex-M3/M4 架構
    
- 大量動畫說明 Exception 與 Interrupt
    
- 使用 Inline Assembly
    
- 使用 GCC Toolchain
    
- 自行撰寫 Startup File
    
- 自行撰寫 Linker Script
    
- 實作 Context Switching
    
- 實作 Task Scheduler
    
- 分析 Fault Exception
    
- Bare-Metal Build Process
    

## 2.2 適合對象

- Embedded Systems 學生
    
- Firmware Engineer
    
- RTOS 開發者
    
- STM32 開發者
    
- Bootloader 開發者
    
- Embedded Security 工程師
    
- 想深入 ARM Cortex-M 架構的人
    

# 3. 上課重點

- ARM Cortex-M3 Architecture
    
- ARM Cortex-M4 Architecture
    
- Core Registers
    
- Processor Modes
    
- Privileged Mode
    
- Unprivileged Mode
    
- EPSR
    
- T Bit
    
- Memory Map
    
- Bus Interfaces
    
- Bit Banding
    
- Stack Operations
    
- MSP
    
- PSP
    
- AAPCS
    
- Function Call Convention
    
- Inline Assembly
    
- Naked Functions
    
- Exception Model
    
- NVIC
    
- Interrupt Priority
    
- Preemption
    
- HardFault
    
- BusFault
    
- UsageFault
    
- Fault Analysis
    
- SVC Exception
    
- PendSV
    
- SysTick
    
- Context Switching
    
- Task Scheduler
    
- Startup File
    
- Linker Script
    
- ELF Analysis
    
- OpenOCD
    
- GDB Debugging
    

# 4. 課程主要綱要

## ARM Cortex-M Processor Fundamentals

- Processor vs MCU
    
- Cortex-M Family
    
- Core Registers
    
- Processor Modes
    
- Access Levels
    

## Memory System

- Memory Map
    
- Bus Interface
    
- Bit Banding
    
- Bus Protocol
    

## Stack and AAPCS

- Stack Model
    
- MSP
    
- PSP
    
- Function Call
    
- AAPCS Standard
    

## Interrupt and Exception

- Exception Model
    
- NVIC
    
- Priority
    
- Preemption
    
- Interrupt Handling
    

## Fault Handling

- HardFault
    
- UsageFault
    
- BusFault
    
- Fault Analysis
    
- Stack Frame Analysis
    

## System Exceptions

- SVC
    
- PendSV
    
- SysTick
    

## Task Scheduling

- Context Switching
    
- Task Scheduler
    
- Multi-tasking
    
- Tick Management
    

## Bare-Metal Embedded Build Process

- GCC Toolchain
    
- Cross Compilation
    
- Makefile
    
- Object Files
    
- ELF Analysis
    

## Startup File

- Vector Table
    
- Reset Handler
    
- Startup Code
    

## Linker Script

- Memory Sections
    
- Location Counter
    
- Symbols
    
- Linking
    

## Debugging

- OpenOCD
    
- GDB
    
- Semihosting
    

# 5. Important Keywords

```text
ARM Cortex-M3, ARM Cortex-M4, Processor Architecture,
Core Registers, EPSR, T Bit, Memory Map,
Bus Interface, Bit Banding, Stack,
MSP, PSP, AAPCS, Function Call,
Inline Assembly, Naked Function,
Exception Model, NVIC,
Interrupt Priority, Preemption,
HardFault, BusFault, UsageFault,
Fault Handler, Stack Frame,
SVC, PendSV, SysTick,
Task Scheduler, Context Switching,
Startup File, Vector Table,
Reset Handler, Linker Script,
ELF, GCC Toolchain,
Cross Compilation, Makefile,
OpenOCD, GDB, Semihosting,
Bare-Metal Programming
```

# 6. 技術能力地圖

## 基礎能力

- ARM Cortex-M 架構
    
- Memory Map
    
- Stack
    
- Bus System
    

## 中階能力

- Interrupt Handling
    
- NVIC Programming
    
- Fault Analysis
    
- Assembly Programming
    

## 高階能力

- Context Switching
    
- Task Scheduling
    
- Startup File Development
    
- Linker Script Development
    

## 專業能力

- RTOS 核心理解
    
- Bootloader 理解
    
- Embedded Debugging
    
- Firmware Architecture
    

# 7. 可做的專題

## 專題1：Mini RTOS Scheduler

實作：

- SysTick
    
- PendSV
    
- Context Switch
    

## 專題2：Custom Startup File

實作：

- Vector Table
    
- Reset Handler
    
- Boot Sequence
    

## 專題3：Fault Analysis Framework

實作：

- HardFault Handler
    
- Stack Dump
    
- Fault Decoder
    

## 專題4：ARM Context Switch Demo

實作：

- Multiple Tasks
    
- Register Save/Restore
    

## 專題5：Bare-Metal Build System

實作：

- GCC Toolchain
    
- Linker Script
    
- Startup File
    

# 8. 對 AI Engineer 的價值

雖然不是 AI 課程，但對：

- Edge AI
    
- TinyML
    
- Embedded AI
    

很重要。

可理解：

- MCU 如何執行 AI Inference
    
- RTOS 如何調度 AI 任務
    
- Memory 如何影響 AI 模型部署
    

# 9. 對 Cybersecurity 的價值

非常高。

可理解：

- Secure Boot 基礎
    
- Fault Injection 原理
    
- Memory Corruption
    
- Stack Overflow
    
- Return Address
    
- Exception Handling
    

是學習：

- Firmware Security
    
- Embedded Security
    
- TrustZone
    

的重要前置課程。

# 10. 對 Embedded Systems 的價值

★★★★★

這門課幾乎是：

```text
Firmware Engineer 必修課
```

因為：

- RTOS 建立在它之上
    
- DMA 建立在它之上
    
- Bootloader 建立在它之上
    
- TrustZone 建立在它之上
    

# 11. 對研究與論文的價值

可延伸方向：

- RTOS Design
    
- Context Switching Optimization
    
- Embedded Security
    
- TrustZone
    
- Secure Boot
    
- Fault Injection Detection
    
- TinyML Runtime
    

# 12. 學習順序建議

```text
Embedded C
        ↓
ARM Cortex-M3/M4 Processor
        ↓
MCU Driver Development
        ↓
MCU2
        ↓
DMA
        ↓
RTOS
        ↓
Bootloader
        ↓
TrustZone
```

# 13. 履歷與學習歷程價值

|項目|評價|
|---|---|
|高中學習歷程|★★★★★|
|大學申請|★★★★★|
|國外申請|★★★★★|
|Embedded 實習|★★★★★|
|Firmware 實習|★★★★★|

這門課代表你不只是會用 STM32，而是理解 ARM Cortex-M Processor 的底層運作。

# 14. 一句話總結

```text
這門課本質上是在學 ARM Cortex-M Processor 的作業系統核心與底層運作原理。
```

# 15. 最終評價

### 難度

★★★★☆

### 實用性

★★★★★

### 含金量

★★★★★

### 作品集價值

★★★★★

### Embedded 相關性

★★★★★

### 未來發展性

★★★★★

這是 FastBit 系列中最核心、最底層、最值得學的一門課。它不是教你怎麼用 STM32 外設，而是教你 Cortex-M 處理器如何運作。學完後，你會真正理解 RTOS、DMA、Bootloader、TrustZone、Interrupt、Context Switching、Startup File、Linker Script 的底層原理。若未來目標是 Firmware Engineer、Embedded Engineer、Embedded Security Engineer，這門課的重要性甚至高於 DMA 課程。