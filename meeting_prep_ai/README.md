# Meeting Prep AI Agent

## Overview

Meeting Prep AI Agent helps users prepare for upcoming client meetings by automatically gathering information from multiple sources and generating a concise meeting brief.

The agent demonstrates:

* Retrieval-Augmented Generation (RAG)
* Short-Term Memory
* Long-Term Memory
* Agentic Workflow
* Tool Usage

---

## Features

### RAG using FAISS

Client documents are embedded using Sentence Transformers and stored in a FAISS vector database.

### Short-Term Memory

Maintains conversation context during the current session.

### Long-Term Memory

Stores client preferences and historical information for future retrieval.

### Agentic Workflow

The agent reasons about the user's request and uses multiple tools before generating a response.

### Tools

1. Document Search Tool
2. Meeting Notes Retrieval Tool
3. Memory Retrieval Tool

---

## Architecture

User Query

↓

Meeting Agent

↓

Tools

* Document Search (FAISS)
* Meeting Notes Retrieval
* Memory Retrieval

↓

LLM

↓

Meeting Brief

---

## Sample Query

Prepare me for my meeting with Acme Corp.

---

## Sample Output

MEETING BRIEF

Client: Acme Corp

Current Projects:

* Cloud Migration
* Dashboard Deployment

Previous Discussions:

* API Integration Completed
* Dashboard Deployment

Open Action Items:

* Share Migration Roadmap
* Provide Dashboard Access

Client Preferences:

* Weekly Updates
* Concise Reports

Suggested Talking Points:

* Migration Progress
* Deployment Timeline
* Reporting Improvements

---

## How to Run

Install dependencies:

pip install -r requirements.txt

Open:

Meeting_Prep_AI_Agent.ipynb

Run all cells from top to bottom.
