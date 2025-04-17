# Scientific Research Chatbot

This project implements an AI-powered chatbot that can answer questions based on scientific research papers stored in a database. The system uses vector similarity search and large language models to provide accurate, factually-grounded responses from the scientific literature.

## Overview

The Scientific Research Chatbot leverages a dual-LLM architecture:
- **Primary Model**: Google's Gemini 1.5 Flash for generating initial responses
- **Refinement Model**: Mistral 7B for verifying and refining responses against source material

The system uses FAISS (Facebook AI Similarity Search) for efficient similarity search to retrieve relevant content from the scientific papers.

## Features

- Vector-based semantic search using FAISS
- Retrieval-augmented generation for accurate responses
- MySQL database integration for document storage
- Dual LLM architecture for reliable answer generation
- Factual grounding in scientific literature

## Prerequisites

- Python 3.11+
- MySQL server
- Google API key (for Gemini and embeddings)
- HuggingFace API key (for Mistral)

## Required Packages

```bash
pip install langchain-huggingface
pip install --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib
pip install huggingface_hub
pip install langchain_community
pip install faiss-cpu
pip install langchain_google_genai
pip install langchain-google-community
pip install mysql-connector-python
pip install PyPDF2
pip install python-dotenv
```

## Setup

1. Clone this repository
2. Create a `.env` file with your API keys:
   ```
   GOOGLE_API_KEY=your_google_api_key
   HUGGINGFACE_API_KEY=your_huggingface_api_key
   ```
3. Set up a MySQL database named `chat_bot` with appropriate credentials
4. Create a `documents` table in the MySQL database to store scientific paper content
5. Place your PDF files in the `Data/` directory

## Usage

Run the main notebook (`Scientific_Chatbot.ipynb`) and interact with the chatbot through the command line interface:

```python
# Ask your queries
Ask a question (or type 'exit' to quit): What effects does climate change have on biodiversity?

# The system will provide a response based on the scientific papers in the database
```

## Architecture

1. **Data Storage**: Scientific papers stored in MySQL
2. **Embedding & Indexing**: Google's text-embedding-004 model creates vector embeddings stored in FAISS
3. **Retrieval**: When a query is received, semantically similar text chunks are retrieved
4. **Response Generation**: 
   - Gemini generates an initial response based on retrieved content
   - Mistral refines and verifies the response against the retrieved data

## Limitations

- Responses are limited to information available in the indexed documents
- The quality of responses depends on the coverage and quality of the scientific papers in the database
- API rate limits may apply depending on your usage of Google and HuggingFace APIs

## Future Improvements

- Web interface for easier interaction
- Support for more document formats beyond PDF
- Enhanced context handling for multi-turn conversations
- Citation generation to reference specific papers