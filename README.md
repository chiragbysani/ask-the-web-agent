# Ask the Web Agent AI-Powered Web Search Agent.

An autonomous AI agent that answers real-time questions by searching the web live using DuckDuckGo — powered by Gemma 3 12B running locally via Ollama. No external API keys required.

# What It Does:

-Searches the web in real-time to answer questions beyond the model's training data.

-Uses a ReAct reasoning loop (Thought → Action → Observation) to chain multiple searches and synthesize a final answer.

-Runs entirely on-device — no OpenAI or paid API needed.

-Handles multi-step queries like comparing live data across two locations.

# Tech Stack:

-LLM:Gemma 3 12B (via Ollama).

-Web Search: DuckDuckGo Search (DDGS).

-Agent Framework: LangChain (ZERO_SHOT_REACT_DESCRIPTION).

-API Layer:FastAPI + Uvicorn.

-Runtime:Google Colab (T4 GPU).

#Sample Output:

Input: "Is Tiptur warmer today or Bangalore?"

Thought: I need to compare temperatures in Tiptur and Bangalore.
Action: search_web
Action Input: "current temperature in Tiptur"
Observation: Tiptur, Karnataka — 31°C (feels like 34°C)

Action: search_web
Action Input: "current temperature in Bangalore"
Observation: Bengaluru, Karnataka — 27°C (feels like 30°C)

Thought: Tiptur is warmer than Bangalore.
Final Answer: Tiptur

#How to Run:

# 1. Install dependencies

!apt-get install -y zstd

!curl -fsSL https://ollama.com/install.sh | sh

!pip install -q langchain==0.3.26 langchain-community==0.3.27 langchain-openai==0.3.27

!pip install -q openai==1.86.0 fastapi==0.116.1 uvicorn==0.35.0 ddgs==9.4.0 ollama

# 2. Start Ollama server

import subprocess, time

subprocess.Popen(["ollama", "serve"])

time.sleep(5)

# 3. Pull model

!ollama pull gemma3:12b

# 4. Run the notebook
Open ask_the_web_agent.ipynb in Google Colab and run all cells.


#Author:
Chirag A Bysani

GitHub: chiragbysani
Email: chiragbysani98@gmail.com


