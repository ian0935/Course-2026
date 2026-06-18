# 目錄

- [[#1. 課程總覽比較表|1. 課程總覽比較表]]
- [[#2. 課程定位|2. 課程定位]]
    - [[#2.1 課程特色|2.1 課程特色]]
    - [[#2.2 適合對象|2.2 適合對象]]
    - [[#2.3 課程難度判斷|2.3 課程難度判斷]]
- [[#3. 上課重點|3. 上課重點]]
- [[#4. 課程主要綱要|4. 課程主要綱要]]
    - [[#4.1 課程導論與 Voice Agent 基礎|4.1 課程導論與 Voice Agent 基礎]]
    - [[#4.2 Vapi Voice Agent 實作|4.2 Vapi Voice Agent 實作]]
    - [[#4.3 n8n + MCP + Vapi Automation|4.3 n8n + MCP + Vapi Automation]]
    - [[#4.4 Production-ready Restaurant Reservation Agent|4.4 Production-ready Restaurant Reservation Agent]]
    - [[#4.5 ElevenLabs Voice Agents|4.5 ElevenLabs Voice Agents]]
    - [[#4.6 Python、Cursor、LiveKit 與 OpenAI Realtime API|4.6 Python、Cursor、LiveKit 與 OpenAI Realtime API]]
    - [[#4.7 AI Automation Agency 商業化|4.7 AI Automation Agency 商業化]]
    - [[#4.8 Security、Data Protection 與 Legal Frameworks|4.8 Security、Data Protection 與 Legal Frameworks]]
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

# AI Voice Agents 課程分析整理

# 1. 課程總覽比較表

| 項目 | 內容 |
|---|---|
| 課程名稱 | AI Voice Agents |
| 領域 | Conversational AI、Voice Agent、LLM Application、AI Automation |
| 難度 | ★★★★☆ |
| 核心定位 | 建立可商業化的 AI 語音代理系統 |
| 適合對象 | AI Engineer、LLM Engineer、Agent Engineer、AI Automation Engineer |
| 先備知識 | 課程宣稱不需基礎，但有 Python、API、JSON、LLM、RAG、n8n 會更好 |
| 課程長度 | 12 小時 29 分鐘 |
| 章節數 | 9 個章節 |
| 講座數 | 84 堂 |
| 實務價值 | ★★★★★ |
| 作品集價值 | ★★★★★ |
| 推薦程度 | ★★★★★ |

這門課是一門偏實作與產品化的 **AI Voice Agent 課程**。它不是單純介紹 Chatbot，而是把 LLM、STT、TTS、RAG、MCP、n8n、ElevenLabs、Vapi、LiveKit、OpenAI Realtime API、Twilio、Webhook、電話系統與商業自動化串起來，做成真正可以接電話、預約、查資料、寄信與連接資料庫的 AI 語音代理。

# 2. 課程定位

## 2.1 課程特色

這門課位於以下幾個領域的交會點：

```text
LLM Application
        ↓
AI Agent
        ↓
Voice Agent
        ↓
AI Automation
        ↓
Business Deployment
```

它的核心特色是：

- 不是只學 Chatbot，而是學會 Voice Agent
- 不是只學 Prompt，而是學完整系統整合
- 不是只學單一平台，而是比較 Vapi、ElevenLabs、LiveKit、Retell、Synthflow 等工具
- 不是只學 Demo，而是包含電話號碼、RAG、MCP、Webhook、n8n、資料庫與商業部署
- 不是只學開發，也包含資安、GDPR、EU AI Act、Prompt Injection、MCP Security

## 2.2 適合對象

適合：

- 想做 AI Engineer 的學生
- 想做 LLM Application 的學生
- 想做 AI Agent 的開發者
- 想做 AI Automation Agency 的人
- 想把 AI 應用到客服、訂位、銷售、行政流程的人
- 想研究 AI Agent Security 的學生
- 想做語音互動、AI Avatar、Realtime AI 的開發者

## 2.3 課程難度判斷

雖然課程標示「No prior knowledge required」，但如果要真正吸收後半段內容，最好具備：

- 基本 LLM 概念
- Prompt Engineering 概念
- API / Webhook 概念
- JSON 基礎
- Python 基礎
- n8n 或自動化工具基礎
- RAG / Vector Database 基礎
- 基本資安意識

所以它實際比較像是：

```text
入門可跟上
中階能吸收
進階能做作品
```

# 3. 上課重點

- Voice Agent 基本原理
- Voice Agent 的目標、優勢與弱點
- Voice Agent 的商業潛力
- LLM、STT、TTS 架構
- 如何選擇適合 Voice Agent 的模型
- Vapi 平台使用
- ElevenLabs 專業語音生成
- Retell、Synthflow、LiveKit 等平台比較
- OpenAI Realtime API
- System Prompt 設計
- Voice Agent Prompt Engineering
- 網站嵌入與 CSS 客製化
- Voice Agent Testing
- Voice Agent Debugging
- Voice Agent Optimization
- n8n Workflow
- API Keys
- Webhook
- MCP Tools
- RAG Voice Agent
- Vector Database
- Pinecone
- Google Sheets 整合
- SQL Database 整合
- Email Automation
- Inbound Call
- Outbound Call
- Twilio Phone Number
- Restaurant Reservation Agent
- Sentiment Analysis
- Human-in-the-Loop
- Transfers and Escalations
- AI Avatar
- Python + LiveKit
- Cursor
- pyenv、pip、uv Package Manager
- Fine-tuning LLM 是否值得
- Local AI Solutions
- Open-source Alternatives
- GDPR
- EU AI Act
- Prompt Injection
- Jailbreak
- Data Poisoning
- Tool Poisoning
- MCP Rug Pull
- API Key Security
- Compliance

# 4. 課程主要綱要

## 4.1 課程導論與 Voice Agent 基礎

- Welcome
- Course Overview
- Explanation of Course Links
- Instructor Introduction
- Tips and Goals for the Course
- The Goal of Voice Agents
- Strengths and Weaknesses Overview
- Understanding Voice Agents
- LLM、TTS、STT 技術架構
- 適合 Voice Agent 的模型選擇
- Voice Agent 平台比較
- 經濟可行性與成本效益分析
- Voice AI Agents Mini Quiz

## 4.2 Vapi Voice Agent 實作

- Vapi Sign-Up and Overview
- Build a Simple Voice Agent in Vapi
- LLMs、STT、TTS 設定
- System Prompt 設計
- RAG Database
- AI Appointment Booking Assistant
- ElevenLabs Voice 整合
- Prompt Engineering
- Dynamic JavaScript Variables
- 網站嵌入
- CSS Customization
- Filler Words 橋接等待時間
- Testing
- Debugging
- Improving Conversation Quality
- OpenRouter 模型選擇
- Context Loss 修正

## 4.3 n8n + MCP + Vapi Automation

- n8n Crash Course
- Sign-Up
- Triggers
- API Keys
- Workflows
- JSON
- n8n Workflow Builder with AI
- Connecting n8n with Vapi via MCP
- Adding Tools
- Email Workflows
- Google Sheets 查詢
- SQL Database 查詢
- Training a RAG App
- Uploading Data to a Vector Database
- Pinecone Vector Database
- Connecting MCP Server with Claude Desktop or Cursor
- Sending Confirmation Emails
- Adding Phone Numbers for Inbound Calls
- Adding Twilio Phone Numbers for Outbound Calls

## 4.4 Production-ready Restaurant Reservation Agent

- Which Voice Agents Should You Build
- How Much Are They Worth
- First Layouts
- AI-Powered Voice Agent for Restaurant Reservations
- System Prompt
- RAG
- MCP Tool Integrations for Booking Tables
- Store Information Intelligently in a Database
- Debugging
- Prompt Engineering Tips
- Transfers
- Escalations
- Human-in-the-Loop
- Sentiment Analysis
- Custom Functions
- Squads
- End Call Tool
- Sending Texts

## 4.5 ElevenLabs Voice Agents

- ElevenLabs Creative Platform
- Voice Agents
- Documentation
- Prompt Engineering Masterclass
- AI Phone Agents
- Website Implementation
- Webhooks for Tools
- Connecting ElevenLabs and n8n
- Additional Tools via Webhooks
- n8n Agents with ElevenLabs
- Templates
- Agent Workflows
- Testing and Debugging
- MCP
- Phone Numbers
- Outbound Calls

## 4.6 Python、Cursor、LiveKit 與 OpenAI Realtime API

- Section Overview
- Python 安裝
- pyenv
- pip
- uv Package Manager
- Cursor Crash Course
- Vibe Coding
- LiveKit Overview
- Python AI Avatar
- Voice Interaction
- OpenAI Realtime API
- Change Voices
- Restart App
- Different Prompts
- Publish Python Project on GitHub
- More Options with LiveKit and Python
- Fine-Tuning Your Own LLM
- Fine-Tuning 是否值得

## 4.7 AI Automation Agency 商業化

- Business Fundamentals for AI Voice Agents
- AI Automation Agency
- Your First Client
- Pricing Strategy for Voice Agents
- Self-Hosting n8n
- Voice AI Automation Agency Business
- Business Recap

## 4.8 Security、Data Protection 與 Legal Frameworks

- Misbehaving MCP Server
- Tool Poisoning
- MCP Rug Pulls
- Security Vulnerabilities
- Jailbreaks
- Prompt Injections
- Data Poisoning
- Authentication
- API Keys
- Copyright
- Data Privacy
- Censorship
- License
- Compliance
- GDPR
- EU AI Act

# 5. Important Keywords

```text
Voice Agent, AI Voice Agent, Conversational AI, LLM, Large Language Model,
STT, Speech-to-Text, TTS, Text-to-Speech, Vapi, ElevenLabs, Retell, Synthflow,
LiveKit, OpenAI Realtime API, n8n, MCP, Model Context Protocol, Webhook,
API Key, RAG, Retrieval-Augmented Generation, Vector Database, Pinecone,
Prompt Engineering, System Prompt, Tool Calling, Function Calling,
Google Sheets API, SQL Database, Email Automation, Twilio, SIP Integration,
Inbound Call, Outbound Call, Phone Agent, AI Appointment Booking,
Restaurant Reservation Agent, Sentiment Analysis, Human-in-the-Loop,
Escalation, Transfer, Custom Function, Squad, End Call Tool, SMS Automation,
AI Avatar, Cursor, Python, pyenv, pip, uv, Fine-Tuning, Local AI,
Open-source LLM, OpenRouter, DeepSeek, Llama, Mistral, Claude Desktop,
GDPR, EU AI Act, Prompt Injection, Jailbreak, Data Poisoning, Tool Poisoning,
MCP Rug Pull, MCP Security, Authentication, API Key Security, Compliance,
AI Automation Agency, Realtime AI, Voice Interface, Customer Support Agent
```

# 6. 技術能力地圖

## 6.1 基礎能力

- 理解 Voice Agent 是什麼
- 理解 Voice Agent 的優勢與限制
- 理解 LLM、STT、TTS 的角色
- 理解 Voice Agent 平台差異
- 理解語音 AI 的商業場景

## 6.2 中階能力

- 建立 Vapi Voice Agent
- 建立 ElevenLabs Voice Agent
- 設計 System Prompt
- 設計 Voice Agent 對話流程
- 使用 OpenRouter 選擇 LLM
- 將 Voice Agent 嵌入網站
- 使用 CSS 客製化介面
- Debug Voice Agent
- 改善對話品質

## 6.3 高階能力

- 建立 RAG Voice Agent
- 上傳資料到 Vector Database
- 串接 Pinecone
- 使用 n8n 建立 Workflow
- 使用 MCP 擴充 Voice Agent 工具
- 串接 Google Sheets
- 串接 SQL Database
- 串接 Email Automation
- 串接 Inbound / Outbound Call
- 使用 Twilio 電話號碼

## 6.4 專業能力

- 建立 Production-ready Voice Agent
- 建立 Restaurant Reservation Agent
- 建立 Human-in-the-Loop 流程
- 加入 Sentiment Analysis
- 使用 Python + LiveKit + OpenAI Realtime API
- 建立即時 AI Avatar
- 評估 Fine-Tuning 是否值得
- Self-hosting n8n
- AI Automation Agency 商業化
- 設計 Voice Agent Security Testing
- 處理 GDPR、EU AI Act、Compliance

# 7. 可做的專題

## 7.1 AI 餐廳訂位語音助理

建立一個可以接電話、詢問人數、日期、時間、特殊需求，並把訂位資料寫入資料庫的 Voice Agent。

可包含：

- Vapi
- System Prompt
- RAG
- MCP Tool
- Database
- n8n
- Sentiment Analysis
- Human Escalation

作品集價值：★★★★★

## 7.2 AI 客服電話助理

建立一個可以回答公司常見問題、查詢文件、轉接人工客服的語音客服系統。

可包含：

- RAG
- Vector Database
- STT
- TTS
- Webhook
- Tool Calling
- Human-in-the-Loop

作品集價值：★★★★★

## 7.3 RAG Voice Agent 知識庫查詢系統

讓語音代理可以查詢公司文件、課程資料、產品資訊、SOP 或 FAQ。

可包含：

- Pinecone
- RAG
- Embedding
- n8n
- Vapi
- MCP
- Query Routing

作品集價值：★★★★★

## 7.4 Python + LiveKit AI Avatar

使用 Python、LiveKit、OpenAI Realtime API 建立即時語音互動 AI Avatar。

可包含：

- Python
- LiveKit
- OpenAI Realtime API
- Cursor
- Voice Streaming
- Realtime Conversation

作品集價值：★★★★★

## 7.5 Voice Agent Security Testing Lab

建立一個專門測試 Voice Agent 安全性的實驗環境。

測試項目：

- Prompt Injection
- Jailbreak
- Tool Poisoning
- MCP Rug Pull
- Data Poisoning
- API Key Leakage
- Authentication Weakness

作品集價值：★★★★★

## 7.6 AI Automation Agency Demo System

建立一套可展示給客戶看的 Voice AI Agency Demo。

可包含：

- 客服 Agent
- 訂位 Agent
- Google Sheets 查詢
- Email Confirmation
- Outbound Call
- Pricing Page
- Demo Website

作品集價值：★★★★☆

# 8. 對 AI Engineer 的價值

這門課非常適合 AI Engineer，因為它訓練的是「把 LLM 做成產品」的能力。

可學到：

- LLM 應用開發
- Prompt Engineering
- RAG
- Tool Calling
- MCP
- Webhook
- Realtime AI
- Voice Interaction
- Workflow Automation
- Production Deployment

它不是只會呼叫 ChatGPT API，而是能把模型接到：

- 電話
- 網站
- 資料庫
- Email
- Google Sheets
- 自動化流程
- Human Escalation

這是目前 AI Engineer 很實用的能力。

# 9. 對 Cybersecurity 的價值

這門課對 AI Security 很有價值。

可延伸主題：

- Prompt Injection
- Jailbreak
- Data Poisoning
- MCP Tool Poisoning
- MCP Rug Pull
- API Key Protection
- Authentication
- GDPR
- EU AI Act
- Voice Agent Compliance

尤其「Voice Agent + MCP」很適合作為 AI Agent Security 的研究題目。

可以做成：

```text
Voice Agent Security Testing Lab
```

或：

```text
Security Evaluation Framework for MCP-based Voice Agents
```

這會比一般只做 Chatbot 更有研究特色。

# 10. 對 Embedded Systems 的價值

這門課不是傳統 Embedded Systems 課程，但可以延伸到 IoT、Robotics、Edge AI。

可延伸方向：

- Voice-controlled IoT Device
- Voice-controlled Robot
- Edge AI Assistant
- Local Voice Agent
- AI + Raspberry Pi
- AI + ESP32 Gateway
- AI + STM32 Gateway
- Voice Interface for Embedded Devices

如果結合 Embedded Systems，可以設計：

```text
Voice Agent Controlled Robot Assistant
```

或：

```text
Voice Agent for Smart Home IoT Gateway
```

這會讓作品集同時具有 AI、語音互動、IoT、Embedded 的特色。

# 11. 對研究與論文的價值

可延伸研究方向：

```text
1. Security Evaluation of MCP-based Voice Agents
2. Prompt Injection Attacks on Voice AI Agents
3. Tool Poisoning Detection in Voice Agent Systems
4. RAG-enhanced Voice Agents for Customer Service
5. Human-in-the-Loop Voice Agent Design
6. Real-time LLM Latency Optimization
7. Voice Agent Compliance under GDPR and EU AI Act
8. Local Voice Agent with Open-source LLMs
9. Multimodal AI Avatar with Realtime Voice Interaction
10. Voice Agent Benchmark for Business Automation
```

適合的論文題目：

```text
A Security Evaluation Framework for MCP-based Voice AI Agents
```

```text
Prompt Injection and Tool Poisoning Attacks in Voice AI Agent Systems
```

```text
RAG-enhanced Voice Agents for Real-time Customer Service Automation
```

```text
Designing Human-in-the-Loop Voice Agents for Business Process Automation
```

# 12. 學習順序建議

## 12.1 AI Engineer 路線

```text
LLM Fundamentals
        ↓
Prompt Engineering
        ↓
RAG
        ↓
Tool Calling
        ↓
MCP
        ↓
Voice Agent
        ↓
Realtime API
        ↓
Production Deployment
```

## 12.2 Cybersecurity 路線

```text
Web Security
        ↓
API Security
        ↓
LLM Security
        ↓
Prompt Injection
        ↓
MCP Security
        ↓
Voice Agent Security Testing
        ↓
Compliance
```

## 12.3 Embedded / Robotics 路線

```text
Embedded Systems
        ↓
IoT Communication
        ↓
API / MQTT / HTTP
        ↓
Voice Agent
        ↓
Voice-controlled Device
        ↓
Edge AI Assistant
```

## 12.4 AI Automation Agency 路線

```text
n8n
        ↓
Vapi / ElevenLabs
        ↓
Webhook
        ↓
Google Sheets / SQL Database
        ↓
Phone Number Integration
        ↓
Client Demo
        ↓
Pricing Strategy
        ↓
Self-hosted n8n
```

# 13. 履歷與學習歷程價值

| 使用場景 | 加分程度 | 理由 |
|---|---|---|
| 高中學習歷程 | ★★★★★ | 題材新，結合 AI、語音、Agent、自動化 |
| 大學申請 | ★★★★★ | 展現超出一般學生的 AI 系統整合能力 |
| 國外大學申請 | ★★★★★ | Voice Agent、RAG、MCP、Realtime API 都是新方向 |
| 實習申請 | ★★★★★ | 非常接近企業 AI Automation / LLM Application 需求 |
| 研究題目 | ★★★★☆ | 可延伸 AI Security / Agent Security |
| 創業作品 | ★★★★★ | 可直接發展 AI Automation Agency |
| 資安作品集 | ★★★★★ | 可做 Voice Agent Security Testing Lab |
| Embedded / Robotics 作品集 | ★★★★☆ | 可延伸語音控制 IoT / Robot |

這門課如果只是看完，價值中等；但如果能做出實際作品，例如「AI 餐廳訂位語音助理」、「AI 客服電話助理」、「Voice Agent Security Testing Lab」，就會非常有說服力。

# 14. 一句話總結

```text
這門課本質上是在學如何把 LLM、語音、RAG、MCP、自動化流程與電話系統整合成可商業化的 AI Voice Agent。
```

# 15. 最終評價

| 評估項目 | 評分 |
|---|---|
| 難度 | ★★★★☆ |
| 實用性 | ★★★★★ |
| 含金量 | ★★★★★ |
| 作品集價值 | ★★★★★ |
| AI 相關性 | ★★★★★ |
| 未來發展性 | ★★★★★ |

這門課非常值得學。它的價值不只是「會做語音機器人」，而是能完整理解 AI Voice Agent 的產品化流程：從 LLM、STT、TTS、Prompt、RAG、MCP、n8n、Webhook、資料庫、電話系統，到商業部署與安全合規。

對江赫霆來說，最值得做成作品集的是：

```text
1. AI Restaurant Reservation Voice Agent
2. AI Customer Support Phone Agent
3. RAG Voice Agent Knowledge Base
4. Python + LiveKit AI Avatar
5. Voice Agent Security Testing Lab
```

如果能把其中一個做成完整 Demo，加上 GitHub、架構圖、技術報告、Prompt 設計、RAG 架構、資安測試，會非常適合放進學習歷程、AI Engineer 作品集、國外大學申請與未來研究題目。
