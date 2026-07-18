# GitHub Codebase Assistant (RAG)

A Retrieval-Augmented Generation (RAG) application that enables semantic question answering over GitHub repositories. Instead of relying on keyword search, the project indexes source code using embeddings and retrieves the most relevant code snippets before generating answers with an LLM.

## Features

* Clone and index a GitHub repository.
* Custom repository loader with metadata (file path, filename, language).
* AST-based code parsing for Python to extract classes and functions as semantic chunks.
* Hybrid chunking strategy:

  * Keep small classes/functions intact.
  * Split only oversized code blocks using `RecursiveCharacterTextSplitter`.
* Hugging Face embeddings (`sentence-transformers/all-MiniLM-L6-v2`) for semantic search.
* FAISS vector database for fast similarity retrieval.
* Groq LLM (`llama-3.3-70b-versatile`) for context-aware code explanations.
* Metadata-aware retrieval with source file references.

## Tech Stack

* Python
* LangChain
* Hugging Face Embeddings
* FAISS
* Groq API
* Python AST

## Architecture

GitHub Repository → Custom Loader → AST-Based Chunking → Hybrid Chunking → Embeddings → FAISS → Retriever → Groq LLM → Answer

## Example Queries

* Where is JWT authentication implemented?
* Explain the architecture of this project.
* Which files call this API?
* Where is the database connection established?
* Explain the `UserService` class.

## Future Improvements

* Tree-sitter support for JavaScript, TypeScript, Java, Go, and other languages.
* Method-level indexing for more precise retrieval.
* Metadata-based filtering (class/function/file).
* Conversational memory for multi-turn code exploration.
* Support for large repositories with incremental indexing.
