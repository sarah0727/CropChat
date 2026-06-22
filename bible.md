# CropChat Bible

## 1. Objective

**What problem does CropChat solve?**
Crop disease information is scattered across research papers, 
agricultural extensions, and technical documents that farmers 
and researchers can't easily access or understand. CropChat 
makes this knowledge conversational and accessible.

**Who is the user?**
Agricultural researchers, students, and farmers who need quick, 
reliable answers about crop diseases, symptoms, and treatments 
without reading through dense research papers.

**What does success look like?**
A user can describe a crop disease symptom in plain English and 
get a accurate, sourced answer pulled from real research papers 
including peer-reviewed publications — deployed live and 
accessible to anyone with a link.

## 2. Stack
- Backend: Python, Flask, LangChain
- LLM: Groq (llama-3.3-70b-versatile)
- Vector DB: ChromaDB
- Embeddings: sentence-transformers
- Frontend: HTML, Tailwind CSS, JavaScript
- Deployment: Render
- Version control: GitHub

## 3. Architecture
User → Flask route → RAG pipeline → ChromaDB retrieval → Groq LLM → Flask response → User

## 4. Folder structure
(paste the structure we defined earlier)

## 5. Data sources
List every PDF you collect + why you chose it

## 6. Sprint log
Update this after every session — what you built, what broke, what you learned

## 7. Decisions Log

Why ChromaDB over FAISS?
ChromaDB is easier to set up locally, has a simple Python 
API, and persists data automatically. FAISS requires more 
manual handling. For v1, ChromaDB wins.

Why sentence-transformers over OpenAI embeddings?
Free, runs locally, no API cost per embedding call.

Why Groq over OpenAI?
Free tier, faster inference, no credit card needed for 
getting started.

Why Flask over Streamlit?
Already familiar with Flask. More control over UI. 
Looks more like a real product than a Streamlit app.

## 8. Known issues & fixes
Document every bug you hit and how you fixed it

## 9. How RAG Works (my understanding)

**Ingestion Pipeline (happens once):**
PDF/data → chunking (fixed/hybrid/semantic) → 
chunks converted to embeddings (sentence-transformers) → 
stored in vector database (ChromaDB) with semantic indices

**Retrieval Pipeline (happens every query):**
User query → embedded → similarity search in ChromaDB → 
ranked relevant chunks returned

**Generation (happens every query):**
Query + retrieved context + instructions → Groq LLM → 
answer delivered to user

**Why RAG over plain LLM:**
- Reduces hallucinations (LLM answers from real documents)
- Cost effective (no retraining when data changes)
- Solves knowledge cutoff (just update vector store)
- Context aware responses

**Future improvement to explore:**
Reranking — scoring retrieved chunks again for relevance 
before passing to LLM for even better accuracy.

## 10. Launch checklist
[ ] Working locally
[ ] Deployed on Render
[ ] GitHub README complete
[ ] Logo added
[ ] LinkedIn post written
[ ] Medium article written