# 🧠 Self-Hosted AI Assistant with Custom Model (Elion)

## 📖 Overview

This project demonstrates the deployment of a fully self-hosted Large Language Model (LLM) environment using **Ollama** and **Open WebUI** on Linux.

The system includes:

- Local LLM deployment
- Custom model creation using Ollama Modelfile
- API configuration and testing
- WebUI integration
- Troubleshooting of port and service conflicts
- Fully offline AI interaction without cloud APIs

The custom model **Elion** was built on top of a base model and configured with specialized system behavior and generation parameters.

---

## 🎯 Project Objectives

- Deploy Ollama on Linux
- Run and manage local LLM models
- Create a custom AI model (Elion)
- Integrate Ollama API with Open WebUI
- Debug and resolve API connection issues
- Successfully interact with a self-hosted AI assistant

---

## 🛠 Technologies Used

- Linux (Ubuntu)
- Ollama
- Open WebUI
- REST API
- Curl
- Git & GitHub

---

# ⚙️ Installation & Setup

## 1️⃣ Install Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Verify installation:

```bash
ollama --version
```

---

## 2️⃣ Start Ollama Server

```bash
ollama serve
```

Server runs on:

```
http://127.0.0.1:11434
```

---

## 3️⃣ Pull Base Model

```bash
ollama pull qwen2.5:3b-instruct-q4_K_M
```

---

# 🧠 Custom Model Creation – Elion

## 📌 Step 1: Create Modelfile

```bash
nano Modelfile
```

Example Modelfile:

```
FROM qwen2.5:3b-instruct-q4_K_M

SYSTEM You are Elion, a professional AI assistant specialized in cybersecurity, Linux troubleshooting, and system diagnostics.

PARAMETER temperature 0.7
PARAMETER num_ctx 4096
PARAMETER top_p 0.9
```

---

## 📌 Step 2: Build Custom Model

```bash
ollama create elion -f Modelfile
```

---

## 📌 Step 3: Verify Model Creation

```bash
ollama list
```

Expected output:

```
elion:latest
qwen2.5:3b-instruct-q4_K_M
```

---

## 📌 Step 4: Test via API

```bash
curl http://127.0.0.1:11434/api/generate -d '{
  "model": "elion",
  "prompt": "Explain Linux port conflicts",
  "stream": false
}'
```

---

# 🌐 Open WebUI Integration

1. Launch Open WebUI
2. Navigate to:  
   **Admin Panel → Settings → Connections**
3. Add Ollama connection:

```
http://127.0.0.1:11434
```

4. Save and refresh
5. Select `elion:latest` from model dropdown

---

# 🔍 Troubleshooting

### Issue: Port 11434 already in use

```bash
sudo lsof -i :11434
sudo killall ollama
```

---

### Issue: "Failed to fetch models"

- Use `http://127.0.0.1:11434` instead of `localhost`
- Ensure `ollama serve` is running
- Disable "Cache Base Model List" in WebUI settings

---

### Issue: Server connection error

- Confirm Ollama is listening:

```bash
curl http://127.0.0.1:11434/api/version
```

---

# 📷 Screenshots

Add these images inside `/images` folder:

```markdown
![Ollama Server Running](images/ollama-server.png)
![Elion Modelfile](images/modelfile.png)
![Model Creation Process](images/elion-creation.png)
![WebUI Connection Setup](images/webui-connection.png)
![Successful AI Chat](images/chat-response.png)
```

Recommended screenshots:
- Terminal showing `ollama serve`
- Modelfile content
- `ollama create elion`
- WebUI connection configuration
- Chat interaction with Elion

---

# 🚀 Results

Successfully deployed and configured a self-hosted AI assistant with:

- Custom model behavior
- Local API communication
- Web interface integration
- Fully offline operation
- Resolved real-world service and networking issues

---

# 📌 GitHub Topics (Add These)

```
ollama
openwebui
llm
self-hosted-ai
linux
local-llm
ai-deployment
api-integration
machine-learning
prompt-engineering
```

---

# 💼 Resume Contribution

Designed and deployed a self-hosted AI assistant using Ollama and Open WebUI on Linux, including custom LLM creation via Modelfile, API integration, and system-level troubleshooting.

---

# 📜 License

MIT License

---

## 👨‍💻 Author

Andrew Moses
