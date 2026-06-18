# Assembly / Reverse Engineering / ARM / x86 課程比較整理

## 課程連結

1. [64-bit ARM Assembly Foundation Course for Ethical Hackers](https://www.udemy.com/course/64-bit-arm-assembly-foundation-course-for-ethical-hackers/?couponCode=PMNVD2025)
2. [Assembly Language Foundation Course for Ethical Hackers](https://www.udemy.com/course/assembly-mastery-for-ethical-hacking-penetration-testing/?couponCode=PMNVD2025)
3. [Assembly Language Programming](https://www.udemy.com/course/assembly-language-programming/?couponCode=PMNVD2025)
4. [AI and MCP for Reverse Engineering](https://www.udemy.com/course/ai-mcp-reverse-engineering/?couponCode=PMNVD2025)
5. [x64 Assembly Language and Reverse Engineering Practicals](https://www.udemy.com/course/x64-assembly-reverse-engineering-practicals/?couponCode=PMNVD2025)
6. [Computer Organization and Assembly Language](https://www.udemy.com/course/computer-organization-and-assembly-language/?couponCode=PMNVD2025)
7. [x86 Assembly Programming From Ground Up](https://www.udemy.com/course/x86-assembly-programming-from-ground-uptm/?couponCode=PMNVD2025)
8. [Assembly Language Programming for Reverse Engineering](https://www.udemy.com/course/assembly-for-reverse-engineering/?couponCode=PMNVD2025)
9. [ARM Assembly Language From Ground Up](https://www.udemy.com/course/arm-assembly-programming/?couponCode=PMNVD2025)

---

# 一句話總結

| 課程                                                    | 一句話定位                                       |
| ----------------------------------------------------- | ------------------------------------------- |
| 64-bit ARM Assembly Foundation for Ethical Hackers    | ARM64 架構 + 資安逆向基礎                           |
| Assembly Language Foundation for Ethical Hackers      | 給資安人的 Assembly 入門                           |
| Assembly Language Programming                         | 偏一般 Assembly 程式設計                           |
| AI and MCP for Reverse Engineering                    | 用 AI / LLM / MCP 輔助逆向工程                     |
| x64 Assembly Reverse Engineering Practicals           | x64dbg 實戰逆向與修改程式                            |
| Computer Organization and Assembly Language           | 電腦組織 + Assembly + GDB/Ghidra + exploit 基礎   |
| x86 Assembly Programming From Ground Up               | 最完整的 x86/x64 Assembly 基礎與 SIMD              |
| Assembly Language Programming for Reverse Engineering | x86 逆向工程入門，偏 x64dbg 實作                      |
| ARM Assembly Language From Ground Up                  | ARM / Thumb / Peripheral Driver Assembly 實作 |

---

# 類型分類

## x86 / x64 類

適合 Windows 逆向、malware analysis、CTF pwn/rev：

* x86 Assembly Programming From Ground Up
* Assembly Language Programming for Reverse Engineering
* x64 Assembly Language and Reverse Engineering Practicals
* Assembly Language Foundation Course for Ethical Hackers
* Computer Organization and Assembly Language

---

## ARM 類

適合 ARM、Android、iOS、IoT、嵌入式逆向：

* ARM Assembly Language From Ground Up
* 64-bit ARM Assembly Foundation Course for Ethical Hackers

---

## AI 輔助逆向類

適合已經懂一點逆向，想用 LLM 提升分析效率：

* AI and MCP for Reverse Engineering

---

# 詳細比較表

| 課程                                          | 架構              | 偏向                      | 難度 | 適合目標                            |
| ------------------------------------------- | --------------- | ----------------------- | -- | ------------------------------- |
| 64-bit ARM Assembly Foundation              | ARM64           | ARM64 + Ethical Hacking | 中高 | ARM64 逆向、Android/iOS/IoT        |
| Assembly Foundation for Ethical Hackers     | x86/x64 可能較多    | 資安 Assembly 基礎          | 中  | CEH/OSCP/逆向入門                   |
| Assembly Language Programming               | 一般 Assembly     | 程式設計                    | 中  | Assembly 基礎與數學/圖形練習             |
| AI and MCP Reverse Engineering              | x86/x64 + tools | AI 輔助逆向                 | 高  | LLM + x64dbg/Ghidra/IDA 自動化     |
| x64 Assembly Reverse Engineering Practicals | x64             | x64dbg 實戰逆向             | 高  | Windows x64 逆向、patch、keygen     |
| Computer Organization and Assembly          | x86 32-bit      | 電腦組織 + exploit 基礎       | 中高 | CS基礎、GDB、Ghidra、buffer overflow |
| x86 Assembly From Ground Up                 | x86/x64         | Assembly 正統基礎           | 中  | x86、SIMD、C/C++ 混合組語             |
| Assembly for Reverse Engineering            | x86             | 逆向工程入門                  | 中  | x64dbg、修改 exe、code cave         |
| ARM Assembly From Ground Up                 | ARM / Thumb     | ARM Assembly + 驅動       | 中高 | STM32、嵌入式、ARM driver            |

---

# 各課程定位

## 1. 64-bit ARM Assembly Foundation Course for Ethical Hackers

這門是 ARM64 方向。

重點包含：

* ARM architecture
* ARM64 registers
* ARM64 instruction set
* memory layout
* stack
* function call
* calling convention
* reverse engineering
* ethical hacking

適合未來想碰：

* Android 逆向
* iOS / macOS ARM64 逆向
* IoT 韌體分析
* ARM Linux binary analysis
* ARM64 exploit 基礎

推薦程度：**8.5 / 10**

---

## 2. Assembly Language Foundation Course for Ethical Hackers

這門比較像「給資安人的 Assembly 入門」。

重點不是做完整系統程式，而是理解：

* CPU
* registers
* memory
* stack
* assembly syntax
* reverse engineering
* 程式底層運作

適合：

* CEH 後想往 OSCP / exploit / reverse 前進
* 想看懂 disassembly
* 想補底層資安基礎

推薦程度：**8 / 10**

---

## 3. Assembly Language Programming

這門比較偏一般 Assembly 程式設計。

內容看起來包含：

* arithmetic
* string library
* graphics library
* vector / matrix
* complex numbers
* Fourier series

它不是最偏資安，而是比較像：

```text
用 Assembly 寫程式
```

適合想訓練底層程式感的人。

推薦程度：**6.5 / 10**

---

## 4. AI and MCP for Reverse Engineering

這門很新，也很特別。

重點是：

* MCP
* LLM
* Claude Desktop
* LM Studio
* OpenAI API
* x64dbg
* dnSpy
* Ghidra
* Cutter
* IDA Pro
* AI-assisted reverse engineering
* 自己寫 MCP server

它不是 Assembly 入門課，而是：

```text
已經會一點逆向
然後用 AI 加速分析
```

適合：

* 已經會 x64dbg / Ghidra
* 想把 LLM 接進逆向工具
* 想做 AI 自動分析 binary
* 想研究 malware analysis 自動化

推薦程度：**9 / 10**

但不建議第一門就學它。

---

## 5. x64 Assembly Language and Reverse Engineering Practicals

這門是 Paul Chin 的 x64 逆向實戰課。

它通常接在：

```text
Assembly Language Programming for Reverse Engineering
```

後面。

重點是：

* x64 assembly
* x64dbg
* 修改 64-bit exe
* code injection
* code caves
* patching
* calling convention
* stack frame
* keygen
* anti-debug
* memory patching

適合：

* Windows x64 逆向
* CTF reversing
* malware analysis 基礎
* binary patching
* 想從 x86 進階到 x64

推薦程度：**9 / 10**

---

## 6. Computer Organization and Assembly Language

這門比較偏正式 CS 基礎。

重點包含：

* x86 32-bit assembly
* GCC build process
* preprocessing
* compilation
* assembly
* linking
* loader
* shared libraries
* process address space
* CPU / registers / RAM / cache
* GDB
* Ghidra
* objdump
* buffer overflow
* ASLR
* stack smashing protection
* DEP

這門很適合補：

```text
資工系底層基礎
+
資安 exploit 基礎
```

推薦程度：**9 / 10**

---

## 7. x86 Assembly Programming From Ground Up

這門是 x86 Assembly 正統基礎課。

重點包含：

* x86 instruction set
* x86-32 / x86-64 差異
* registers
* flags
* memory addressing
* C/C++ mixed assembly
* MMX
* SSE
* AVX
* image processing
* DSP routines
* IEEE-754 floating point

這門不只是資安，而是完整學 x86。

適合：

* 想扎實學 x86
* 想理解 C/C++ 編譯後的底層
* 想看懂 disassembly
* 想學 SIMD / AVX
* 想往 exploit / reverse / performance optimization

推薦程度：**9.5 / 10**

---

## 8. Assembly Language Programming for Reverse Engineering

這門是逆向工程導向 Assembly。

重點包含：

* x64dbg
* CPU registers
* stack
* function calls
* flags
* jumps
* compare instructions
* code caves
* modifying programs
* injecting code into exe
* hollowing exe

這門很適合當：

```text
Windows 逆向第一門實戰課
```

推薦程度：**9 / 10**

---

## 9. ARM Assembly Language From Ground Up

這門是 ARM / Thumb / Thumb-2 的正統實作課。

重點包含：

* ARM instruction set
* Thumb / Thumb-2
* RISC architecture
* state machines
* data structures
* lookup tables
* jump tables
* GPIO driver
* UART driver
* ADC driver
* GPTM driver
* embedded algorithms
* DSP routines

它比較偏：

```text
嵌入式 ARM Assembly
```

不是純逆向。

適合：

* STM32
* Cortex-M
* 嵌入式韌體
* bare-metal
* driver development
* IoT firmware

推薦程度：**9 / 10**

---

# 建議學習順序

## 如果目標是 CTF Reverse / Malware Analysis / Windows 逆向

建議：

```text
1. Computer Organization and Assembly Language
↓
2. x86 Assembly Programming From Ground Up
↓
3. Assembly Language Programming for Reverse Engineering
↓
4. x64 Assembly Language and Reverse Engineering Practicals
↓
5. AI and MCP for Reverse Engineering
```

理由：

先補 CS 底層，再學 x86/x64，再進入 x64dbg 實戰，最後用 AI 自動化。

---

## 如果目標是 OSCP / Exploit Development / Binary Exploitation

建議：

```text
1. Computer Organization and Assembly Language
↓
2. x86 Assembly Programming From Ground Up
↓
3. Assembly Language Foundation Course for Ethical Hackers
↓
4. Assembly Language Programming for Reverse Engineering
↓
5. x64 Assembly Reverse Engineering Practicals
```

理由：

OSCP 不一定要求很深逆向，但懂 stack、calling convention、GDB、buffer overflow 會很有幫助。

---

## 如果目標是 ARM / IoT / Android / 嵌入式逆向

建議：

```text
1. ARM Assembly Language From Ground Up
↓
2. 64-bit ARM Assembly Foundation Course for Ethical Hackers
↓
3. Computer Organization and Assembly Language
↓
4. AI and MCP for Reverse Engineering
```

理由：

先學 ARM / Thumb / Cortex-M，再補 ARM64 與逆向工具。

---

## 如果目標是 STM32 / 嵌入式韌體

建議：

```text
1. ARM Assembly Language From Ground Up
↓
2. x86 Assembly Programming From Ground Up
↓
3. Computer Organization and Assembly Language
```

理由：

STM32 最相關的是 ARM Assembly，而 x86 可以幫助理解一般電腦架構與 C/C++ 底層。

---

# 如果只能選 3 門

我會選：

```text
1. Computer Organization and Assembly Language
2. x86 Assembly Programming From Ground Up
3. Assembly Language Programming for Reverse Engineering
```

原因：

這三門組合最平衡：

```text
CS底層基礎
+
x86/x64 Assembly
+
逆向實戰
```

---

# 如果偏 ARM / 嵌入式，只選 3 門

```text
1. ARM Assembly Language From Ground Up
2. 64-bit ARM Assembly Foundation Course for Ethical Hackers
3. Computer Organization and Assembly Language
```

---

# 如果偏資安逆向，只選 3 門

```text
1. Assembly Language Programming for Reverse Engineering
2. x64 Assembly Language and Reverse Engineering Practicals
3. AI and MCP for Reverse Engineering
```

但這個組合比較不適合完全零基礎。

---

# 總排名

| 排名 | 課程                                                    | 推薦理由                            |
| -- | ----------------------------------------------------- | ------------------------------- |
| 1  | x86 Assembly Programming From Ground Up               | x86/x64 基礎最扎實，還有 SIMD           |
| 2  | Computer Organization and Assembly Language           | CS 底層 + GDB/Ghidra + exploit 基礎 |
| 3  | Assembly Language Programming for Reverse Engineering | Windows 逆向入門最直接                 |
| 4  | x64 Assembly Reverse Engineering Practicals           | x64 逆向進階實戰                      |
| 5  | ARM Assembly Language From Ground Up                  | ARM / STM32 / 嵌入式最有價值           |
| 6  | AI and MCP for Reverse Engineering                    | 很新，但適合有逆向基礎後學                   |
| 7  | 64-bit ARM Assembly Foundation                        | ARM64 資安方向有用                    |
| 8  | Assembly Foundation for Ethical Hackers               | 資安導向 Assembly 入門                |
| 9  | Assembly Language Programming                         | 較一般，優先度最低                       |

---

# 給你的建議

以你目前背景：

* C / C++
* Python
* ROS
* STM32
* CTF
* Cybersecurity
* 想走 OSCP / Reverse / Embedded / Edge AI

最適合你的主線是：

```text
Computer Organization and Assembly Language
↓
x86 Assembly Programming From Ground Up
↓
Assembly Language Programming for Reverse Engineering
↓
x64 Assembly Reverse Engineering Practicals
↓
ARM Assembly Language From Ground Up
↓
64-bit ARM Assembly Foundation
↓
AI and MCP for Reverse Engineering
```

這條路線會同時補到：

```text
資工底層
+
x86/x64
+
逆向工程
+
ARM/嵌入式
+
AI輔助逆向
```

如果你之後要做 CTF rev/pwn、malware analysis、IoT firmware reversing、STM32/ARM 開發，這組課程會很有長期價值。
