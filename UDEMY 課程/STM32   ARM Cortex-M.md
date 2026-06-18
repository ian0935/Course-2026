# STM32 / ARM Cortex-M / FreeRTOS / Driver / Bootloader 課程比較整理

## 課程連結

1. [ARM Cortex M Microcontroller DMA Programming Demystified](https://www.udemy.com/course/microcontroller-dma-programming-fundamentals-to-advanced/)
2. [ARMv8-M TrustZone on Cortex-M33 with LPC55S69](https://www.udemy.com/course/armv8-m-trust-zone-on-cortex-m33-embedded-security/)
3. [Embedded Systems Programming on ARM Cortex-M3/M4 Processor](https://www.udemy.com/course/embedded-system-programming-on-arm-cortex-m3m4/)
4. [Embedded Systems Bare-Metal Programming Ground Up™ (STM32)](https://www.udemy.com/course/embedded-systems-bare-metal-programming/)
5. [Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging](https://www.udemy.com/course/mastering-rtos-hands-on-with-freertos-arduino-and-stm32fx/)
6. [Mastering Microcontroller and Embedded Driver Development MCU1](https://www.udemy.com/course/mastering-microcontroller-with-peripheral-driver-development/)
7. [Mastering Microcontroller: Timers, PWM, CAN, Low Power MCU2](https://www.udemy.com/course/microcontroller-programming-stm32-timers-pwm-can-bus-protocol/)
8. [STM32Fx Microcontroller Custom Bootloader Development](https://www.udemy.com/course/stm32f4-arm-cortex-mx-custom-bootloader-development/)
9. [Mastering STM32CubeMX 5 and CubeIDE - Embedded Systems](https://www.udemy.com/course/stm32cubemx-5-and-cubeide/)

---

# 一句話總結

| 課程                            | 一句話定位                             |
| ----------------------------- | --------------------------------- |
| DMA Programming Demystified   | 專門深入 DMA，適合 ADC/UART/SPI 高速資料搬運   |
| ARMv8-M TrustZone             | Cortex-M33 安全隔離與 TrustZone        |
| ARM Cortex-M3/M4 Processor    | Cortex-M 處理器架構、NVIC、中斷、例外、啟動流程    |
| Bare-Metal STM32 Ground Up    | 不用 HAL，從暫存器/CMSIS 寫 STM32 driver  |
| Mastering RTOS FreeRTOS       | FreeRTOS 任務、排程、同步、除錯              |
| MCU1 Driver Development       | GPIO/SPI/I2C/USART driver 從零寫     |
| MCU2 Timers/PWM/CAN/Low Power | Timer、PWM、CAN、RTC、Low Power 進階外設  |
| Custom Bootloader             | STM32 bootloader、Flash、更新韌體       |
| STM32CubeMX 5 and CubeIDE     | 用 CubeMX/CubeIDE 快速建立 STM32 專案與外設 |

---

# 大分類

## 1. Cortex-M 核心架構

最適合先學：

* Embedded Systems Programming on ARM Cortex-M3/M4 Processor

它主要補：

```text
CPU 架構
NVIC
Interrupt
Exception
Stack
Startup code
Linker script
Memory map
```

這是 STM32 底層能力的根。

---

## 2. Bare-metal Driver 開發

最適合：

* Mastering Microcontroller and Embedded Driver Development MCU1
* Embedded Systems Bare-Metal Programming Ground Up™ (STM32)

這類課會教你不用 HAL，自己看 datasheet / reference manual 寫 driver。

重點：

```text
GPIO
USART
SPI
I2C
ADC
Interrupt
CMSIS
Register programming
```

---

## 3. 進階外設

最適合：

* Mastering Microcontroller: Timers, PWM, CAN, Low Power MCU2
* ARM Cortex M Microcontroller DMA Programming Demystified

這類課補的是產品開發會很常用，但初學者容易卡住的外設：

```text
Timer
PWM
Input Capture
Output Compare
CAN
RTC
Low Power
DMA
ADC + DMA
UART + DMA
SPI + DMA
```

---

## 4. RTOS

最適合：

* Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging

重點：

```text
Task
Scheduler
Queue
Semaphore
Mutex
Event Group
Timer
Interrupt + RTOS
SEGGER SystemView Debugging
```

這是從 bare-metal 走向大型韌體架構的關鍵。

---

## 5. Bootloader / Firmware Update

最適合：

* STM32Fx Microcontroller Custom Bootloader Development

重點：

```text
Boot mode
Vector table
Flash erase/program
Application jump
Firmware update protocol
Bootloader command packet
Option bytes
Flash protection
```

這是做產品韌體更新非常重要的能力。

---

## 6. Embedded Security

最適合：

* ARMv8-M TrustZone on Cortex-M33 with LPC55S69

重點：

```text
Secure world
Non-secure world
SAU
IDAU
Secure Gateway
Cortex-M33
ARMv8-M
Secure firmware
```

這門比較偏進階安全，不是 STM32 入門課。

---

## 7. CubeMX / CubeIDE 快速開發

最適合：

* Mastering STM32CubeMX 5 and CubeIDE - Embedded Systems

重點：

```text
CubeMX 設定
CubeIDE 開發
GPIO
UART
SPI
ADC
DMA
USB HID
USB CDC
FreeRTOS
```

它比較偏工具與快速開發，不是純 register-level 課程。

---

# 詳細比較表

| 課程                            | 主題                        | 難度 | 偏向         | 是否適合初學          |
| ----------------------------- | ------------------------- | -: | ---------- | --------------- |
| ARM Cortex-M3/M4 Processor    | CPU 核心架構                  | 中高 | 底層原理       | 適合有 C 基礎        |
| Bare-Metal STM32 Ground Up    | STM32 暫存器開發               | 中高 | Bare-metal | 適合              |
| MCU1 Driver Development       | GPIO/SPI/I2C/USART driver |  中 | Driver     | 很適合             |
| MCU2 Timers/PWM/CAN/Low Power | Timer/CAN/低功耗             | 中高 | 進階外設       | 建議 MCU1 後       |
| DMA Programming               | DMA 專題                    | 中高 | 效能/資料搬運    | 建議 ADC/UART 後   |
| FreeRTOS                      | RTOS                      | 中高 | 系統架構       | 建議 bare-metal 後 |
| Bootloader                    | 韌體更新                      |  高 | 系統/Flash   | 建議 driver 後     |
| TrustZone                     | 嵌入式安全                     |  高 | Security   | 不適合第一門          |
| CubeMX/CubeIDE                | 工具/快速開發                   |  中 | HAL/CubeMX | 適合快速上手          |

---

# 各課程詳細說明

## 1. ARM Cortex M Microcontroller DMA Programming Demystified

這門專門講 DMA。

DMA 的意思是：

```text
Direct Memory Access
```

白話：

```text
不用 CPU 一筆一筆搬資料
讓 DMA 幫你搬
CPU 去做其他事情
```

例如：

```text
ADC 連續取樣
↓
DMA 自動搬到 RAM
↓
CPU 每隔一段時間處理一批資料
```

適合用途：

* ADC 高速取樣
* UART 大量資料接收
* SPI sensor streaming
* Audio / DSP
* IMU 資料流
* Edge AI 前處理

推薦程度：**9 / 10**

但建議不要第一門學，最好先懂 UART、ADC、Interrupt。

---

## 2. ARMv8-M TrustZone on Cortex-M33 with LPC55S69

這門偏嵌入式安全。

TrustZone 的核心概念是：

```text
Secure World
+
Non-Secure World
```

例如：

```text
加密金鑰
安全開機
安全韌體
```

放在 Secure World。

一般應用程式放在 Non-Secure World。

適合用途：

* IoT Security
* Secure Boot
* Firmware Protection
* Key Storage
* ARMv8-M Security
* Cortex-M33

推薦程度：**8 / 10**

但它是進階課，建議順序排後面。

---

## 3. Embedded Systems Programming on ARM Cortex-M3/M4 Processor

這門是 Cortex-M 核心架構課。

它不是單純教 STM32 外設，而是教 CPU 本身。

重點：

* ARM Cortex-M3/M4 架構
* Memory map
* Stack
* MSP / PSP
* Exception
* Interrupt
* NVIC
* Priority
* Preemption
* Systick
* Startup code
* Linker script
* Inline Assembly

這門很像：

```text
嵌入式系統的作業系統底層課
```

適合：

* 想真正理解 Interrupt
* 想理解 FreeRTOS 為什麼能切換 task
* 想看懂 startup file
* 想寫 bootloader
* 想做嵌入式安全

推薦程度：**9.5 / 10**

---

## 4. Embedded Systems Bare-Metal Programming Ground Up™ (STM32)

這門是 BHM / EmbeddedExpertIO 的 STM32 bare-metal 大課。

特色是：

```text
不用 HAL
不用第三方 library
直接操作 register
```

重點：

* GPIO
* ADC
* UART
* Timer
* PWM
* Interrupt
* SPI
* I2C
* RTC
* DMA
* CMSIS
* Debugging

這門比較像：

```text
STM32 暫存器開發完整訓練
```

適合：

* STM32 初中階
* 想理解 HAL 背後在幹嘛
* 想寫自己的 driver
* 想練 reference manual 閱讀能力

推薦程度：**9.5 / 10**

---

## 5. Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging

這門是 FreeRTOS 主線課。

你會學：

* Task
* Task priority
* Scheduler
* Context switch
* Queue
* Semaphore
* Mutex
* Timer
* Event
* Interrupt with RTOS
* Debugging
* SEGGER SystemView

白話：

bare-metal 是：

```text
while(1)
{
    讀 sensor
    控 motor
    傳 UART
}
```

RTOS 是：

```text
Task 1: 讀 sensor
Task 2: 控 motor
Task 3: 傳 UART
Task 4: AI inference
```

這對大型 STM32 專案非常重要。

推薦程度：**9.5 / 10**

---

## 6. Mastering Microcontroller and Embedded Driver Development MCU1

這門是 FastBit 很經典的 driver development 課。

重點：

* GPIO Driver
* SPI Driver
* I2C Driver
* USART Driver
* Driver API 設計
* Header file
* Source file
* Register map
* Peripheral clock
* Interrupt handling
* Datasheet / reference manual

它比 CubeMX 更底層。

你會學到：

```text
如何把 reference manual 變成 driver code
```

適合：

* STM32 driver 入門
* 嵌入式韌體基礎
* 想走 embedded software engineer
* 想理解 HAL 原理

推薦程度：**9.5 / 10**

---

## 7. Mastering Microcontroller: Timers, PWM, CAN, Low Power MCU2

這門是 MCU1 的進階課。

重點：

* Basic Timer
* General Purpose Timer
* Input Capture
* Output Compare
* PWM
* CAN Protocol
* CAN Filtering
* RTC
* Low Power Mode
* Wakeup
* Power Management

用途：

```text
馬達控制
伺服控制
車用 CAN Bus
低功耗 IoT 裝置
時間測量
頻率測量
```

這門很實用，尤其如果你做：

* 無人機
* 自走車
* 機器人
* 車用通訊
* 低功耗感測器

推薦程度：**9 / 10**

---

## 8. STM32Fx Microcontroller Custom Bootloader Development

這門是 bootloader 專門課。

你會學：

* Bootloader 是什麼
* STM32 boot modes
* Flash memory layout
* Vector table
* Jump to application
* Flash erase
* Flash program
* UART bootloader protocol
* Command packet
* Option bytes
* Read/write protection
* Firmware update

白話：

一般程式：

```text
上電
↓
直接跑 main()
```

Bootloader 架構：

```text
上電
↓
Bootloader
↓
檢查是否要更新韌體
↓
跳到 Application
```

這是產品化很重要的能力。

推薦程度：**9 / 10**

---

## 9. Mastering STM32CubeMX 5 and CubeIDE - Embedded Systems

這門偏 CubeMX / CubeIDE 工具實戰。

重點：

* CubeMX 產生專案
* Clock configuration
* GPIO
* UART
* ADC
* SPI
* DMA
* USB HID Mouse
* USB HID Keyboard
* USB Virtual COM Port
* FreeRTOS
* CubeIDE debugging

它不像 MCU1 那樣從 register 寫 driver，而是比較偏：

```text
用 ST 官方工具快速做出功能
```

適合：

* 快速做專案
* 快速測外設
* 想學 USB HID / CDC
* 不想一開始全部寫 register

推薦程度：**8 / 10**

---

# 建議學習順序

## 如果目標是 STM32 韌體工程師

建議順序：

```text
1. Embedded Systems Programming on ARM Cortex-M3/M4 Processor
↓
2. Mastering Microcontroller and Embedded Driver Development MCU1
↓
3. Mastering Microcontroller: Timers, PWM, CAN, Low Power MCU2
↓
4. ARM Cortex M Microcontroller DMA Programming Demystified
↓
5. Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging
↓
6. STM32Fx Microcontroller Custom Bootloader Development
↓
7. ARMv8-M TrustZone on Cortex-M33
```

---

## 如果目標是快速做 STM32 專案

建議順序：

```text
1. Mastering STM32CubeMX 5 and CubeIDE
↓
2. Mastering Microcontroller and Embedded Driver Development MCU1
↓
3. Mastering RTOS: FreeRTOS and STM32Fx
↓
4. DMA Programming
↓
5. Bootloader
```

---

## 如果目標是無人機 / 機器人 / ROS 底層

建議順序：

```text
1. ARM Cortex-M3/M4 Processor
↓
2. MCU1 Driver Development
↓
3. MCU2 Timers/PWM/CAN/Low Power
↓
4. DMA Programming
↓
5. FreeRTOS
↓
6. Bootloader
```

理由：

機器人底層很常用：

```text
PWM
Timer
Encoder
UART
SPI
I2C
CAN
DMA
RTOS
```

---

## 如果目標是 IoT Security / Firmware Security

建議順序：

```text
1. ARM Cortex-M3/M4 Processor
↓
2. MCU1 Driver Development
↓
3. Custom Bootloader Development
↓
4. DMA Programming
↓
5. ARMv8-M TrustZone on Cortex-M33
```

理由：

要做嵌入式安全，必須懂：

```text
Memory map
Boot process
Flash
Interrupt
DMA
Secure / Non-secure world
```

---

# 如果只能選 3 門

## 最推薦組合

```text
1. Embedded Systems Programming on ARM Cortex-M3/M4 Processor
2. Mastering Microcontroller and Embedded Driver Development MCU1
3. Mastering RTOS: Hands on FreeRTOS and STM32Fx with Debugging
```

這三門組合最完整：

```text
Cortex-M 核心
+
Peripheral Driver
+
RTOS
```

---

## 如果偏產品化

```text
1. MCU1 Driver Development
2. FreeRTOS
3. Custom Bootloader Development
```

---

## 如果偏機器人 / 控制

```text
1. MCU1 Driver Development
2. MCU2 Timers/PWM/CAN/Low Power
3. DMA Programming
```

---

## 如果偏安全

```text
1. ARM Cortex-M3/M4 Processor
2. Custom Bootloader Development
3. ARMv8-M TrustZone
```

---

# 總排名

| 排名 | 課程                                                             | 推薦理由                    |
| -- | -------------------------------------------------------------- | ----------------------- |
| 1  | Embedded Systems Programming on ARM Cortex-M3/M4 Processor     | 最能補 Cortex-M 核心底層       |
| 2  | Mastering Microcontroller and Embedded Driver Development MCU1 | 最經典 driver 開發課          |
| 3  | Embedded Systems Bare-Metal Programming Ground Up™             | STM32 register-level 大課 |
| 4  | Mastering RTOS: FreeRTOS and STM32Fx                           | 大型韌體架構必學                |
| 5  | MCU2 Timers/PWM/CAN/Low Power                                  | 機器人、車用、控制很重要            |
| 6  | DMA Programming Demystified                                    | 高速資料搬運與 DSP/ADC 必學      |
| 7  | Custom Bootloader Development                                  | 產品化與韌體更新必學              |
| 8  | STM32CubeMX 5 and CubeIDE                                      | 快速開發工具課                 |
| 9  | ARMv8-M TrustZone                                              | 嵌入式安全進階課                |

---

# 給你的建議

以你目前方向：

```text
STM32
ROS
Jetson
Edge AI
機器人
無人機
資安
韌體逆向
```

最適合你的主線是：

```text
Embedded Systems Programming on ARM Cortex-M3/M4 Processor
↓
Mastering Microcontroller and Embedded Driver Development MCU1
↓
MCU2 Timers/PWM/CAN/Low Power
↓
DMA Programming Demystified
↓
Mastering RTOS FreeRTOS
↓
Custom Bootloader Development
↓
TrustZone on Cortex-M33
```

這條線會讓你從：

```text
CPU 架構
→ Driver
→ Timer/PWM/CAN
→ DMA
→ RTOS
→ Bootloader
→ Embedded Security
```

一路補完整。

如果之後要接：

```text
STM32 + 感測器
STM32 + Jetson
STM32 + ROS 2
STM32 + Edge AI
STM32 + 韌體安全
```

這套課程路線非常有長期價值。