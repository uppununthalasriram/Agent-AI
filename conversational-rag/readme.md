# Conversational RAG Assistant with Tool Calling

## Project Overview

This project implements a Conversational Retrieval-Augmented Generation (RAG) Assistant capable of:

* Maintaining conversation memory
* Understanding follow-up questions using chat history
* Rewriting follow-up questions into standalone questions
* Retrieving relevant information from a PDF document
* Calling external tools when required
* Routing user queries between document retrieval and tool execution

The system uses a PDF knowledge base, TF-IDF retrieval, Gemini 2.5 Flash for reasoning, and a custom tool for retrieving the current time.

---

## Features

### 1. Conversation Memory

The assistant stores previous user and assistant messages in a chat history list.

Example:

User: What is Python?

User: Explain it more.

The assistant understands that "it" refers to Python.

---

### 2. History-Aware Retrieval

Before retrieval, follow-up questions are rewritten into standalone questions.

Example:

Original Question:

Can you explain it more?

Rewritten Question:

Can you explain Python in more detail?

This improves retrieval quality and ensures context is preserved.

---

### 3. Retrieval-Augmented Generation (RAG)

The assistant retrieves relevant document chunks from the PDF using TF-IDF vectorization and cosine similarity.

Workflow:

1. Load PDF
2. Split document into chunks
3. Create TF-IDF vectors
4. Retrieve top matching chunks
5. Generate answers using retrieved context

---

### 4. External Tool

The project includes a tool:

get_current_time()

This tool returns the current system time.

Example:

User: What is the current time?

Assistant: The current time is 2026-06-02 15:45:30

---

### 5. Tool Calling

The assistant determines whether a user query requires a tool.

Workflow:

1. Detect tool requirement
2. Execute Python function
3. Return tool output
4. Generate final natural-language response

---

### 6. Routing Logic

The assistant decides whether to:

* Answer using retrieved document context (RAG)
* Use an external tool

Routing Process:

* If relevant context is available → RAG
* Otherwise → Tool Calling

---

## Tech Stack

* Python
* Gemini 2.5 Flash
* LangChain
* PyPDFLoader
* Scikit-Learn
* TF-IDF Vectorization
* Cosine Similarity

---

## Project Structure

conversational-rag-assistant/

├── Conversational_RAG_Assistant.ipynb

├── tools.py

├── README.md

├── requirements.txt

└── screenshots/

---

## Memory Implementation

Conversation history is maintained using:

```python
chat_history = []
```

Each interaction is stored as:

```python
{
    "role": "user",
    "content": user_query
}

{
    "role": "assistant",
    "content": answer
}
```

The history is used during question rewriting to generate standalone questions.

---

## Tool Implementation

Tool:

```python
def get_current_time():
    return datetime.now().strftime("%Y-%m-%d %H:%M:%S")
```

The tool is invoked when the query requires current time information.

---

## Steps to Run

### Step 1: Install Dependencies

```bash
pip install google-genai
pip install langchain
pip install langchain-community
pip install langchain-text-splitters
pip install pypdf
pip install scikit-learn
```

### Step 2: Add PDF

Place the PDF file inside:

```text
data/python_tutorial.pdf
```

### Step 3: Configure Gemini API Key

Replace:

```python
client = genai.Client(
    api_key="YOUR_GEMINI_API_KEY"
)
```

with your Gemini API key.

### Step 4: Run Notebook

Execute all notebook cells sequentially.

### Step 5: Start Conversation

Example:

```text
You: What is Python?

You: Explain it more

You: What is the current time?
```

---

## Example Queries

### Retrieval-Based Query

```text
What is Python?
```

### Follow-Up Query

```text
Explain it more
```

### Tool Query

```text
What is the current time?
```

---

## Screenshots Included

* Successful Retrieval-Based Answer
* Follow-Up Conversational Question
* Successful Tool Call

---

## Future Improvements

* Persistent chat history using SQLite
* Multiple tool support
* ChromaDB vector storage
* Source chunk display
* Hybrid retrieval techniques
* Advanced agent-based routing
