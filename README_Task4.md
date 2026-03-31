# 🏥 AI/ML Engineering Internship — Task 4: HealthBot (AI Health Assistant)

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![LLM](https://img.shields.io/badge/LLM-Llama--3.1--8B-green?logo=meta)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Router%20API-yellow?logo=huggingface)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Task Objective

The goal of this task is to build **HealthBot** — an AI-powered conversational health assistant that:
- Answers general health questions in simple, friendly language
- Detects **medical emergencies** and redirects to emergency services
- Detects **mental health crises** and provides helpline information
- Blocks **harmful requests** automatically
- Maintains **conversation memory** across multiple turns

> ⚠️ *HealthBot is an educational assistant only — NOT a replacement for a real doctor.*

---

## 📊 Dataset Used

| Property        | Details                                              |
|-----------------|------------------------------------------------------|
| **Type**        | No static dataset — uses LLM API for responses      |
| **Model**       | `meta-llama/Llama-3.1-8B-Instruct:cerebras`         |
| **API**         | HuggingFace Router API (`https://router.huggingface.co/v1`) |
| **Alternative Models** | `Qwen/Qwen2.5-7B-Instruct:novita`, `google/gemma-2-2b-it:novita` |
| **Input**       | User health questions (text)                         |
| **Output**      | Educational health information (text)                |

---

## 🧠 Models / Components Applied

### 1. 🤖 LLM — Llama 3.1 8B Instruct
- Hosted on HuggingFace Router (Cerebras inference provider)
- OpenAI-compatible API interface
- `max_tokens: 500`, `temperature: 0.7`
- System prompt enforces safe, educational responses

### 2. 🛡️ Safety Filter System (Rule-Based)
Three layers of safety checks before any LLM call:

| Filter Type | Keywords Detected | Response |
|-------------|-------------------|----------|
| 🚨 Emergency | chest pain, stroke, overdose, seizure... | Call 1122 / 911 immediately |
| 💙 Mental Health Crisis | suicide, self harm, want to die... | Crisis helpline info |
| ⚠️ Harmful Request | illegal drugs, how to make poison... | Request blocked |

### 3. 💬 Conversation Memory
- Stores last **10 exchanges** (20 messages) in history
- Maintains context across multi-turn conversations
- Reset feature to start fresh

---

## 🧪 Test Queries & Results

| # | Query | Filter Triggered |
|---|-------|-----------------|
| 1 | *"What causes a sore throat?"* | ✅ SAFE → LLM responded |
| 2 | *"Is paracetamol safe for children?"* | ✅ SAFE → LLM responded |
| 3 | *"What are symptoms of diabetes?"* | ✅ SAFE → LLM responded |
| 4 | *"I have severe chest pain and can't breathe!"* | 🚨 EMERGENCY → Direct redirect |

---

## 📈 Key Results and Findings

- ✅ **Safety filters work perfectly** — emergency queries never reach the LLM
- ✅ **Llama 3.1 8B** gives clear, concise health information in 3–5 sentences
- ✅ **Multi-turn memory** maintains conversation context effectively
- ✅ **Pakistan-specific emergency numbers** (1122, 115) included in responses
- ⚡ **Cerebras provider** offers fast inference for Llama models (free tier)
- 🔄 Conversation history auto-truncates at 20 messages to avoid token overflow

---

## 🗂️ Project Structure

```
📦 AI-ML-Internship-Task-4-HealthBot/
├── 📓 AI_ML_Engineering_Internship_Tasks_4.ipynb   ← Main notebook
├── 📁 Visualization_Images/                         ← Architecture & flow diagrams
└── 📄 README.md                                     ← This file
```

---

## ⚙️ How to Run

### Prerequisites
```bash
pip install openai huggingface_hub
```

### Setup
1. Get a **free HuggingFace token** from: https://huggingface.co/settings/tokens
2. Enable **"Make calls to Inference Providers"** permission
3. Paste your token in `HF_API_TOKEN` variable

### Run
```bash
jupyter notebook AI_ML_Engineering_Internship_Tasks_4.ipynb
```
Run all cells — interactive chat starts at **Step 8**

### Chat Commands
| Command | Action |
|---------|--------|
| Any health question | Get educational answer |
| `history` | View conversation history |
| `reset` | Clear chat memory |
| `quit` / `exit` | End session |

---

## 🛠️ Technologies Used

- **Python 3.8+**
- **Jupyter Notebook**
- `openai` — OpenAI-compatible API client
- `huggingface_hub` — HuggingFace integration
- **Llama 3.1 8B Instruct** — Meta's open-source LLM
- **HuggingFace Router API** — Free LLM inference

---

## ⚠️ Disclaimer

HealthBot is for **educational purposes only**.  
Always consult a qualified doctor for personal medical advice.  
In emergencies: 🇵🇰 **1122 | 115** | 🌍 **112** | 🇺🇸 **911**


*This project was completed as part of an AI/ML Engineering Internship program.*
