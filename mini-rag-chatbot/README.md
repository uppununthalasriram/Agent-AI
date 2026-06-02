# Mini RAG Chatbot

## Overview

This project implements a simple Retrieval-Augmented Generation (RAG) chatbot capable of answering questions from a PDF document.

The chatbot performs:

* PDF text extraction
* Text chunking
* Embedding generation
* Vector storage using FAISS
* Semantic retrieval
* Context-based answering

---

## Technologies Used

* Python
* Jupyter Notebook
* LangChain
* FAISS
* Scikit-learn
* NumPy
* PyPDF

---

## Project Workflow

1. Load PDF document
2. Extract text from PDF
3. Split text into chunks
4. Generate embeddings using TF-IDF
5. Store embeddings in FAISS vector database
6. Retrieve relevant chunks using semantic similarity
7. Generate context-based answers

---

## Project Structure

mini-rag-chatbot/

├── Mini_RAG_Chatbot.ipynb

├── README.md

├── requirements.txt

├── sample_data/

│ └── sample.pdf

└── screenshots/

---

## How to Run

1. Install dependencies:

pip install -r requirements.txt

2. Open the notebook:

jupyter notebook

3. Run all notebook cells sequentially.

---

## Features

* PDF Question Answering
* Semantic Search
* Vector Database
* Retrieval-Augmented Generation
* Interactive Query System

---

## Future Improvements

* OpenAI/Gemini integration
* Streamlit UI
* Multi-PDF support
* Conversational memory

---

## Note

Due to compatibility issues between some transformer/Gemini SDK versions and the local Python environment, the final response generation step uses retrieved contextual chunks directly from the FAISS vector database.

The complete RAG pipeline is still fully implemented successfully.
