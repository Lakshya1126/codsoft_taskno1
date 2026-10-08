# Chatbot
<div align="center">

# 🤖 Simple-Chatbot — Rule-Based Console Chatbot

**A lightweight, keyword-matching chatbot built in pure Python**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![CLI](https://img.shields.io/badge/Interface-Command--Line-4B4B4B?style=flat-square)](https://en.wikipedia.org/wiki/Command-line_interface)
[![No Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen?style=flat-square)](#-tech-stack-summary)

</div>

---

## 📋 Table of Contents

1. [What is this Project?](#-what-is-this-project)
2. [Key Features](#-key-features)
3. [How it Works — Conversation Flow](#-how-it-works--conversation-flow)
4. [Architecture Overview](#-architecture-overview)
5. [Project Structure](#-project-structure)
6. [Response Rules](#-response-rules)
7. [Installation & Running](#-installation--running)
8. [Tech Stack Summary](#-tech-stack-summary)
9. [Limitations](#-limitations)
10. [Future Scope](#-future-scope)

---

## 🎯 What is this Project?

The **Simple Chatbot** is a beginner-friendly, console-based chatbot built entirely in Python's standard library. It simulates a basic conversation by matching keywords in user input against a set of predefined rules, then responding accordingly.

There's no AI, no NLP model, and no external API calls — just straightforward `if`/`elif` string matching running inside a loop. It's designed as a starting point for understanding conversational logic before moving on to more advanced NLP-based or LLM-powered chatbots.

---

## ✨ Key Features

| Feature | Details |
|---|---|
| 👋 **Greeting Detection** | Responds to `hello` or `hi` anywhere in the input |
| 🙂 **Small Talk** | Recognizes "how are you" style questions |
| 🏷️ **Identity Response** | Answers questions about its own name |
| 🚪 **Graceful Exit** | Ends the loop cleanly on `bye` or `exit` |
| ❓ **Fallback Handling** | Returns a default message for unrecognized input instead of crashing |
| 🔁 **Continuous Loop** | Keeps the conversation going until the user exits |

---

## 🔄 How it Works — Conversation Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                      CHATBOT SESSION FLOW                       │
└─────────────────────────────────────────────────────────────────┘

1. START
   └── Print welcome message
         │
         ▼
2. LOOP (while True)
   └── Read user input → convert to lowercase
         │
         ▼
3. KEYWORD MATCHING
   ├── contains "hello" / "hi"       → greeting response
   ├── contains "how are you"        → small talk response
   ├── contains "your name"          → identity response
   ├── contains "bye" / "exit"       → farewell response + break loop
   └── no match                      → fallback response
         │
         ▼
4. REPEAT until "bye"/"exit" is entered
         │
         ▼
5. END — loop breaks, program exits
```

---

## 🏗️ Architecture Overview

The chatbot uses a **single-function, sequential rule-matching architecture** — no classes, no external state, no persistence. Everything lives inside one loop in one function call.

```
┌──────────────────────────────────────────────────────────┐
│                     TERMINAL (stdin/stdout)               │
│              User types input / reads responses           │
└───────────────────────────┬────────────────────────────────┘
                            │ input() / print()
                            ▼
┌──────────────────────────────────────────────────────────┐
│                    chatbot() function                     │
│                                                            │
│   while True:                                              │
│       user_input = input().lower()                         │
│       if / elif keyword checks ───► matched response       │
│       else ───► fallback response                          │
│       break on "bye" / "exit"                               │
└──────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
simple-chatbot/
│
└── chatbot.py     # Entire chatbot logic — single file, single function
```

---

## 📜 Response Rules

| Trigger Keyword(s) | Response |
|---|---|
| `hello`, `hi` | "Hello! How can I help you today?" |
| `how are you` | "I'm just a program, so I don't have feelings, but thanks for asking!" |
| `your name` | "I'm a simple chatbot created to assist you!" |
| `bye`, `exit` | "Goodbye! Have a great day!" *(then exits)* |
| *(anything else)* | "I'm sorry, I don't understand that. Can you please rephrase?" |

> Matching is done with simple substring checks (`in`), so keywords are detected anywhere within the sentence — not just as exact matches.

---

## 🚀 Installation & Running

### Prerequisites

| Tool | Purpose |
|---|---|
| Python 3.x | Only requirement — no external packages needed |

### Steps

```bash
# 1. Save the code as chatbot.py

# 2. Run it from your terminal
python chatbot.py

# 3. Start chatting — type your message after "You:"

# 4. Type "bye" or "exit" to end the session
```

---

## 🛠️ Tech Stack Summary

| Layer | Technology | Purpose |
|---|---|---|
| **Language** | Python 3 | Core logic and control flow |
| **I/O** | Built-in `input()` / `print()` | Terminal-based interaction |
| **Dependencies** | None | Runs with a standard Python install, no `pip install` needed |

---

## ⚠️ Limitations

- Purely rule-based — no understanding of context, grammar, or intent
- Only detects exact substrings, so typos or rephrased questions go unrecognized
- No memory of previous messages within the conversation
- Single-turn matching only — can't handle multi-part or follow-up questions
- No persistence — nothing is logged or saved between sessions

---

## 🔮 Future Scope

- Add more keyword/response pairs for broader coverage
- Integrate NLP libraries (`nltk`, `spaCy`) for intent recognition instead of raw substring matching
- Handle typos and fuzzy matching (e.g., `difflib`, `rapidfuzz`)
- Add conversation logging to a file or database
- Wrap the logic in a GUI (Tkinter) or web interface (Flask)
- Swap rule-based logic for an LLM-powered backend for open-ended conversation

<div align="center">

Developed by Lakshya Kansal

</div>

