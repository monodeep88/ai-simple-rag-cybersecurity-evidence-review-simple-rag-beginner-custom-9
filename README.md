# Cyber Evidence RAG Assistant

## Project Overview

Cyber Evidence RAG Assistant is a complete full-stack AI project for **Simple RAG** at **Beginner** difficulty. It includes a FastAPI backend, a React frontend, sample documents, vector search with ChromaDB support, source citations, timeline logs, structured run storage, Docker files, and tests.

Cybersecurity Evidence Review involves analyzing diverse digital artifacts (e.g., incident reports, log files, vulnerability scans, policy documents) to understand security incidents, assess compliance, or identify threats. This project simplifies that process by allowing a user to 'chat' with their evidence base, retrieving relevant sections and generating concise answers to specific questions, reducing manual document review time.

Difficulty controls project complexity, architecture depth, AI model selection, and how advanced the generated codebase is.

- Architecture depth: minimal backend, simple folder structure, easy README, low-cost/free model
- Selected architecture: PDF FAQ Knowledge Bot
- Template path: templates/simple-rag/pdf-faq-knowledge-bot
- Generated stack: FastAPI backend, React UI, local vector fallback, simple tests
- README style: beginner-friendly setup and clear expected output

## Tech Stack

- Backend: Python, FastAPI, Pydantic, SQLAlchemy
- AI/RAG: LangChain-ready prompt layer, ChromaDB vector storage, local deterministic fallback model
- Workflow: Agent pipeline with planner, retrieval, tool, reasoning, and final answer steps
- Frontend: React and Vite
- Database: SQLite by default, PostgreSQL through Docker Compose
- Testing: pytest
- Difficulty: Beginner

## Generation Method

This project was generated with a template-based architecture engine. AI is used only for the blueprint, domain customization, sample data, prompts, and documentation. The codebase is produced from tested FastAPI/React/Docker templates rather than raw LLM source output.

## Project Type Satisfaction Map

This generated project satisfies **Simple RAG** through the runtime path below. The implementation is not only a README claim: the files listed after the diagram are generated in the repository and validated before GitHub push.

```text
[User]
  |
  | question / task details / tone / constraints
  v
[React Frontend]
  |
  | POST /api/ask
  v
[FastAPI Backend]
  |
  +--> [Vector Store / Sample Docs]
  |        |
  |        +-- retrieved context / cited sources
  |
  v
[Retriever]
  |
  v
[Citation Answer Builder]
  |
  v
[Final Answer Builder]
  |
  | answer + sources + timeline steps
  v
[React Frontend]
  |
  v
[User sees final output + agent timeline]
```

Runtime proof points:

- `frontend/src/App.jsx` renders the user workspace, starter prompts, answer panel, cited sources, and timeline.
- `backend/app/main.py` exposes `POST /api/ask` and returns the final answer, sources, timeline steps, and project type.
- `backend/app/services/pipeline.py` orchestrates the project-type flow: Retriever, Citation Answer Builder.
- `backend/app/services/vector_store.py` loads sample documents and retrieves relevant cited context.
- `backend/app/domain.py` contains the generated topic-specific workflow steps, business rules, tools, persona, and starter questions.
- `backend/app/db.py` stores each run so the generated app behaves like a real workflow tool instead of a static prompt demo.
- `backend/tests/test_project_contract.py` validates the API contract and project-type behavior.

Type-specific behavior:

- Flow style: User question -> load documents -> split chunks -> embed -> Chroma similarity search -> answer with citations.
- Visible output: final answer, cited sources, timeline steps, and project type.
- Validation gate: pytest, frontend build, Docker Compose config, and Docker build before repository upload.

## Folder Structure

```text
ai-simple-rag-cybersecurity-evidence-review-simple-rag-beginner-custom-9/
  backend/
app/
  main.py
  config.py
  db.py
  schemas.py
  data/sample_docs/
  services/
text.py
vector_store.py
llm.py
tools.py
pipeline.py
tests/
  test_project_contract.py
requirements.txt
Dockerfile
  frontend/
src/
  App.jsx
  main.jsx
  styles.css
package.json
Dockerfile
  docker-compose.yml
  .env.example
  README.md
  ARCHITECTURE.md
  WHY_THIS_PROJECT.md
  DEPLOYMENT.md
  docs/screenshots/app-preview.svg
```

## Environment Variables

```env
OPENAI_API_KEY=
OPENAI_MODEL=gpt-4o-mini
USE_CREWAI_RUNTIME=false
PINECONE_API_KEY=
PINECONE_INDEX_NAME=
DATABASE_URL=sqlite:///./app.db
ALLOWED_ORIGINS=http://localhost:5173,http://localhost:3000
VITE_API_URL=http://localhost:8000
```

The app runs without an OpenAI key by using a deterministic local answer model. Add `OPENAI_API_KEY` to use LangChain with OpenAI. For CrewAI projects, set `USE_CREWAI_RUNTIME=true` after installing dependencies to run the live CrewAI Agent/Task/Crew workflow; otherwise the app uses a deterministic CrewAI-shaped fallback.

For Pinecone projects, add `PINECONE_API_KEY` and `PINECONE_INDEX_NAME` to use a live Pinecone index. Without them, the repo still runs using local ChromaDB/local retrieval fallback.

## Installation

```bash
cd backend
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

```bash
cd ../frontend
npm install
```

## Run Backend

```bash
cd backend
uvicorn app.main:app --reload --port 8000
```

## Run Frontend

```bash
cd frontend
npm run dev
```

## Run With Docker

```bash
docker compose up --build
```

## Example API Request

```bash
curl -X POST http://localhost:8000/api/ask ^
  -H "Content-Type: application/json" ^
  -d "{\"question\": \"What is the refund policy?\"}"
```

## Example User Question

```text
What should I do if a customer asks for a refund without an order id?
```

## Expected Output

The API returns:

- `answer`: a grounded answer generated from retrieved context
- `sources`: cited document chunks with similarity scores
- `steps`: planner, retriever, reasoning, tool-call, and final-answer timeline logs
- `project_type`: `Simple RAG`

## How The RAG/Agent Flow Works

User question -> load documents -> split chunks -> embed -> Chroma similarity search -> answer with citations.

## Project Planner Agent Workflow

User -> React Dashboard -> FastAPI -> Project Planner Agent -> Specialist Agents -> Generated Project -> Auto Testing -> GitHub Repository Creation -> Push Code -> Return GitHub URL

- **Receive User Query**: Define app boundaries, data flow, runtime stack, and integration points. Outputs: Project-ready output.
- **Embed Query**: Design FastAPI modules, service contracts, validation, and error handling. Outputs: Project-ready output.
- **Retrieve Relevant Context**: Design React screens, state flow, controls, and user feedback states. Outputs: Project-ready output.
- **Construct LLM Prompt**: Design persistence models, sample data, indexes, and audit records. Outputs: Project-ready output.
- **Generate Answer**: Define contract tests, smoke tests, and generated project validation. Outputs: Project-ready output.
- **Return Answer**: Define environment variables, Docker workflow, and repository packaging. Outputs: Project-ready output.

## AI-Customized Domain Workflow

- **1. Document Preparation:** User gathers cybersecurity evidence documents (e.g., incident reports, log files, policy docs).
- **2. Document Upload:** User navigates to the web UI and uploads one or more documents via the designated upload area.
- **3. Ingestion & Embedding:** The backend service receives the document, extracts text, splits it into smaller chunks, generates vector embeddings for each chunk, and stores these embeddings along with their original text in ChromaDB.
- **4. Document Listing:** The uploaded document appears in the 'Uploaded Documents' list on the UI, confirming successful ingestion.
- **5. Query Formulation:** User types a natural language question into the chat interface related to the uploaded documents (e.g., 'What was the timeline of the attack?').
- **6. Retrieval:** The backend embeds the user's query and performs a similarity search in ChromaDB to retrieve the most relevant document chunks.
- **7. Context Augmentation:** The retrieved chunks are combined with the user's original query into a coherent prompt for the LLM.
- **8. Generation:** The LLM processes the augmented prompt and generates a concise, relevant answer based solely on the provided context.

## Business Rules

- Documents must be less than 10MB to ensure efficient processing for a beginner setup.
- Only text-based documents (or those convertible to text like PDF) are supported.
- Document chunks must have a minimum length to ensure semantic meaning (e.g., 50 characters).
- The RAG system must only answer questions based on the content of the uploaded documents; no external knowledge.
- The system should prioritize factual extraction and summarization over creative generation.
- Maximum of 5 relevant chunks will be retrieved for context augmentation to manage LLM token limits.
- A clear error message must be displayed if no relevant information is found for a query.

1. The backend loads sample documents from `backend/app/data/sample_docs`.
2. Documents are split into chunks.
3. Chunks are embedded and stored in ChromaDB when available, with a local fallback for development.
4. User questions are matched against relevant chunks.
5. Agent-specific steps run: planner, retriever, tool call, reasoning, reviewer, or graph nodes.
6. The final answer is returned with source citations and a timeline.

## Testing

```bash
cd backend
pytest
```

## Validation Gates Before GitHub Push

The SaaS validates generated projects before creating and pushing the GitHub repository:

- `pytest`
- `npm install`
- `npm run build`
- `docker compose config`
- `docker compose build`

## Portfolio Proof Files

- `WHY_THIS_PROJECT.md`: explains why this repo satisfies the selected project type.
- `ARCHITECTURE.md`: documents the runtime flow, agents/nodes, and validation strategy.
- `DEPLOYMENT.md`: gives Render, Railway, Vercel, and Docker deployment options.
- `docs/screenshots/app-preview.svg`: generated UI preview image for README/profile use.

## Deployment

See `DEPLOYMENT.md` for Render, Railway, Vercel, and Docker deployment steps.
