# RAG Complaint Chatbot  
**Author:** Bezawit Assefa 

This repository contains the work for building a **Retrieval-Augmented Generation (RAG) pipeline** using CFPB consumer complaint data. The project is divided into two main tasks: Exploratory Data Analysis (EDA) and preparing text data for semantic search using chunking, embedding, and vector store indexing.  

---

## Task 1: Exploratory Data Analysis (EDA)  

**Objective:** Understand the structure, distribution, and content of the complaint narratives to guide preprocessing and model development.  

**Key Steps:**  
1. Loaded the dataset of **82,164 complaints** with complete narratives.  
2. Analyzed **narrative lengths**: most complaints are very short (0–250 words), with a few very long ones (up to 6,469 words).  
3. Visualized the distribution of narrative lengths using a **histogram**. The visualization shows a right-skewed distribution: many short complaints, few long ones.  
 <img width="300" height="200" alt="image" src="https://github.com/user-attachments/assets/dcc166fb-94ed-4ee1-bb13-1aabd497d3eb" /> 

4. Cleaned the data:  
   - Converted all text to lowercase.  
   - Removed special characters and boilerplate phrases.  
   - Filtered complaints to include only key financial products like Credit Cards, Personal Loans, Savings Accounts, etc.  

**Deliverables:**  
- Cleaned CSV file (`filtered_complaints.csv`).  
- Histogram visualization of narrative lengths.  

---

## Task 2: Text Chunking, Embedding, and Vector Store Indexing  

**Objective:** Convert cleaned complaint narratives into a format suitable for **semantic search**, allowing retrieval of complaints based on meaning rather than keywords.  

**Key Steps:**  
1. **Sampling:**  
   - Randomly selected ~10,000–15,000 complaints while preserving **proportions of each product type**.  

2. **Chunking:**  
   - Split long complaint narratives into smaller chunks to help the model understand them better.  
   - Kept a small overlap between chunks to maintain context.  

3. **Embedding:**  
   - Used `SentenceTransformer` model `all-MiniLM-L6-v2` to convert chunks into **vectors (embeddings)**.  
   - This model is **fast, small, and accurate** for semantic search tasks.  

4. **Vector Store Indexing:**  
   - Stored all embeddings in **FAISS**, a vector database.  
   - Stored metadata alongside each chunk (complaint ID, product type) to trace results back to the source.  

**Deliverables:**  
- Notebook: `note_books/text_chunking_embedding.ipynb` (performs sampling, chunking, embedding, and indexing).  
- Persisted vector store saved in `vector_store/`.  
- Metadata and chunks used for embeddings.  


---

## Usage  

1. Open the notebooks in **Jupyter Notebook** or **VS Code**.  
2. Run the notebooks step by step to reproduce the results.  
3. For semantic search, load the vector store and use the embeddings to query similar complaints.  

---

**Summary:**  
This project allows searching consumer complaints based on meaning, not just keywords. Task 1 explored and cleaned the dataset, while Task 2 prepared the text for semantic search using chunking, embeddings, and FAISS vector storage.  



