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
    

# LLMOps And AIOps Bootcamp With 8 End To End Projects

# 1. 課程總覽比較表

|項目|內容|
|---|---|
|課程名稱|LLMOps And AIOps Bootcamp With 8 End To End Projects|
|領域|LLMOps、MLOps、DevOps、Cloud AI Deployment|
|難度|★★★★★|
|核心定位|Production-Ready AI System Deployment|
|適合對象|AI Engineer、MLOps Engineer、LLMOps Engineer|
|先備知識|Python、Docker、LangChain、RAG|
|實務價值|★★★★★|
|作品集價值|★★★★★|
|推薦程度|★★★★★|

本課程專注於 LLM 應用的生產環境部署（Production Deployment）。課程涵蓋 Docker、Kubernetes、Jenkins、GitHub Actions、GitLab CI/CD、ArgoCD、AWS、GCP、Prometheus、Grafana、ELK Stack 等企業級工具，並透過 8 個完整專案展示如何從開發、測試、部署到監控 AI 系統。

# 2. 課程定位

## 2.1 課程特色

- 8 個完整 LLMOps 專案
    
- Jenkins CI/CD
    
- GitHub Actions
    
- GitLab CI/CD
    
- CircleCI
    
- ArgoCD
    
- Docker 容器化
    
- Kubernetes 部署
    
- AWS Fargate
    
- GCP GKE
    
- Vector Database
    
- Monitoring & Observability
    
- ELK Stack
    
- SonarQube
    
- Trivy Security Scan
    
- Production AI Deployment
    

## 2.2 適合對象

- AI Engineer
    
- LLM Engineer
    
- Agent Engineer
    
- MLOps Engineer
    
- DevOps Engineer
    
- Cloud Engineer
    
- AI Startup Founder
    
- AI Product Engineer
    

# 3. 上課重點

- LLMOps Fundamentals
    
- Production AI Systems
    
- LangChain
    
- ChromaDB
    
- FAISS
    
- AstraDB
    
- RAG Pipeline
    
- FastAPI
    
- Flask
    
- Streamlit
    
- Docker
    
- Kubernetes
    
- Minikube
    
- Jenkins
    
- GitHub Actions
    
- GitLab CI/CD
    
- CircleCI
    
- ArgoCD
    
- AWS Fargate
    
- AWS ECR
    
- AWS Runner
    
- GCP VM
    
- GKE
    
- GAR
    
- SonarQube
    
- Trivy
    
- Prometheus
    
- Grafana
    
- ELK Stack
    
- Filebeat
    
- Logstash
    
- ElasticSearch
    
- Kibana
    
- Monitoring
    
- Logging
    
- Observability
    
- Infrastructure as Code
    
- CI/CD Automation
    

# 4. 課程主要綱要

## 專案 1：AI Recommendation System

|名詞|類別|中文解釋|主要用途|系統中的角色|
|---|---|---|---|---|
|AI Recommendation System|AI Application|AI 推薦系統|推薦內容、商品、課程|最終產品|
|[LangChain](https://www.langchain.com/?utm_source=chatgpt.com)|AI Framework|LLM 應用框架|建立 AI 工作流|Agent/RAG|
|ChromaDB|Vector Database|向量資料庫|儲存 Embedding|知識庫|
|[Groq](https://groq.com/?utm_source=chatgpt.com)|AI Inference Platform|超高速 LLM 推理平台|執行模型|AI 引擎|
|[Hugging Face](https://huggingface.co/?utm_source=chatgpt.com)|AI Model Hub|AI 模型平台|提供模型與資料集|模型來源|
|Docker|Container|容器化平台|打包應用|部署|
|Kubernetes|Cloud Platform|容器管理平台|大規模部署|基礎設施|
|Google Cloud VM|Cloud Compute|雲端虛擬機|執行系統|主機|

## 專案 2：Production RAG System

|名詞|類別|中文解釋|主要用途|在 RAG 系統中的角色|
|---|---|---|---|---|
|Production RAG System|AI 系統|正式上線的 RAG 平台|企業知識庫查詢|整體產品|
|Astra DB|Vector Database|雲端向量資料庫|儲存 Embeddings|知識庫|
|Memory RAG|RAG Architecture|帶記憶能力的 RAG|保留對話上下文|長期記憶|
|Flask|Backend Framework|Python Web API|提供查詢服務|API 層|
|Prometheus|Monitoring|指標監控系統|收集效能數據|監控|
|Grafana|Dashboard|視覺化監控平台|顯示監控圖表|儀表板|
|Kubernetes|Cloud Platform|容器管理平台|大規模部署|基礎設施|

## 專案 3：|名詞|類別|中文解釋|主要用途|AI 專案中的角色|
|---|---|---|---|---|
|Travel Planner Agent|AI Application|AI 旅遊規劃助理|自動規劃行程|最終產品|
|[LangChain](https://www.langchain.com/?utm_source=chatgpt.com) Agent|Agent Framework|AI Agent 框架|管理工具與推理流程|AI 大腦|
|[Streamlit](https://streamlit.io/?utm_source=chatgpt.com)|Web UI|快速建立網頁介面|使用者操作介面|前端|
|ELK Stack|Monitoring|日誌分析系統|監控與除錯|維運|
|Kubernetes|Cloud Platform|容器管理平台|大規模部署|基礎設施|
    

## 專案 4：Question Generator Platform

|名詞|類別|中文解釋|主要用途|重要度|
|---|---|---|---|---|
|Question Generator Platform|AI Application|AI 自動出題平台|產生考題、測驗、題庫|★★★★★|
|[GitHub](https://github.com/?utm_source=chatgpt.com)|Source Control|原始碼管理平台|存放與協作程式碼|★★★★★|
|Jenkins|CI/CD Tool|自動化建置工具|自動測試與部署|★★★★☆|
|Argo CD|GitOps Tool|Kubernetes 自動部署|持續交付 (CD)|★★★★★|
|CI/CD Pipeline|DevOps Process|持續整合與持續部署流程|自動化開發流程|★★★★★|

## 專案 5：Vision AI Application

|名詞|類別|中文解釋|主要用途|與 AI 的關係|
|---|---|---|---|---|
|**Vision AI Application**|AI 應用|電腦視覺應用程式|讓電腦看懂影像、影片|AI 視覺系統的最終產品|
|**OpenCV**|Computer Vision Library|開源電腦視覺函式庫|影像處理、物件偵測、影像分析|Vision AI 最常用工具之一|
|**Llama 4**|Large Language Model|Meta 最新大型語言模型|對話、推理、多模態 AI|AI Agent、RAG、聊天機器人|
|**CircleCI**|CI/CD 平台|自動化測試與部署工具|自動建置與發佈程式|MLOps、DevOps|
|**GKE Deployment**|Cloud Deployment|Google Kubernetes Engine 部署|將應用程式部署到 Kubernetes|大規模 AI 系統上線|

## 專案 6：Research Agent


|工具|類別|用途|重要度（AI Engineer）|
|---|---|---|---|
|[Tavily](https://tavily.com/?utm_source=chatgpt.com)|AI Search API|AI 專用搜尋引擎|★★★★★|
|FastAPI|Backend API|建立 AI API 服務|★★★★★|
|Jenkins|CI/CD|自動建置部署|★★★☆☆|
|SonarQube|Code Quality|程式碼品質與安全分析|★★★★☆|
|AWS Fargate|Cloud Runtime|執行 Docker 應用|★★★★★|

## 專案 7：PDF RAG Assistant

- HuggingFace
    
- AI RAG 系統  
│
├─ FAISS   Facebook AI Similarity Search 
│   └─ 向量搜尋
│
├─ Jenkins
│   └─ 自動部署   自動化軟體開發流程
│
└─ Trivy
    └─ 安全掃描
    
|項目|Jenkins|CircleCI|
|---|---|---|
|安裝|自架伺服器|雲端服務|
|維護|較麻煩|較簡單|
|學習門檻|高|中|
|新創公司|較少|很多|
- AWS Deployment
    

## 專案 8：AI Streamlit Application

- GitLab CI/CD
    
- GKE
    
- GAR
    
- Production Deployment
    

# 5. Important Keywords

```text
LLMOps, AIOps, MLOps,
LangChain, RAG, ChromaDB,
FAISS, AstraDB,
Vector Database,
FastAPI, Flask, Streamlit,
Docker, DockerHub,
Kubernetes, Minikube,
GKE, AWS Fargate,
AWS ECR, GAR,
Git, GitHub,
GitHub Actions,
GitLab CI/CD,
CircleCI,
Jenkins,
ArgoCD,
Prometheus,
Grafana,
ELK Stack,
Filebeat,
Logstash,
ElasticSearch,
Kibana,
Monitoring,
Observability,
Logging,
Trivy,
SonarQube,
CI/CD,
Cloud Native,
Production AI,
Infrastructure as Code,
Groq,
HuggingFace,
Tavily,
LLM Deployment
```

# 6. 技術能力地圖

## 基礎能力

- LangChain
    
- RAG
    
- Vector Database
    
- FastAPI
    
- Flask
    
- Streamlit
    

## 中階能力

- Docker
    
- Kubernetes
    
- GitHub
    
- Jenkins
    
- AWS
    
- GCP
    

## 高階能力

- CI/CD Pipeline
    
- GitOps
    
- ArgoCD
    
- Production Monitoring
    
- Security Scanning
    

## 專業能力

- Production AI Architecture
    
- Enterprise AI Deployment
    
- LLM Infrastructure Design
    
- Cloud-native AI Systems
    

# 7. 可做的專題

## 專題1：Production RAG Platform

- ChromaDB
    
- FAISS
    
- Kubernetes
    
- Monitoring
    

## 專題2：Enterprise AI Chatbot

- FastAPI
    
- Docker
    
- Jenkins
    
- AWS
    

## 專題3：AI Research Agent

- Tavily
    
- LangChain
    
- Kubernetes
    

## 專題4：LLM Monitoring Platform

- Prometheus
    
- Grafana
    
- ELK
    

## 專題5：AI CI/CD Pipeline

- GitHub Actions
    
- Jenkins
    
- ArgoCD
    

## 專題6：Multi-Agent Deployment Platform

- LangGraph
    
- Kubernetes
    
- GitOps
    

# 8. 對 AI Engineer 的價值

★★★★★

這門課最大的價值：

```text
把 AI Demo 變成 Production System
```

學會：

- 部署 AI 系統
    
- 維護 AI 系統
    
- 擴展 AI 系統
    
- 監控 AI 系統
    

這正是業界 AI Engineer 最缺乏的能力。

# 9. 對 Cybersecurity 的價值

★★★★☆

包含：

- Trivy Security Scan
    
- SonarQube
    
- Container Security
    
- Kubernetes Security
    
- CI/CD Security
    

可作為：

- DevSecOps
    
- AI Security
    

的重要基礎。

# 10. 對 Embedded Systems 的價值

★★☆☆☆

直接相關性較低。

但若未來做：

- Edge AI
    
- Robotics AI Platform
    
- Embedded AI Cloud Backend
    

則非常有幫助。

# 11. 對研究與論文的價值

研究方向：

- LLMOps Framework
    
- AgentOps
    
- Production RAG
    
- AI Observability
    
- LLM Monitoring
    
- AI Reliability Engineering
    
- AI Infrastructure
    

適合研究：

```text
Production Deployment of Agentic AI Systems
```

```text
Monitoring and Reliability of LLM Applications
```

# 12. 學習順序建議

```text
Python
        ↓
LangChain
        ↓
RAG
        ↓
FastAPI
        ↓
Docker
        ↓
Kubernetes
        ↓
Cloud Deployment
        ↓
LLMOps
        ↓
AgentOps
```

# 13. 履歷與學習歷程價值

|項目|評價|
|---|---|
|高中學習歷程|★★★★☆|
|大學申請|★★★★★|
|國外大學申請|★★★★★|
|AI 實習|★★★★★|
|MLOps 實習|★★★★★|
|LLM Engineer|★★★★★|

最大的加分點：

```text
Production AI Deployment
```

這是許多學生完全沒有接觸過的能力。

# 14. 一句話總結

```text
這門課本質上是在學如何把 LLM 與 Agent 系統部署到企業級生產環境。
```

# 15. 最終評價

### 難度

★★★★★

### 實用性

★★★★★

### 含金量

★★★★★

### 作品集價值

★★★★★

### AI 相關性

★★★★★

### 未來發展性

★★★★★

這門課是目前 Udemy 上少數真正聚焦於 LLMOps 與 Production AI 的課程。它不教你如何呼叫 ChatGPT API，而是教你如何建立完整的 AI Infrastructure。對未來想成為 AI Engineer、LLM Engineer、Agent Engineer、MLOps Engineer 的人來說，價值遠高於一般 Prompt Engineering 課程。若你的目標是 AI Agent、RAG、Multi-Agent、企業級 AI 系統開發，這門課屬於高優先級課程。

---


# AI Engineer / LLMOps / MLOps 技術地圖

> 從 RAG、Agent 到企業級 AI 系統部署與維運的完整技術樹

---

# 1. LLMOps 與 Production AI

|技術|中文|功能|
|---|---|---|
|LLMOps Fundamentals|LLM 運維基礎|管理 LLM 的開發、部署、監控|
|Production AI Systems|企業級 AI 系統|正式上線的 AI 平台|
|RAG Pipeline|檢索增強生成流程|文件 → Embedding → 檢索 → LLM|

## 核心觀念

```text
模型管理
Prompt 管理
知識庫管理
API 部署
監控與維運
```

---

# 2. Agent / RAG Framework

|技術|類型|功能|
|---|---|---|
|LangChain|LLM Framework|建立 Agent、RAG、Workflow|
|RAG Pipeline|Retrieval System|文件檢索與生成|

## 架構

```text
Question
    ↓
Retriever
    ↓
Vector DB
    ↓
LLM
    ↓
Answer
```

---

# 3. Vector Database

|技術|類型|功能|
|---|---|---|
|ChromaDB|Vector DB|本地 RAG|
|FAISS|Similarity Search|高速向量搜尋|
|AstraDB|Cloud Vector DB|Production RAG|

## 學習順序

```text
ChromaDB
    ↓
FAISS
    ↓
AstraDB
```

---

# 4. API Service Layer

|技術|功能|
|---|---|
|FastAPI|高效能 Python API|
|Flask|輕量級 Web API|
|Streamlit|AI Demo UI|

## 建議

```text
FastAPI ★★★★★
Streamlit ★★★★★
Flask    ★★★☆☆
```

---

# 5. Container Technology

|技術|功能|
|---|---|
|Docker|容器化應用|
|Kubernetes|容器編排平台|
|Minikube|本地 Kubernetes|

## 架構

```text
Application
    ↓
Docker
    ↓
Kubernetes
```

---

# 6. CI/CD 工具

|技術|功能|
|---|---|
|Jenkins|傳統企業 CI/CD|
|GitHub Actions|GitHub CI/CD|
|GitLab CI/CD|GitLab CI/CD|
|CircleCI|雲端 CI/CD|
|ArgoCD|GitOps Deployment|

## 現代流程

```text
GitHub
    ↓
GitHub Actions
    ↓
Docker Build
    ↓
ArgoCD
    ↓
Kubernetes
```

---

# 7. AWS 雲端部署

|技術|功能|
|---|---|
|AWS ECR|Docker Registry|
|AWS Fargate|Serverless Container|
|AWS Runner|CI/CD Runner|

## 架構

```text
GitHub
    ↓
CI/CD
    ↓
ECR
    ↓
Fargate
    ↓
Production
```

---

# 8. Google Cloud Platform

|技術|功能|
|---|---|
|GCP VM|虛擬機|
|GKE|Kubernetes Service|
|GAR|Artifact Registry|

## 架構

```text
Docker
    ↓
GAR
    ↓
GKE
    ↓
Production
```

---

# 9. DevSecOps

|技術|功能|
|---|---|
|SonarQube|程式碼品質分析|
|Trivy|Docker 漏洞掃描|

## 流程

```text
Git Push
    ↓
SonarQube
    ↓
Trivy
    ↓
Deploy
```

---

# 10. Monitoring / Logging / Observability

## Monitoring

監控系統健康狀態

例如：

```text
CPU
RAM
GPU
Network
Latency
```

---

## Logging

記錄系統事件

例如：

```text
Application Logs
API Logs
Error Logs
Audit Logs
```

---

## Observability

可觀測性

包含：

```text
Metrics
Logs
Traces
```

---

# 11. Prometheus + Grafana

|技術|功能|
|---|---|
|Prometheus|Metrics Collector|
|Grafana|Dashboard Visualization|

## 架構

```text
CPU
RAM
GPU
Latency
    ↓
Prometheus
    ↓
Grafana
```

---

# 12. ELK Stack

|技術|功能|
|---|---|
|Filebeat|收集日誌|
|Logstash|處理日誌|
|Elasticsearch|儲存日誌|
|Kibana|視覺化查詢|
|ELK Stack|完整日誌平台|

## 架構

```text
Application Log
        ↓
Filebeat
        ↓
Logstash
        ↓
Elasticsearch
        ↓
Kibana
```

---

# 13. Infrastructure as Code (IaC)

## 定義

以程式碼管理基礎設施

## 常見工具

```text
Terraform
Pulumi
CloudFormation
```

## 流程

```text
Code
    ↓
Infrastructure
    ↓
Cloud Resources
```

---

# 14. CI/CD Automation

## CI

Continuous Integration

持續整合

---

## CD

Continuous Deployment

持續部署

---

## 流程

```text
Git Push
    ↓
Test
    ↓
Build
    ↓
Security Scan
    ↓
Deploy
    ↓
Monitor
```

---

# AI Engineer 學習路線圖

## 第一階段（核心）

```text
LangChain
RAG Pipeline
ChromaDB
FAISS
FastAPI
Streamlit
Docker
GitHub Actions
```

---

## 第二階段（進階）

```text
Kubernetes
Minikube
Prometheus
Grafana
SonarQube
Trivy
```

---

## 第三階段（企業級）

```text
AstraDB
ArgoCD
GKE
AWS Fargate
ELK Stack
Infrastructure as Code
```

---

# Top 10 最重要技術

```text
1. LangChain
2. RAG Pipeline
3. ChromaDB
4. FAISS
5. FastAPI
6. Docker
7. GitHub Actions
8. Kubernetes
9. Prometheus
10. Grafana
```

---

# 最終 Production AI 架構

```text
User
  ↓
FastAPI
  ↓
LangChain Agent
  ↓
RAG Pipeline
  ↓
Vector Database
(ChromaDB / FAISS / AstraDB)
  ↓
LLM
  ↓
Answer

─────────────────

Docker
  ↓
Kubernetes
  ↓
ArgoCD
  ↓
Cloud (AWS/GCP)

─────────────────

Prometheus
  ↓
Grafana

ELK Stack
  ↓
Observability
```