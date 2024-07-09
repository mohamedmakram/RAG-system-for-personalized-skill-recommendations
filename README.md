# RAG-application



## Requirements

1) Python 3.11 or later.

2) Install required packages:
```bash
pip install -r requirements.txt
```


## Pipeline

![RAG System]("RAG Pipeline.png)

1) Cleaning & Preparation
* Removed all the rows (based on their existance in the description columns) with missing values.
* Removed Requirements as it has most of the values missing.
* remove HTML tags from description.
* concatenate job_title with description.


2) Vector Database
* using FAISS to create our vector database.
* using HuggingFaceEmbeddings to create the embeddings.
* sentence-transformers/all-mpnet-base-v2 as my embedding model.
* break it into chuncks each of size 1000 characters with no overlap.

3) Chain
* build a prompt that forces the model to give and advice and arange them in steps or bullet points.
* using quantized (microsoft/Phi-3-mini-4k-instruct) to generate responses.
* retrieve chucks that are most similar to the query.
* (prompt + LLm + retrieved samples) --> Response.
