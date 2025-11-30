# langchain-rag-chat-history-pipeline

This repository contains a complete Retrieval-Augmented Generation (RAG) pipeline built using **LangChain**, **ChatGroq**, **Chroma Vectorstore**, and **RunnableWithMessageHistory** for multi-turn conversational memory.

It includes vectorstores, retrievers, RAG chains, and history-aware conversation pipelines.

---

## 📌 Features

### ✅ 1. Modern LangChain RAG Pipeline
- Uses the **new Runnable pipeline**
- Clean flow using the `|` operator
- Updated for the latest LangChain versions (no deprecated chain imports)

### ✅ 2. Vectorstore + Retriever
- Uses **Chroma** vector database
- Stores document embeddings
- Efficient similarity search for relevant chunks

### ✅ 3. History-Aware Retriever
- Reformulates follow-up questions into standalone queries
- Uses `MessagesPlaceholder("chat_history")`
- Handles multi-turn conversations intelligently

### ✅ 4. Conversational RAG Pipeline
- Uses **RunnableWithMessageHistory**
- Supports session-based memory (ex: `chat1`, `chat2`, etc.)
- Stores chat history in a custom dictionary
- Automatically logs both user and AI messages

### ✅ 5. Fully Updated (2025-Compatible)
Old LangChain functions removed in newer versions:
create_retrieval_chain  
create_stuff_documents_chain

This project uses the correct **new LangChain RAG pipeline** approach.

---

## 🔧 Installation

Create a virtual environment:

python -m venv venv  
source venv/bin/activate      # macOS/Linux  
venv\Scripts\activate         # Windows  

Install dependencies:

pip install -r requirements.txt

---

Example usage:

response = conversational_rag_chain.invoke(
    {"input": "what are types of memory?"},
    config={"configurable": {"session_id": "chat1"}}
)
print(response["answer"])

---

## 🧠 How the Pipeline Works (High-Level)

### Step 1: User asks a question
LLM receives the raw question.

### Step 2: History-aware query reformulation
If the user asks a follow-up question:
"What are the types of memory?"  
Then:  
"And explain any one?"  
→ Reformulated: "Explain any one type of memory."

### Step 3: Retriever fetches relevant chunks
Vectorstore performs similarity search.

### Step 4: Prompt injects:
- the context  
- the user input  
- the chat history  

### Step 5: LLM generates answer

### Step 6: Conversation history is saved

Sessions are independent:
chat1 → memory of chat 1  
chat2 → separate memory  
chat3 → separate memory

---

## 🛠️ Technologies Used

- LangChain  
- Groq (llama-3.1-8b-instant)  
- Chroma Vectorstore  
- RunnableWithMessageHistory  
- Embeddings- HuggingFace Embeddings
- Retrievers  
- PromptTemplates  

---

## 🎯 Learning Goal

This repo is built to help me master:
- RAG pipelines  
- Chat memory  
- History-aware retrieval  
- Prompt engineering  
- New LangChain runnable architecture  
- Building real LLM applications  

---
