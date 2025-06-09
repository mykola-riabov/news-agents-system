# 🧠 News Agents System (NAS)

**News Agents System (NAS)** is a modular multi-agent framework built on top of `uAgents`, designed to autonomously collect, process, analyze, and publish crypto-related news and forecasts into a Telegram channel.

---

## 📌 About the Project

This system was designed for Telegram-based crypto and tech news channels. It is fully autonomous, extensible, and stylistically flexible — publications are made in the voices of characters from **Futurama**:

- **Bender** posts news and jokes.
- **Fry** delivers crypto forecasts.

---

## 🧩 Architecture & Agents

Each agent is an independent service that communicates with others via the `uAgents` protocol. It handles addressing (DID), secure messaging, and pub/sub signaling.

`uAgents` is an open-source agent framework developed by the **Fetch.ai** team. It allows building secure and distributed Python-based systems with clean and readable logic.

---

## 🤖 Core Agents

### 📡 `CollectorAgent`  
A template-based agent, configurable via `settings.json`, capable of spawning multiple news collectors (RSS, API, or HTML parsing). Does **not** use LLM.

### 🧹 `FilterAgent`  
Performs deduplication, keyword scoring, and tag analysis. Does **not** use LLM.

### 🧠 `SummarizerAgent`  
Generates short, sarcastic summaries using LLM (OpenAI or ASI). Speaks in the voice of **Bender**.

### 🧾 `StorageAgent`  
Saves final summaries as Markdown and maintains hash tracking. Does **not** use LLM.

### 📢 `PublisherAgent`  
Publishes content to Telegram — either automatically or after manual review. Does **not** use LLM.

### 🤖 `BenderAgent`  
Posts periodic sarcastic crypto jokes using LLM and prompt-based generation. Requires no external data.

---

## 🔮 Forecast Pipeline

### 📊 `ForecastCollectorAgent`  
Collects OHLCV data from Binance on a 4-hour timeframe. Supports tokens like `BTCUSDT`, `ETHUSDT`. Does **not** use LLM.

### 🧮 `ForecastAnalystAgent`  
Calculates technical indicators (SMA, EMA, MACD, RSI, ATR, Bollinger Bands, volume spikes, etc.). Does **not** use LLM.

### 🧠 `ForecastInterpreterAgent`  
Reads calculated indicators and produces Fry-style, data-driven forecasts including trend direction, volatility, and recommendations. Uses LLM.

---

## 🧠 Language Models (LLMs)

The system supports two LLM providers:

- **OpenAI** (`gpt-4`, `gpt-4o`, `gpt-3.5-turbo`)
- **ASI** (`ASI-1`, `ASI-1 Mini`)

Each agent independently selects its model and provider via `.env` configuration. Generation is done through standard REST APIs.

---

## 🎭 Character Styling

All outputs are styled to fit the **Futurama** theme:

- Fry gives realistic forecasts — sometimes referencing Bender or Leela.
- Bender mocks the crypto world and posts edgy one-liners.
- Output is Markdown-formatted and easy to read.

You can change the theme to any fictional characters — just update prompt templates and `.env` variables.

---

## ⚙️ Tech Stack

- `Python 3`
- `uAgents` by Fetch.ai
- `dotenv` for config
- `OpenAI` and `ASI` APIs
- `pandas` for indicator logic
- `Binance API` for OHLCV data
- `Telegram Bot API` for publishing

---

## 📣 Follow the Telegram Channel

[https://t.me/ai_crypto_news_v1](https://t.me/ai_crypto_news_v1)
