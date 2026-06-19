# Embedded Systems / STM32 / ARM 課程分析比較

> 目的：比較 10 門 Embedded Systems / STM32 / ARM 課程的定位、上課重點、主要綱要、重要 Keywords，以及建議學習順序。  
> 適合用途：HackMD、Obsidian、學習歷程整理、嵌入式系統自學規劃。

---

## 0. 總覽比較表

| 編號 | 課程 | 核心定位 | 難度 | 最適合學習目標 |
|---|---|---|---|---|
| 1 | [ARM Cortex M Microcontroller DMA Programming Demystified](https://www.udemy.com/course/microcontroller-dma-programming-fundamentals-to-advanced/?couponCode=25BBPMXINACTIVE) | DMA 專題課 | 中階 | 學會 ADC / UART / SRAM / Peripheral DMA 資料搬移 |
| 2 | [ARMv8-M TrustZone on Cortex-M33 with LPC55S69](https://www.udemy.com/course/armv8-m-trust-zone-on-cortex-m33-embedded-security/?couponCode=PMNVD2025) | Embedded Security / TrustZone | 中高階 | 學 MCU 安全隔離、Secure / Non-Secure 韌體架構 |
| 3 | [Embedded Systems Programming on ARM Cortex-M3/M4 Processor](https://www.udemy.com/course/embedded-system-programming-on-arm-cortex-m3m4/?couponCode=25BBPMXINACTIVE) | ARM Cortex-M 架構底層 | 中階 | 理解 NVIC、Exception、Startup、Linker Script、Context Switch |
| 4 | [Embedded Systems Bare-Metal Programming Ground Up™ (STM32)](https://www.udemy.com/course/embedded-systems-bare-metal-programming/?couponCode=25BBPMXINACTIVE) | STM32 Bare-Metal 從零寫 Driver | 初中階 → 中階 | 不靠 HAL，直接用 Register 寫 GPIO / UART / SPI / I2C / ADC / DMA |
| 5 | [Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging](https://www.udemy.com/course/mastering-rtos-hands-on-with-freertos-arduino-and-stm32fx/?couponCode=25BBPMXINACTIVE) | FreeRTOS 實作與 Debug | 中階 | 學 Task、Queue、Semaphore、Mutex、Scheduler、SystemView Debug |
| 6 | [Mastering Microcontroller and Embedded Driver Development](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/?couponCode=25BBPMXINACTIVE) | MCU1：Peripheral Driver Development | 中階 | 系統化寫 GPIO / SPI / I2C / USART Driver |
| 7 | [Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2)](https://www.udemy.com/course/microcontroller-programming-stm32-timers-pwm-can-bus-protocol/?couponCode=25BBPMXINACTIVE) | MCU2：進階 Peripheral | 中階 | 學 Timer、PWM、CAN、RTC、Low Power、Clock |
| 8 | [STM32Fx Microcontroller Custom Bootloader Development](https://www.udemy.com/course/stm32f4-arm-cortex-mx-custom-bootloader-development/?couponCode=PMNVD2025) | Bootloader / IAP | 中高階 | 學自製 Bootloader、Flash Programming、Host Communication |
| 9 | [Mastering STM32CubeMX 5 and CubeIDE - Embedded Systems](https://www.udemy.com/course/stm32cubemx-5-and-cubeide/?couponCode=PMNVD2025) | CubeMX / CubeIDE 實務整合 | 初中階 | 快速用 CubeMX + CubeIDE 做 USB、ADC、SPI、UART、DMA、FreeRTOS |
| 10 | [AI-Assisted Embedded Firmware Development](https://www.udemy.com/course/ai-assisted-embedded-firmware-development/?couponCode=25BBPMXINACTIVE) | AI 輔助 Firmware Workflow | 中階 | 學如何安全使用 AI 寫 Driver、Debug、Refactor、Test |

---

## 1. 課程個別分析

---

### 1. ARM Cortex M Microcontroller DMA Programming Demystified

**課程連結：**  
[ARM Cortex M Microcontroller DMA Programming Demystified](https://www.udemy.com/course/microcontroller-dma-programming-fundamentals-to-advanced/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門課專門講 **DMA（Direct Memory Access）**。它不是一般 STM32 入門課，而是針對 MCU 中「資料搬移效率」的進階主題。

DMA 的核心價值是：  
讓資料可以在 **Memory ↔ Peripheral** 之間搬移，而不需要 CPU 一筆一筆處理。

#### 上課重點

- DMA 基本原理
- ARM Cortex-M Bus Matrix
- AHB Bus / APB Bus
- DMA Controller 內部架構
- DMA Stream / Channel / Priority
- Memory-to-Memory Transfer
- Peripheral-to-Memory Transfer
- Memory-to-Peripheral Transfer
- UART + DMA
- ADC + DMA
- GPIO + DMA
- DMA Interrupt
- Circular Mode
- FIFO / Burst / Alignment
- Debug DMA 問題

#### 主要綱要

1. DMA Introduction
2. MCU Bus Matrix
3. DMA Controller Internal Architecture
4. DMA Channel and Stream Mapping
5. DMA Configuration Flow
6. GPIO DMA Exercise
7. UART to SRAM DMA
8. ADC to SRAM DMA
9. DMA Interrupt Handling
10. DMA Debugging

#### Important Keywords

```text
DMA, Direct Memory Access, ARM Cortex-M, STM32, AHB Bus, APB Bus, Bus Matrix,
DMA Stream, DMA Channel, FIFO, Burst Transfer, Circular Mode, Memory-to-Memory,
Peripheral-to-Memory, Memory-to-Peripheral, ADC DMA, UART DMA, Interrupt,
Priority, Alignment, Embedded C, STM32CubeMX
```

#### 適合做的專案

- 高速 ADC 資料擷取
- UART 大量資料接收
- Sensor Data Logger
- 音訊或訊號資料 Buffer
- STM32 + DMA + FreeRTOS 專題
- 機器人感測器資料流最佳化

#### 評價

這門課很適合已經會 GPIO / UART / ADC 的學生。  
如果還沒學 Peripheral Driver，建議先學 MCU1 或 Bare-Metal 再來學 DMA。

---

### 2. ARMv8-M TrustZone on Cortex-M33 with LPC55S69

**課程連結：**  
[ARMv8-M TrustZone on Cortex-M33 with LPC55S69](https://www.udemy.com/course/armv8-m-trust-zone-on-cortex-m33-embedded-security/?couponCode=PMNVD2025)

#### 課程定位

這門課是 **嵌入式安全（Embedded Security）** 的專題課，重點是 ARMv8-M TrustZone。  
它不像 STM32F4 常見課程，而是偏向 Cortex-M33 / Secure Firmware Architecture。

#### 上課重點

- ARMv8-M Architecture
- Cortex-M33 Processor Architecture
- TrustZone Security Model
- Secure State / Non-Secure State
- Secure Gateway
- SAU（Security Attribution Unit）
- IDAU（Implementation Defined Attribution Unit）
- Memory Attribution
- Secure / Non-Secure Interrupt
- TrustZone State Transition
- CMSIS Security API
- LPC55S69 實作

#### 主要綱要

1. Cortex-M33 Architecture
2. TrustZone Concept
3. Secure and Non-Secure Execution Context
4. Memory Security Attribution
5. SAU and IDAU
6. Secure Gateway Instruction
7. BLXNS / BXNS / SG Instructions
8. Secure Interrupt Handling
9. CMSIS TrustZone Programming
10. LPC55S69 Firmware Implementation

#### Important Keywords

```text
ARMv8-M, Cortex-M33, TrustZone, Embedded Security, Secure State, Non-Secure State,
SAU, IDAU, Secure Gateway, SG Instruction, BLXNS, BXNS, CMSIS, Secure Firmware,
Memory Attribution, Secure Boot, Interrupt Security, LPC55S69, MPU, Firmware Isolation
```

#### 適合做的專案

- Secure Boot Prototype
- Secure Firmware Partition
- Crypto Key Protection Demo
- Secure / Non-Secure API Demo
- IoT Device Security Demo
- MCU Trusted Execution Environment

#### 評價

這門課非常適合想走 **資安 + 嵌入式系統** 的學生。  
如果未來想做 IoT Security、Firmware Security、Automotive Security，這門課很有價值。

---

### 3. Embedded Systems Programming on ARM Cortex-M3/M4 Processor

**課程連結：**  
[Embedded Systems Programming on ARM Cortex-M3/M4 Processor](https://www.udemy.com/course/embedded-system-programming-on-arm-cortex-m3m4/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門課是理解 ARM Cortex-M 底層架構的核心課。  
它不是單純寫 STM32 外設，而是教你 MCU 的處理器內部如何運作。

#### 上課重點

- ARM Cortex-M3 / M4 Architecture
- Memory Map
- Processor Modes
- Privileged / Unprivileged Mode
- Stack
- AAPCS Calling Convention
- Inline Assembly
- Startup File
- Linker Script
- Exception Handling
- NVIC
- SysTick
- PendSV
- Context Switching
- Fault Handler
- Bare-Metal Build Process

#### 主要綱要

1. Cortex-M Processor Architecture
2. Core Registers
3. Memory Map
4. Operation Modes
5. Stack and AAPCS
6. Inline Assembly
7. Startup Code
8. Linker Script
9. Exception and Interrupt
10. NVIC
11. SysTick and PendSV
12. Context Switching
13. Fault Debugging

#### Important Keywords

```text
ARM Cortex-M3, ARM Cortex-M4, NVIC, Exception, Interrupt, SysTick, PendSV,
Context Switching, Startup Code, Linker Script, Stack, AAPCS, Inline Assembly,
Fault Handler, HardFault, BusFault, Memory Map, Privileged Mode, Unprivileged Mode,
Bare-Metal Build Process
```

#### 適合做的專案

- Mini Task Scheduler
- Context Switch Demo
- Custom Startup File
- Linker Script Demo
- Fault Analysis Lab
- Bare-Metal Kernel Prototype

#### 評價

這門課是「真正理解 ARM MCU」的關鍵。  
如果目標是從 STM32 使用者變成 Firmware Engineer，這門課很重要。

---

### 4. Embedded Systems Bare-Metal Programming Ground Up™ (STM32)

**課程連結：**  
[Embedded Systems Bare-Metal Programming Ground Up™ (STM32)](https://www.udemy.com/course/embedded-systems-bare-metal-programming/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門課主打 **不用第三方 Library、不靠 HAL，直接從 Datasheet / Reference Manual 寫 Register Driver**。

它非常適合建立真正的 STM32 Bare-Metal 能力。

#### 上課重點

- STM32 Memory-Mapped Register
- Peripheral Base Address
- Register Definition
- GPIO Driver
- UART Driver
- ADC Driver
- Timer Driver
- PWM Driver
- SPI Driver
- I2C Driver
- DMA Driver
- Interrupt Driver
- CMSIS Standard
- Debugger 使用
- Datasheet / Reference Manual 閱讀

#### 主要綱要

1. 建立 Bare-Metal 開發環境
2. 從文件找 Peripheral Address
3. 建立 Register 結構
4. GPIO Driver
5. Interrupt Driver
6. UART Driver
7. Timer / PWM Driver
8. ADC Driver
9. SPI Driver
10. I2C Driver
11. DMA Driver
12. Debugging

#### Important Keywords

```text
Bare-Metal, STM32, Embedded C, Register-Level Programming, Memory-Mapped IO,
CMSIS, GPIO, UART, SPI, I2C, ADC, Timer, PWM, DMA, Interrupt, Datasheet,
Reference Manual, Peripheral Base Address, Bit Manipulation, Debugging
```

#### 適合做的專案

- STM32 Register-Level Driver Library
- Bare-Metal Sensor Driver
- ADC + DMA Data Acquisition
- UART Command Interface
- SPI Display Driver
- I2C Sensor Integration

#### 評價

這門課非常適合打底。  
它的價值在於訓練你讀 Datasheet 和 Reference Manual，而不是只會按 CubeMX。

---

### 5. Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging

**課程連結：**  
[Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging](https://www.udemy.com/course/mastering-rtos-hands-on-with-freertos-arduino-and-stm32fx/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門課專門學 **FreeRTOS + STM32**。  
重點不是只會建立 Task，而是理解 Scheduler、Context Switching、Priority、Debug Trace。

#### 上課重點

- RTOS vs GPOS
- Real-Time Application
- Task Creation / Deletion
- Task Priority
- Scheduler
- Context Switching
- SysTick
- PendSV
- SVC Handler
- Queue
- Semaphore
- Mutex
- Priority Inversion
- Stack / Heap
- Task Synchronization
- ISR to Task Synchronization
- SEGGER SystemView Debug
- FreeRTOS Porting

#### 主要綱要

1. RTOS Introduction
2. FreeRTOS Project Setup
3. Task Creation
4. Scheduler
5. Context Switching
6. Stack and Heap
7. Queue
8. Semaphore
9. Mutex
10. Interrupt Synchronization
11. Priority Inversion
12. SEGGER SystemView
13. FreeRTOS Debugging
14. Low Power with RTOS

#### Important Keywords

```text
FreeRTOS, RTOS, Task, Scheduler, Context Switching, SysTick, PendSV, SVC,
Queue, Semaphore, Mutex, Priority Inversion, Stack, Heap, ISR, Synchronization,
SEGGER SystemView, Real-Time System, Tick Timer, ARM Cortex-M, STM32
```

#### 適合做的專案

- Multi-Task Sensor System
- FreeRTOS Robot Controller
- RTOS-Based UART Command Processor
- RTOS Data Logger
- RTOS + DMA + ADC System
- Real-Time Motor Control Prototype

#### 評價

這門課很適合學完 GPIO / UART / Timer 後進階。  
如果要做機器人、無人機、控制系統、IoT Gateway，FreeRTOS 是必學。

---

### 6. Mastering Microcontroller and Embedded Driver Development

**課程連結：**  
[Mastering Microcontroller and Embedded Driver Development](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門是 FastBit 的 MCU1 課程，是 **Peripheral Driver Development 主線課程**。  
它比單純 HAL 課更底層，重點是系統化開發 GPIO / SPI / I2C / USART Driver。

#### 上課重點

- MCU Datasheet / Reference Manual
- Peripheral Register
- Peripheral Clock
- AHB / APB Bus
- GPIO Driver
- SPI Driver
- I2C Driver
- USART Driver
- Interrupt Handling
- NVIC
- Driver Header Design
- API Design
- Logic Analyzer
- Serial Protocol Debugging
- Clock Tree

#### 主要綱要

1. STM32CubeIDE Setup
2. Embedded Debugging
3. MCU Memory Map
4. RCC and Clock
5. GPIO Driver
6. SPI Driver
7. I2C Driver
8. USART Driver
9. Interrupt and NVIC
10. Driver API Design
11. Logic Analyzer Debugging

#### Important Keywords

```text
MCU Driver Development, GPIO, SPI, I2C, USART, Peripheral Driver, RCC,
Clock Tree, AHB, APB, NVIC, Interrupt, Register, Datasheet, Reference Manual,
Driver API, Embedded C, Logic Analyzer, Serial Protocol, STM32CubeIDE
```

#### 適合做的專案

- 自製 STM32 Driver Library
- SPI Sensor Driver
- I2C OLED / Sensor Driver
- USART Shell
- Logic Analyzer Protocol Debug
- Multi-Peripheral Firmware Project

#### 評價

這門課是整組課程中最值得先學的主線之一。  
它會讓你理解「Driver 是怎麼寫出來的」。

---

### 7. Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2)

**課程連結：**  
[Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2)](https://www.udemy.com/course/microcontroller-programming-stm32-timers-pwm-can-bus-protocol/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門是 MCU1 後面的進階課，主題是 **Timer / PWM / CAN / Low Power / RTC / Clock**。

它很適合做馬達控制、車用通訊、低功耗裝置。

#### 上課重點

- STM32 Timers
- Basic Timer
- General Purpose Timer
- Input Capture
- Output Compare
- PWM
- Timer Interrupt
- CAN Protocol
- CAN Signaling
- CAN Filtering
- CAN Interrupt
- STM32 HAL Driver
- Low Power Mode
- Sleep Mode
- Stop Mode
- Standby Mode
- RTC Calendar / Alarm / Wakeup
- HSE / HSI / LSE / LSI / PLL

#### 主要綱要

1. Timer Introduction
2. Input Capture
3. Output Compare
4. PWM
5. Timer Interrupt
6. CAN Protocol
7. CAN Peripheral Programming
8. CAN Filtering
9. Low Power Modes
10. RTC
11. Clock Tree
12. PLL Programming

#### Important Keywords

```text
STM32 Timer, PWM, Input Capture, Output Compare, Timer Interrupt, CAN Bus,
CAN Protocol, CAN Filtering, CAN Transceiver, RTC, Low Power, Sleep Mode,
Stop Mode, Standby Mode, Wakeup Pin, EXTI, HSE, HSI, LSE, LSI, PLL, Clock Tree
```

#### 適合做的專案

- PWM Motor Control
- Servo Control
- Ultrasonic Sensor Input Capture
- CAN Bus Node
- Low-Power Sensor Device
- RTC Alarm Wakeup System
- 車用 CAN 通訊 Demo

#### 評價

這門很實用。  
如果赫霆未來要做機器人、無人機、車用控制、STM32 專題，Timer / PWM / CAN 都是核心能力。

---

### 8. STM32Fx Microcontroller Custom Bootloader Development

**課程連結：**  
[STM32Fx Microcontroller Custom Bootloader Development](https://www.udemy.com/course/stm32f4-arm-cortex-mx-custom-bootloader-development/?couponCode=PMNVD2025)

#### 課程定位

這門課是 **Bootloader / Firmware Update / IAP（In-Application Programming）** 專題。

Bootloader 是產品化 Firmware 非常重要的一環，尤其是需要 OTA、現場更新、USB / UART 更新韌體的裝置。

#### 上課重點

- Bootloader Concept
- STM32 Boot Modes
- Reset Sequence
- Memory Aliasing
- Flash Memory Layout
- Flash Sector Erase
- Flash Programming
- Mass Erase
- Option Bytes
- Host-Bootloader Communication
- Bootloader Command Packet
- In-Application Programming
- Vector Table Relocation
- Application Jump
- CRC / Firmware Validation

#### 主要綱要

1. Bootloader Introduction
2. STM32 Memory Organization
3. Reset Sequence
4. Boot Configuration
5. Host Communication
6. Bootloader Command Packet
7. Flash Erase / Program
8. Option Bytes
9. Flash Protection
10. Vector Table Relocation
11. Jump to Application
12. IAP Implementation

#### Important Keywords

```text
Bootloader, STM32 Boot Mode, Reset Sequence, Memory Aliasing, Flash Memory,
Flash Sector, Sector Erase, Flash Programming, Mass Erase, Option Bytes,
In-Application Programming, IAP, Vector Table Relocation, Host Communication,
Firmware Update, CRC, Application Jump, UART Bootloader
```

#### 適合做的專案

- UART Firmware Update Bootloader
- Secure Bootloader Prototype
- Firmware Version Manager
- Bootloader + Application 分區
- OTA Update 前置基礎
- Product-Grade Firmware Update System

#### 評價

這門課很有作品集價值。  
如果做出「STM32 自製 Bootloader + PC Host Tool + Firmware Update Demo」，對申請、履歷、實習都很加分。

---

### 9. Mastering STM32CubeMX 5 and CubeIDE - Embedded Systems

**課程連結：**  
[Mastering STM32CubeMX 5 and CubeIDE - Embedded Systems](https://www.udemy.com/course/stm32cubemx-5-and-cubeide/?couponCode=PMNVD2025)

#### 課程定位

這門課偏向 **CubeMX / CubeIDE 實務整合**，它不是最底層，但很適合快速做出功能。

它會碰到 GPIO、Timer、ADC、SPI、UART、DMA、USB、FreeRTOS。

#### 上課重點

- STM32CubeMX
- STM32CubeIDE
- Clock Configuration
- GPIO
- Timer
- PWM
- ADC
- SPI
- UART
- DMA
- USB HID Mouse
- USB HID Keyboard
- USB Virtual COM Port
- FreeRTOS
- Mutex
- Thread Notification
- ARM Assembly with CubeIDE

#### 主要綱要

1. CubeMX / CubeIDE Setup
2. Clock Configuration
3. GPIO Driver
4. Bare-Metal Embedded C
5. ARM Assembly
6. Timer Driver
7. ADC Driver
8. SPI Driver
9. UART Driver
10. USB HID / VCP
11. FreeRTOS Tasks
12. Mutex and Thread Notification

#### Important Keywords

```text
STM32CubeMX, STM32CubeIDE, HAL, LL Driver, GPIO, Timer, PWM, ADC, SPI, UART,
DMA, USB HID, USB Keyboard, USB Mouse, USB CDC, Virtual COM Port, FreeRTOS,
Mutex, Thread Notification, ARM Assembly, Clock Configuration
```

#### 適合做的專案

- USB HID Keyboard
- USB HID Mouse
- USB Virtual COM Port
- STM32 Sensor Dashboard
- FreeRTOS Peripheral Integration
- CubeMX Rapid Prototyping

#### 評價

這門課適合「快速做作品」。  
但如果只學這門，容易只會 CubeMX，不一定真正理解底層。因此建議搭配 Bare-Metal 或 MCU1。

---

### 10. AI-Assisted Embedded Firmware Development

**課程連結：**  
[AI-Assisted Embedded Firmware Development](https://www.udemy.com/course/ai-assisted-embedded-firmware-development/?couponCode=25BBPMXINACTIVE)

#### 課程定位

這門課很新，重點不是教 STM32 外設本身，而是教你如何用 AI 輔助 Firmware 開發，同時避免 AI 亂寫 Register、亂猜 Datasheet、造成 Silent Failure。

#### 上課重點

- AI as Peer Programmer
- AI Prompting for Firmware
- Embedded AI Workflow
- Prompting for Driver Development
- Prompting for Debugging
- Prompting for Refactoring
- Prompting for Test Cases
- Prompting for Documentation
- Datasheet Cross-Checking
- Warning Policy
- Hardware Evidence
- Code Review Checklist
- Failure Modes
- Hallucinated Registers
- Wrong Timing / Clock Assumptions
- ABI and Memory Layout Mistakes

#### 主要綱要

1. Mental Model for AI Assistance
2. Safe Baseline Workflow
3. Prompt Discipline
4. Explain Legacy Code
5. Interrupt / Concurrency Prompting
6. Generate Peripheral Drivers Safely
7. Refactor Firmware Safely
8. Test and Validation
9. Datasheet Verification
10. Common AI Failure Modes
11. AI-Assisted Workspace
12. Hardware Validation

#### Important Keywords

```text
AI-Assisted Firmware, LLM, Prompt Engineering, Embedded C, Code Review,
Driver Generation, Firmware Debugging, Refactoring, Test Case Generation,
Datasheet Validation, Hardware Evidence, Warning Policy, Hallucinated Register,
Clock Assumption, Timing Bug, ABI, Memory Layout, Human-in-the-Loop, Copilot
```

#### 適合做的專案

- AI-Assisted Driver Development Report
- LLM + STM32 Driver Review Checklist
- AI Debugging Workflow Demo
- AI-Generated Code Verification Pipeline
- Datasheet-Based Prompt Template Library
- Firmware Code Review Agent

#### 評價

這門課很適合赫霆，因為它結合：

- Embedded Systems
- AI Agent
- Prompt Engineering
- Firmware Safety
- Verification

這門課也可以變成很好的研究題目：「AI 輔助嵌入式韌體開發的安全性與驗證流程」。

---

## 2. 課程之間的差異

---

### A. 底層架構類

| 課程 | 重點 |
|---|---|
| Embedded Systems Programming on ARM Cortex-M3/M4 Processor | ARM Core、NVIC、Exception、Startup、Linker、Context Switch |
| ARMv8-M TrustZone on Cortex-M33 | Secure / Non-Secure、SAU、IDAU、TrustZone |
| STM32Fx Custom Bootloader Development | Boot Flow、Flash、Vector Table、Firmware Update |

#### 核心能力

```text
Processor Architecture, Exception Model, Startup, Linker, Security Isolation,
Boot Process, Firmware Update
```

---

### B. Peripheral Driver 類

| 課程 | 重點 |
|---|---|
| Embedded Systems Bare-Metal Programming Ground Up™ | 從 Register 寫所有常見 Peripheral |
| Mastering Microcontroller and Embedded Driver Development | 系統化寫 GPIO / SPI / I2C / USART Driver |
| Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2) | Timer / PWM / CAN / RTC / Low Power |
| ARM Cortex M DMA Programming | DMA 專題 |

#### 核心能力

```text
Register-Level Programming, Peripheral Driver, GPIO, UART, SPI, I2C, ADC,
Timer, PWM, CAN, DMA, Interrupt
```

---

### C. 系統整合類

| 課程 | 重點 |
|---|---|
| Mastering RTOS | FreeRTOS、多工、同步、Debug |
| Mastering STM32CubeMX 5 and CubeIDE | CubeMX 快速整合 USB / DMA / FreeRTOS / Peripheral |
| AI-Assisted Embedded Firmware Development | 用 AI 加速 Firmware 開發，但保留驗證與安全流程 |

#### 核心能力

```text
FreeRTOS, Task Scheduling, Synchronization, CubeMX, HAL, USB, Middleware,
AI-Assisted Development, Verification Workflow
```

---

## 3. 建議學習順序

---

### 路線 A：最扎實的 Firmware Engineer 路線

```text
1. Embedded Systems Bare-Metal Programming Ground Up™
        ↓
2. Mastering Microcontroller and Embedded Driver Development
        ↓
3. Embedded Systems Programming on ARM Cortex-M3/M4 Processor
        ↓
4. Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2)
        ↓
5. ARM Cortex M Microcontroller DMA Programming Demystified
        ↓
6. Mastering RTOS: FreeRTOS and STM32Fx
        ↓
7. STM32Fx Custom Bootloader Development
        ↓
8. ARMv8-M TrustZone on Cortex-M33
        ↓
9. AI-Assisted Embedded Firmware Development
```

---

### 路線 B：快速做作品路線

```text
1. Mastering STM32CubeMX 5 and CubeIDE
        ↓
2. Embedded Systems Bare-Metal Programming Ground Up™
        ↓
3. Mastering RTOS
        ↓
4. DMA Programming
        ↓
5. Bootloader Development
        ↓
6. AI-Assisted Embedded Firmware Development
```

---

### 路線 C：資安 + 嵌入式安全路線

```text
1. Embedded Systems Programming on ARM Cortex-M3/M4 Processor
        ↓
2. Embedded Systems Bare-Metal Programming Ground Up™
        ↓
3. STM32Fx Custom Bootloader Development
        ↓
4. ARMv8-M TrustZone on Cortex-M33
        ↓
5. AI-Assisted Embedded Firmware Development
```

---

### 路線 D：機器人 / 無人機 / 控制系統路線

```text
1. Embedded Systems Bare-Metal Programming Ground Up™
        ↓
2. Mastering Microcontroller and Embedded Driver Development
        ↓
3. Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2)
        ↓
4. DMA Programming
        ↓
5. Mastering RTOS
        ↓
6. AI-Assisted Embedded Firmware Development
```

---

## 4. 對赫霆最有價值的優先順序

如果目標是做出能放進學習歷程、申請大學、申請實習的作品，建議優先順序如下：

| 優先 | 課程 | 理由 |
|---|---|---|
| 1 | Embedded Systems Bare-Metal Programming Ground Up™ | 建立真正 Register-Level 能力 |
| 2 | Mastering Microcontroller and Embedded Driver Development | 系統化 Driver 能力 |
| 3 | Embedded Systems Programming on ARM Cortex-M3/M4 Processor | 理解 ARM Core / NVIC / Startup / Linker |
| 4 | Mastering Microcontroller: Timers, PWM, CAN, Low Power(MCU2) | 對機器人、控制、車用通訊很有用 |
| 5 | DMA Programming Demystified | 高速資料流、ADC、UART、Sensor System 必備 |
| 6 | Mastering RTOS | 做多工系統、機器人、IoT 必備 |
| 7 | STM32Fx Custom Bootloader Development | 作品集價值高 |
| 8 | ARMv8-M TrustZone | 嵌入式資安特色很強 |
| 9 | AI-Assisted Embedded Firmware Development | 可結合 AI Agent / Firmware Verification |
| 10 | STM32CubeMX 5 and CubeIDE | 適合快速做 Demo，但不建議當唯一主線 |

---

## 5. 最推薦做成作品集的專題

---

### 專題 1：STM32 Bare-Metal Driver Library

#### 專題內容

自己寫一套 STM32 Driver Library，包括：

- GPIO
- UART
- SPI
- I2C
- ADC
- Timer
- PWM
- DMA
- Interrupt

#### 對應課程

- Embedded Systems Bare-Metal Programming Ground Up™
- Mastering Microcontroller and Embedded Driver Development
- DMA Programming Demystified

#### 展示價值

可以證明你不是只會用 HAL，而是真的懂底層 Register。

---

### 專題 2：FreeRTOS Sensor Data Logger

#### 專題內容

使用 STM32 + FreeRTOS 建立多工資料記錄系統：

- Task 1：讀取 Sensor
- Task 2：UART 輸出
- Task 3：資料儲存
- ISR：處理外部事件
- Queue / Semaphore / Mutex
- DMA 加速資料搬移

#### 對應課程

- Mastering RTOS
- DMA Programming
- MCU1
- MCU2

#### 展示價值

可以展示 RTOS、多工、同步、DMA、Peripheral Integration。

---

### 專題 3：STM32 Custom Bootloader + Firmware Update Tool

#### 專題內容

做一個 UART Bootloader：

- Bootloader Region
- Application Region
- Vector Table Relocation
- Flash Erase / Program
- CRC Check
- PC Host Tool
- Firmware Version Check

#### 對應課程

- STM32Fx Custom Bootloader Development
- Embedded Systems Programming on ARM Cortex-M3/M4 Processor

#### 展示價值

非常接近業界 Firmware Update 機制，作品集含金量高。

---

### 專題 4：Secure Firmware with TrustZone

#### 專題內容

用 Cortex-M33 / LPC55S69 做：

- Secure World
- Non-Secure World
- Secure API
- Key Storage
- Secure Boot Prototype
- Non-Secure App 呼叫 Secure Function

#### 對應課程

- ARMv8-M TrustZone on Cortex-M33
- STM32Fx Custom Bootloader Development
- AI-Assisted Embedded Firmware Development

#### 展示價值

結合資安與嵌入式，對申請 CS / Cybersecurity / Embedded Systems 很有特色。

---

### 專題 5：AI-Assisted Firmware Verification Workflow

#### 專題內容

建立一套 AI 輔助 Firmware 開發流程：

- Prompt Template
- Driver Generation
- Datasheet Cross-Check
- Static Review Checklist
- Build Warning Policy
- Hardware Smoke Test
- AI Failure Case Report

#### 對應課程

- AI-Assisted Embedded Firmware Development
- Bare-Metal Programming
- MCU Driver Development

#### 展示價值

非常適合做成研究型學習歷程，主題新而且和 AI Agent 很接近。

---

## 6. 10 門課的共同核心 Keywords

```text
Embedded Systems, STM32, ARM Cortex-M, Cortex-M3, Cortex-M4, Cortex-M33,
Bare-Metal Programming, Embedded C, Register-Level Programming, CMSIS,
Peripheral Driver, GPIO, UART, USART, SPI, I2C, ADC, Timer, PWM, DMA,
CAN Bus, RTC, Low Power Mode, Interrupt, NVIC, SysTick, PendSV,
Exception Handling, Startup Code, Linker Script, Memory Map, AHB, APB,
Clock Tree, PLL, FreeRTOS, Task, Queue, Semaphore, Mutex, Scheduler,
Context Switching, SEGGER SystemView, Bootloader, Flash Programming,
Vector Table Relocation, IAP, TrustZone, Secure State, Non-Secure State,
SAU, IDAU, Secure Gateway, AI-Assisted Firmware, Prompt Engineering,
Datasheet Validation, Hardware Evidence
```

---

## 7. 一句話總結

這 10 門課如果全部串起來，其實是一條完整的 **Embedded Firmware Engineer Roadmap**：

```text
ARM Cortex-M Architecture
        ↓
Bare-Metal Register Programming
        ↓
Peripheral Driver Development
        ↓
Timer / PWM / CAN / DMA
        ↓
FreeRTOS Real-Time System
        ↓
Bootloader / Firmware Update
        ↓
TrustZone Embedded Security
        ↓
AI-Assisted Firmware Workflow
```

最重要的不是「看完課」，而是把課程內容變成 3～5 個可以展示的作品：

```text
1. STM32 Bare-Metal Driver Library
2. FreeRTOS Sensor Data Logger
3. STM32 Custom Bootloader
4. TrustZone Secure Firmware Demo
5. AI-Assisted Firmware Verification Workflow
```

這樣就能從「修課清單」變成真正有說服力的學習歷程與作品集。
