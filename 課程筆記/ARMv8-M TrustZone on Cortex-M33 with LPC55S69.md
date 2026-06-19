# ARMv8-M TrustZone on Cortex-M33 with LPC55S69

# 目錄

- [[#1. 課程總覽比較表|1. 課程總覽比較表]]
- [[#2. 課程定位|2. 課程定位]]
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

# 1. 課程總覽比較表

| 項目 | 內容 |
|------|------|
| 課程名稱 | ARMv8-M TrustZone on Cortex-M33 with LPC55S69 |
| 領域 | Embedded Security / ARM Security Architecture |
| 難度 | ★★★★★ |
| 時數 | 6小時47分鐘 |
| 評分 | 5.0 / 5 |
| 學員數 | 2,100+ |
| 開發板 | LPC55S69 |
| 核心技術 | ARM TrustZone、SAU、IDAU、CMSIS |
| 價值等級 | 專家級 Embedded Security |

# 2. 課程定位

## 2.1 課程特色

這門課是非常少見的 ARM Cortex-M33 TrustZone 專門課程。

大部分 STM32 或 Cortex-M 課程只教：

- GPIO
- UART
- SPI
- RTOS

但本課程直接進入：

- Secure World
- Non-Secure World
- Trusted Execution Environment (TEE)
- Hardware Security Architecture

層級。

課程同時涵蓋：

- ARMv8-M Security Architecture
- TrustZone Security Model
- Secure Boot 基礎概念
- Secure Firmware Design
- Secure Memory Partitioning
- Secure Interrupt Handling
- Hardware Isolation

是典型的 Embedded Security 高階課程。

## 2.2 適合對象

- Embedded Engineer
- Firmware Engineer
- IoT Security Engineer
- Automotive Security Engineer
- Secure MCU Developer
- ARM Cortex-M 開發者
- 資安研究人員

# 3. 上課重點

- ARMv8-M Architecture
- Cortex-M33 Security Model
- TrustZone
- Secure State
- Non-Secure State
- NSC Region
- SAU
- IDAU
- CMSIS Security
- Secure Interrupts
- Secure Exceptions
- Secure Firmware Development
- TrustZone Debugging

# 4. 課程主要綱要

## ARMv8-M Security Architecture

- ARMv8-M 演進
- Cortex-M33 架構
- Bus Interface
- Security Context

## TrustZone 核心概念

- Secure World
- Non-Secure World
- Security Attribution
- Secure Gateway

## Memory Partitioning

- SAU
- IDAU
- Address Decoding
- Security Regions
- Peripheral Security

## Security Instructions

- SG
- BLXNS
- BXNS
- TT
- TTT
- TTA
- TTAT

## Secure Exception Handling

- Secure Interrupts
- NVIC Security
- VTOR_S
- VTOR_NS
- HardFault
- BusFault
- NMI

## CMSIS Security APIs

- cmse_check_address_range()
- Security Macros
- Secure Interface Export

## 實驗專案

- Secure Firmware
- Non-Secure Firmware
- Secure Library Interface
- LPC55S69 Security Project

# 5. Important Keywords

ARMv8-M, Cortex-M33, TrustZone, Trusted Execution Environment, TEE, Secure World, Non-Secure World, SAU, IDAU, Security Attribution Unit, CMSIS, Secure Gateway, SG Instruction, BLXNS, BXNS, Secure Interrupts, Secure Exceptions, VTOR_S, VTOR_NS, LPC55S69, Embedded Security, Firmware Security, Secure Boot, Hardware Isolation

# 6. 技術能力地圖

Embedded C

↓

ARM Cortex-M

↓

RTOS

↓

ARMv8-M Architecture

↓

TrustZone

↓

Secure Firmware

↓

Trusted Execution Environment

↓

Embedded Security Architect

# 7. 可做的專題

## 入門

- Secure GPIO Control
- Secure UART Communication

## 中階

- TrustZone Secure Storage
- Secure Firmware Update System
- Secure Sensor Gateway

## 高階

- Secure IoT Device
- Trusted Medical Device
- Secure Smart Lock
- Secure Industrial Controller
- Secure Robotics Platform

# 8. 對 AI Engineer 的價值

直接價值較低。

但若未來進入：

- Edge AI
- Secure AI Devices
- AIoT

則會非常有用。

價值評分：6/10

# 9. 對 Cybersecurity 的價值

極高。

因為課程本質就是：

Embedded Security。

涵蓋：

- Hardware Root of Trust
- Trusted Execution Environment
- Secure Isolation
- Secure Boot Concept

價值評分：10/10

# 10. 對 Embedded Systems 的價值

幾乎是頂級課程。

因為目前：

- Cortex-M33
- Cortex-M35P
- Secure MCU

都大量使用 TrustZone。

價值評分：10/10

# 11. 對研究與論文的價值

適合：

- Embedded Security
- IoT Security
- Secure Firmware
- Trusted Execution Environment
- Automotive Security
- Medical Device Security
- Hardware Security

研究方向。

價值評分：10/10

# 12. 學習順序建議

1. Embedded C
2. ARM Cortex-M
3. STM32 Development
4. RTOS
5. Embedded Linux
6. ARMv8-M TrustZone
7. Secure Firmware Development
8. Embedded Security Research

# 13. 履歷與學習歷程價值

★★★★★

這是大部分學生完全沒接觸過的內容。

可展示：

- Advanced Embedded Security
- ARM Security Architecture
- Secure Firmware Development
- TrustZone Development
- Hardware Security Design

對申請：

- 資安研究所
- Embedded Systems
- Robotics
- Secure IoT

非常有辨識度。

# 14. 一句話總結

TrustZone 是 ARM Cortex-M33 時代最重要的安全架構，本課程完整教授 Secure Firmware 設計、硬體隔離與 Trusted Execution Environment 建構能力。

# 15. 最終評價

| 項目 | 評分 |
|--------|--------|
| Embedded價值 | 10/10 |
| Cybersecurity價值 | 10/10 |
| AI價值 | 6/10 |
| 研究價值 | 10/10 |
| 專業度 | 10/10 |
| 難度 | 9/10 |
| 履歷加分 | 10/10 |
| 綜合推薦 | 9.8/10 |
