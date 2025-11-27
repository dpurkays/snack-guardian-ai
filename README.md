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
- Google's ADK (Agent Development Kit)
- Gemini 2.5 Flash Lite
- SQLite (DatabaseSessionService)

## 📚 Concepts Used

- Multi-agent Architecture
- Sequential Agent Workflow
- Custom Tools
- Persistent Memory
- RAG

## 🧱 Architecture

![Alt text](./assets/images/snack_guardian_architecture.png)

### 🧠 GuardianDialogueAgent | Orchestrator

This is the root agent whom the user communicates with. It remembers personal details, acknowledges new information, summarizes what it knows, keeps a friendly, gentle tone and decides when to call the SnackGenerationPipeline.

It only calls the pipeline when:

- the user asks about snacks
- the user asks what they can eat
- the user asks for “something gentle”
- the user gives new long-term profile info (diet, restrictions, gut condition, etc.)

If the user is just chatting, the dialogue agent replies conversationally and does not call any tools.

### ⚙️ SnackPipelineAgent | Sequential Workflow

This pipeline runs only when the user asks for snacks or gives new profile info. It performs all the actual “work” (update profile → RAG → snack generation).

#### 1. 👤 UserProfileAgent

Extracts user profile information from each message:

- name
- diet preferences
- avoid ingredients
- gut conditions

Outputs a clean JSON profile, `user_profile_json`
This profile is passed to the next agent and reused in the dialogue.

#### 2. 🔍 ConditionRAGAgent

Looks up gut-friendly “safe” and “avoid” foods using a local JSON RAG knowledge base.

- Receives the user’s structured profile, `user_profile_json`
- Detects which condition applies
- Calls the custom tool: `gut_condition_lookup(query)`
- Returns either:
  - a list of matched condition entries, or
  - "None" if no condition applies

#### 3. 🍳 SnackChefAgent

Creates 1–2 snack ideas + simple recipe steps that respect user's diet.

- Uses user_profile_json
- Uses gut_knowledge
- Uses google_search (built-in ADK tool) to find recipe inspiration
- Produces simple recipes (2–4 steps)
- Avoids plain ingredients (no “just eat a banana”)

## 🍪 Stay Tuned

Snack Guardian is learning how to take care of sensitive tummies one snack at a time.

Over the next couple of weeks, I’ll be refining the agents, building the memory layer, and preparing the full write-up and demo video for the Kaggle × Google AI Agents Intensive Course.

Thanks for stopping by! Your stomach deserves nice things!
