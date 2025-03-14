# Retrieval-Augmented Generation (RAG) with Multi-Agent Orchestration
## Overview
This project implements a Retrieval-Augmented Generation (RAG) pipeline using Microsoft Autogen's MagenticOne framework, Azure OpenAI's GPT-4o, and ChromaDB. The system consists of two key agents:

Data Ingestion Agent – Extracts, chunks, and stores document embeddings.

Query Processing Agent – Retrieves relevant document chunks and generates responses.

The Retrieval-Augmented Generation (RAG) with Multi-Agent Orchestration is an AI-powered system that dynamically retrieves, processes, and generates responses using a multi-agent framework, ensuring efficient and scalable workflow execution. The system is scalable and extensible, allowing multiple workflows to be configured dynamically to optimize agent execution for complex business tasks.

This solution enables efficient document processing and retrieval, ensuring AI-generated responses remain grounded in factual data.
The Retrieval-Augmented Generation (RAG) with Multi-Agent Orchestration is an AI-powered system that dynamically retrieves, processes, and generates responses using a multi-agent framework, ensuring efficient and scalable workflow execution.
The Retrieval-Augmented Generation (RAG) with Multi-Agent Orchestration is an intelligent AI-driven system designed to handle user queries efficiently. It combines a RAG pipeline with a multi-agent framework to retrieve relevant knowledge and generate precise responses. The system is scalable and extensible, allowing multiple workflows to be configured dynamically to optimize agent execution for complex business tasks.

## Architecture
### High-Level Workflow
The architecture consists of the following key components:
* **Document Ingestion**: Extract text from documents using Azure Form Recognizer.
* **Text Chunking**: Split extracted text into smaller, meaningful chunks.
* **Embedding Generation**: Generate vector embeddings using OpenAI's text-embedding-ada-002 model
* **Storage in ChromaDB**: Store embeddings for efficient retrieval.
* **Query Processing**: Retrieve relevant text chunks from ChromaDB.
* **Response Generation**: Generate accurate responses using GPT-4o with retrieved context.
* **User Query Handling**: The system processes user queries and determines the best approach to retrieve relevant information.
* **RAG Pipeline**: A combination of **retrieval-based** and **LLM-generated** responses ensures accurate and contextually relevant answers.
* **Multi-Agent Orchestration:**:
  * **Information Extraction Agent**: Extracts relevant data from unstructured sources, ensuring high-quality retrieval.
  * **Query Processing Agent**: Processes user queries, determines intent, and retrieves the most relevant responses from the knowledge base. 
* **Conversation Logs**: Managed using autogen-core event-logger_name, ensuring traceability and debugging capabilities.

## Component Breakdown
1) **Data Ingestion Agent**
   * Extracts text from documents (PDF, Word, etc.).
   * Splits text into chunks using LangChain's RecursiveCharacterTextSplitter.
   * Generates embeddings using GPT-4o embedding model.
   * Stores embeddings in ChromaDB.
2) **Query Processing Agent**
   * Accepts user queries.
   * Retrieves relevant chunks from ChromaDB using vector search.
   * Generates responses using GPT-4o, ensuring factual accuracy.
   * Responds with "I do not have enough information" if relevant data is unavailable.

## Technologies Used
* **Microsoft Autogen** - MagenticOne (Multi-agent framework)
* **OpenAI GPT-4o** (LLM for response generation)
* **Azure Form Recognizer** (Document processing)
* **ChromaDB** (Vector database for retrieval)
* **LangChain** (Text processing and chunking)
* **FastAPI** (For API-based interaction)

## Architecture Diagram

![Multi Agentic RAG](https://github.com/user-attachments/assets/a5faa236-c1b9-4b77-8429-4f78f2aa771e)

## Installation & Setup
1. Clone the Repository
   ```bash
   # Clone the repository
    git clone https://github.com/karthikpatel-code/Multi_Agentic_RAG.git
    cd Agentic

    # Create a virtual environment
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate

    # Install dependencies
    pip install -r requirements.txt
   
## Running the Application
    ```bash
    python application.py
## Query the Information Extraction and Data Ingestion API
    ```bash
    curl --location 'http://localhost:8000/runtask' \
    --form 'file=@"verizon-plan-data.pdf"' \
    --form 'query="{
        \"query\" : \"Please Ingest the document into vector store\",
        \"workflowid\" : \"Data Ingestion\",
        \"conv_id\" : \"1223634-abc66d5efg-123456-def-567-ghi\",
        \"conv_type\" : \"New\"
    }"'

## Query the Query Processing API
    ```bash
    curl --location 'http://localhost:8000/runtask' \
    --form 'query="{
        \"query\" : \"What is the pricing for Verizon Smart Family plan ?\",
        \"workflowid\" : \"Query Processing\",
        \"conv_id\" : \"12233-abcdefg-123456-def-567-ghi\",
        \"conv_type\" : \"New\"
    }"'

## Future Enhancements

* Hybrid Search (Dense + Sparse retrieval) for improved results.
* Multi-turn Conversational Memory for handling follow-up questions.
* Integration with CI/CD for automated deployment.


## Demo Video

https://github.com/user-attachments/assets/d65f22f5-2dce-4cf5-9270-7803933f7646




## Conclusion
This Retrieval-Augmented Generation (RAG) pipeline demonstrates the power of multi-agent collaboration in efficiently processing, retrieving, and generating responses from unstructured data. By leveraging Azure OpenAI, Microsoft Autogen, and ChromaDB, the system ensures that responses remain contextually relevant and factually accurate.

As a scalable and modular prototype, this implementation lays the foundation for expanding into a full-fledged AI-powered platform capable of handling multi-step workflows and complex automation tasks. With enhancements like hybrid search, conversational memory, and CI/CD integration, the solution can evolve into a robust, enterprise-grade AI system for knowledge management, document automation, and intelligent query processing.

This repository serves as a starting point for developers and researchers interested in building RAG-based AI applications, enabling seamless information retrieval and accurate response generation.









