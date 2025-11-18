# Snack Guardian AI

A Personalized AI Snack Concierge for Sensitive Stomachs

> **Note:** Snack Guardian is being developed as the Capstone Project for the **Kaggle × Google 5-Day AI Agents Intensive (November 2025)**
>
> You can have a look at this [repo, 5-day AI Agent (Google X Kaggle)](https://github.com/dpurkays/5day-ai-agents-google-kaggle) for my notes and codelabs.

## 🧩 Problem

People with digestive sensitivities such as GERD, acid reflux, IBS, or food intolerances, often struggle to figure out what they can safely eat, especially when tired, stressed, or low-energy. Searching online for “safe snacks” is time-consuming, overwhelming, and often leads to contradictory or generic advice.
There is no simple tool that understands your symptoms, your dietary restrictions, your preferences, and your body’s patterns all at once.

## 🌿 Solution

Snack Guardian is a multi-agent AI system that acts as a personalized snack concierge.
It analyzes your current symptoms, long-term food restrictions, and mood or cravings, then recommends safe, comforting snacks tailored to your body’s needs.

These agents deliver suggestions that feel personal, caring, and aligned with your digestive comfort.

## ⭐ Value

Snack Guardian helps users:

- Save time deciding what to eat
- Reduce discomfort by avoiding trigger foods
- Feel supported with gentle, personalized recommendations
- Discover new, safe snacks that match their energy level
- Build long-term awareness of patterns (“warm snacks feel better at night”)

Instead of relying on guesswork or generic lists, users get snack guidance that adapts to them.

## ⚙️ Tech & Tools

- Python
- Kaggle Notebook
- Google's ADK

## 📚 Concepts Used

- Multi-agent
  - Sequential Flow
- Custom Tools
- Persistent Memory
- RAG

## 🧱 Architecture

### 🧠 Orchestrator Agent

- Reads user message
- Calls memory tool, `user_profile_tool`
- Builds A2A payload
- Sends payload to the Diet Agent
- Formats & returns the final answer

### 🔍 Specialist Agent

- Receives structured payload
- Calls:
  - `user_profile_tool`
  - `snack_db_tool`
  - `gut_knowledge_retriever` (RAG)
- Filters snacks
- Sends structured suggestions back

### 🔁 Response Flow

**User → Orchestrator Agent → Specialist Agent → Orchestrator → User**

## 🍪 Stay Tuned

Snack Guardian is learning how to take care of sensitive tummies one snack at a time.

Over the next couple of weeks, I’ll be refining the agents, building the memory layer, and preparing the full write-up and demo video for the Kaggle × Google AI Agents Intensive Course.

Thanks for stopping by! Your stomach deserves nice things!
