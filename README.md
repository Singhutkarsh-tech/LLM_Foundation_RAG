*Milvus + LangChain + RAG + LLM Cache* 
A hands-on project where I explored how **vector databases, RAG pipelines, and LLM caching** actually come together in a real environment.

This repo combines everything I’ve learned about **vector databases**, **retrieval-augmented generation (RAG)**, and **intelligent caching for LLMs** into one place.  
It’s built using **Milvus**, **LangChain**, **SentenceTransformers**, and **Docker**, and covers three complete use-cases:

1. Building and managing a Milvus vector database from scratch.  
2. Running a full **RAG pipeline** with embeddings and PDF ingestion.  
3. Using Milvus as a **vector-based cache** for LLM responses.

Everything here is coded, tested, and working end-to-end.

*File*	                                                    *Description*
docker-compose.yml	                                        Deploys Milvus and dependencies in a local Docker environment.
milvus-database-operations.ipynb	                        End-to-end Milvus basics: connections, DB/user creation, data insertion, and ANN searches.
rag_with_milvus.ipynb	                                    Full RAG pipeline: PDF ingestion → text cleaning → chunking → embedding → Milvus vector storage → LLM query answering.
vector-db-as-LLM-cache.ipynb	                            Demonstrates Milvus as a vector cache for LLM queries to reduce redundant API calls and latency.
course.csv	                                                Sample course data used for embedding and vector insertion.
LLM_Demo.pdf	                                            Example long-form document used to create embeddings for RAG queries.
LICENSE	                                                    Open-source MIT license.


1. milvus-database-operations.ipynb
	•	Connects to Milvus and creates a fresh DB.
	•	Creates a schema with FieldSchema and CollectionSchema.
	•	Uses SentenceTransformers (all-MiniLM-L6-v2) to embed text.
	•	Inserts vector data and builds an IVF_FLAT index.
	•	Demonstrates both scalar queries (course_id == 1003) and ANN vector searches using cosine similarity.

 2. rag_with_milvus.ipynb
	•	Loads and cleans a PDF using LangChain’s PyMuPDFLoader.
	•	Splits the document using RecursiveCharacterTextSplitter.
	•	Generates embeddings for each chunk and stores them in Milvus.
	•	Builds an index and retrieves semantically similar chunks using vector search.
	•	Constructs a query prompt and passes it to an LLM (Llama3.2 via Ollama) for context-aware answering.
	•	Essentially, this is a working Retrieval-Augmented Generation pipeline.

3. vector-db-as-LLM-cache.ipynb
	•	Converts prompts into embeddings and checks if a similar query already exists in Milvus.
	•	If found → returns cached response instantly.
	•	If not found → queries the LLM (Gemini or Ollama), stores the result, and builds the cache.
	•	Helps reduce repeated API calls and latency for similar prompts.

Core Tools
	•	Milvus (vector DB)
	•	LangChain
	•	SentenceTransformers
	•	Transformers
	•	Pandas / NumPy

For LLMs
	•	Ollama (local)
	•	Google Gemini 2.5 Flash
	•	OpenAI API (optional)

Indexing
	•	IVF_FLAT
	•	COSINE / L2 metrics


Learning Outcomes
	•	Understood how to integrate Milvus with LangChain
	•	Learned the full lifecycle of a vector search pipeline
	•	Implemented a real Retrieval-Augmented Generation system
	•	Built a vector cache to improve LLM response efficiency
	•	Deployed everything locally using Docker Compose


--UTKARSH SINGH
--ML-AI/Data Engineer, BITS Pilani