A minimal Retrieval-Augmented Generation pipeline that answers questions from your own PDF documents.

![Simple RAG diagram]([docs/simple_rag_linkedin.png](https://github.com/Gaballah10/Simple-RAG/blob/main/simple_rag_linkedin.png))

## How it works

**Indexing (once)**
1. Load the PDF with `PyPDFLoader`
2. Split it into chunks (1000 characters, 200 overlap)
3. Embed each chunk with OpenAI embeddings
4. Store the vectors in FAISS

**Querying (every question)**
1. Embed the question
2. Retrieve the Top-K closest chunks (k = 2)
3. Build a prompt from the chunks and the question
4. Let the LLM answer from that context
