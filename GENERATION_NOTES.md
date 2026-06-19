# Generation Notes

Mode: ai

Model: gemini / gemini-2.5-flash

Fallback reason: OpenAI limit reached. Automatically switched to Gemini.

Architecture: PDF FAQ Knowledge Bot

Template path: templates/simple-rag/pdf-faq-knowledge-bot

Short description:

A beginner-friendly Retrieval-Augmented Generation (RAG) system for querying and summarizing cybersecurity incident evidence documents. Users can upload various reports, logs, and policies, then ask natural language questions to extract key information and insights.

Architecture notes:

- This architecture prioritizes simplicity and local deployability for a beginner RAG project. The React frontend provides an intuitive chat interface. The FastAPI backend orchestrates document ingestion, chunking, embedding, vector storage in ChromaDB, and the RAG query process. ChromaDB is chosen for its ease of setup as an embedded database. A local Sentence Transformer model handles document chunk embeddings, avoiding external API costs for this critical step. For text generation, a simple local LLM or a mock API is specified to ensure the project is fully runnable without requiring external API keys. This setup provides practical experience with core RAG components in a self-contained environment, making it ideal for portfolio demonstration.

Project planner agent workflow:

- Receive User Query: Define app boundaries, data flow, runtime stack, and integration points. Outputs: 
- Embed Query: Design FastAPI modules, service contracts, validation, and error handling. Outputs: 
- Retrieve Relevant Context: Design React screens, state flow, controls, and user feedback states. Outputs: 
- Construct LLM Prompt: Design persistence models, sample data, indexes, and audit records. Outputs: 
- Generate Answer: Define contract tests, smoke tests, and generated project validation. Outputs: 
- Return Answer: Define environment variables, Docker workflow, and repository packaging. Outputs: 
