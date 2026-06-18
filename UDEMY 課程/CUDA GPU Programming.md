# CUDA / GPU Programming / Parallel Programming 課程比較整理

## 課程連結

1. [CUDA Programming Course – High-Performance Computing with GPUs](https://www.youtube.com/watch?v=86FAWCzIe_4)
2. [CUDA Programming for NVIDIA H100s – Comprehensive Course](https://www.youtube.com/watch?v=SqQUQHdYWyc)
3. [GPU Programming Specialization - Coursera](https://www.coursera.org/specializations/gpu-programming)
4. [Parallel, Concurrent, and Distributed Programming in Java Specialization - Coursera](https://www.coursera.org/specializations/pcdp)

---

# 一句話總結

| 課程                                   | 一句話定位                                           |
| ------------------------------------ | ----------------------------------------------- |
| CUDA HPC with GPUs                   | CUDA 入門到深度學習實作，適合開始寫 GPU kernel                 |
| CUDA for NVIDIA H100s                | Hopper / H100 進階 CUDA，偏 Tensor Core、WGMMA、多 GPU |
| GPU Programming Coursera             | 大學式 GPU Programming 專項，較系統化                     |
| Java Parallel/Concurrent/Distributed | 平行、並行、分散式觀念課，不是 GPU 課                           |

---

# 詳細比較

| 課程                       | 平台                         | 主要語言                            | 難度 | 重點                                              |
| ------------------------ | -------------------------- | ------------------------------- | -- | ----------------------------------------------- |
| CUDA HPC with GPUs       | freeCodeCamp / YouTube     | C++ / CUDA / Triton / PyTorch   | 中  | CUDA kernel、記憶體、矩陣乘法、PyTorch extension          |
| CUDA for NVIDIA H100s    | freeCodeCamp / YouTube     | CUDA C++ / PTX / CUTLASS / NCCL | 高  | H100、WGMMA、TMA、Tensor Core、Multi-GPU            |
| GPU Programming Coursera | Coursera / Johns Hopkins   | C / C++ / CUDA                  | 中高 | GPU programming 系統化訓練                           |
| Java PCDP Coursera       | Coursera / Rice University | Java                            | 中  | Parallelism、Concurrency、Distributed programming |

---

# 課程定位

## 1. CUDA Programming Course – High-Performance Computing with GPUs

這門比較適合作為 CUDA 第一門實作課。

內容包含：

* CUDA setup
* C / C++ review
* GPU 架構入門
* CUDA kernels
* CUDA API
* device memory / host memory
* matrix multiplication
* shared memory
* Triton
* PyTorch extensions
* MNIST MLP

核心目標是：

```text
用 CUDA 寫出可以在 GPU 上跑的程式
```

適合：

* 想開始寫 CUDA kernel
* 想理解 PyTorch 背後 GPU 運算
* 想學 matrix multiplication
* 想做 AI / HPC 加速

推薦程度：**9 / 10**

---

## 2. CUDA Programming for NVIDIA H100s – Comprehensive Course

這門不是一般 CUDA 入門課，而是 H100 / Hopper 架構進階課。

內容包含：

* H100 Hopper architecture
* HBM3
* Tensor Cores
* Tensor Memory Accelerator, TMA
* Thread Block Clusters
* Distributed Shared Memory
* Async operations
* Memory barriers
* WGMMA
* FP8
* CUTLASS
* kernel pipeline
* persistent scheduling
* multi-GPU programming
* NCCL
* AllReduce
* tensor parallel / pipeline parallel

核心目標是：

```text
理解現代 AI 訓練用 GPU 的高效矩陣乘法與多 GPU 通訊
```

適合：

* 已經懂 CUDA 基礎
* 想研究 H100 / Hopper
* 想理解 AI training kernel
* 想看懂 CUTLASS
* 想理解 NCCL / Multi-GPU
* 想走 GPU kernel engineer

推薦程度：**9.5 / 10**

但不建議第一門就學。

---

## 3. GPU Programming Specialization - Coursera

這是 Johns Hopkins University 的 GPU Programming 專項課程。

Coursera 頁面顯示它是 4 門課組成的專項，建議有至少一年程式經驗，最好有 C/C++ 基礎，預估約 2 個月完成。

內容方向通常包含：

* GPU programming foundation
* CUDA programming
* parallel programming concepts
* memory hierarchy
* performance optimization
* GPU-accelerated computing

核心目標是：

```text
用比較大學課程的方式，系統性學 GPU programming
```

適合：

* 想要 Coursera 證書
* 想要比 YouTube 更有作業結構
* 想補 GPU programming 基礎
* 想做 HPC / AI acceleration

推薦程度：**8.5 / 10**

---

## 4. Parallel, Concurrent, and Distributed Programming in Java Specialization

這是 Rice University 的 Java 專項課程。

Coursera 頁面顯示它是 3 門課組成，主題是 parallel、concurrent、distributed programming，適合已有 Java sequential programming 基礎的人。

它不是 GPU 課，而是更一般的平行與分散式程式設計。

內容包含：

* Parallel programming
* Concurrency
* Multithreading
* Fork/Join
* Futures
* Streams
* Locks
* Isolation
* Distributed programming
* Message passing
* Client-server programming

核心目標是：

```text
理解多核心 CPU、執行緒、同步、分散式系統
```

適合：

* 想補 parallel / concurrent 基礎
* 想理解 thread、lock、race condition
* 想寫大型後端系統
* 想理解 distributed computing
* 想補資工系平行程式設計

推薦程度：**8.5 / 10**

---

# 四門課的關係

這四門可以分成兩條線。

## GPU / CUDA 線

```text
CUDA HPC with GPUs
↓
GPU Programming Specialization
↓
CUDA for NVIDIA H100s
```

這條線是：

```text
GPU kernel
→ CUDA optimization
→ H100 / Tensor Core / Multi-GPU
```

---

## Parallel / Distributed 線

```text
Java Parallel, Concurrent, and Distributed Programming
```

這條線是：

```text
CPU 多執行緒
→ 並行控制
→ 分散式系統
```

---

# 學習順序建議

## 如果目標是 AI / GPU / CUDA

建議：

```text
1. CUDA Programming Course – High-Performance Computing with GPUs
↓
2. GPU Programming Specialization - Coursera
↓
3. CUDA Programming for NVIDIA H100s
↓
4. Java Parallel/Concurrent/Distributed
```

理由：

先能寫 CUDA，再系統化補 GPU programming，最後進 H100 與多 GPU。

---

## 如果目標是資工系平行計算基礎

建議：

```text
1. Java Parallel, Concurrent, and Distributed Programming
↓
2. GPU Programming Specialization
↓
3. CUDA HPC with GPUs
↓
4. CUDA for H100s
```

理由：

先懂平行、並行、分散式，再進 GPU。

---

## 如果目標是 GPU Kernel Engineer

建議：

```text
1. CUDA HPC with GPUs
↓
2. GPU Programming Specialization
↓
3. CUDA for NVIDIA H100s
```

重點能力：

```text
CUDA kernel
shared memory
memory coalescing
matrix multiplication
profiling
Triton
CUTLASS
WGMMA
NCCL
```

---

## 如果目標是 AI Infra / LLM Training

建議：

```text
1. CUDA HPC with GPUs
↓
2. CUDA for NVIDIA H100s
↓
3. Java Parallel/Concurrent/Distributed
↓
4. GPU Programming Specialization
```

理由：

LLM training 會碰到：

```text
Tensor Core
FP8
NCCL
AllReduce
Tensor Parallel
Pipeline Parallel
Distributed Training
```

---

# 如果只能選一門

## 想開始學 CUDA

```text
CUDA Programming Course – High-Performance Computing with GPUs
```

## 想挑戰高階 GPU / H100

```text
CUDA Programming for NVIDIA H100s
```

## 想要 Coursera 證書

```text
GPU Programming Specialization
```

## 想補平行 / 並行 / 分散式基礎

```text
Parallel, Concurrent, and Distributed Programming in Java
```

---

# 總排名

| 排名 | 課程                       | 推薦理由                                      |
| -- | ------------------------ | ----------------------------------------- |
| 1  | CUDA HPC with GPUs       | 最適合開始寫 CUDA，並接到 AI 實作                     |
| 2  | CUDA for NVIDIA H100s    | 最進階，對 AI Infra / H100 / LLM training 很有價值 |
| 3  | GPU Programming Coursera | 系統化、有證書，適合補 GPU programming               |
| 4  | Java PCDP Coursera       | 很重要，但不是 GPU 主線                            |

---

# 給自己的結論

以目前方向：

```text
AI
GPU
CUDA
Jetson
Edge AI
HPC
Parallel Computing
```

最適合的學習路線是：

```text
CUDA Programming Course – High-Performance Computing with GPUs
↓
GPU Programming Specialization
↓
CUDA Programming for NVIDIA H100s
↓
Parallel, Concurrent, and Distributed Programming in Java
```

這樣會形成完整能力鏈：

```text
CUDA 基礎
→ GPU memory / kernel / matrix multiplication
→ GPU programming 系統化訓練
→ H100 / Tensor Core / Multi-GPU
→ CPU parallel / distributed programming
```

如果未來想做：

* CUDA kernel optimization
* PyTorch custom operator
* Triton kernel
* LLM inference acceleration
* Multi-GPU training
* Jetson Edge AI acceleration

這四門裡最關鍵的是：

```text
CUDA HPC with GPUs
+
CUDA for NVIDIA H100s
```

Coursera GPU Programming 則適合當作比較正式、可放履歷的學習證明。