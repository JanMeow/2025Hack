**Colab Notebook for 2025 Hackathon**


**Challenge: Find the Connection**

This repository contains two Colab notebooks designed for the 2025 Hackathon Challenge: Find the Connection.

1. Spatial Graph Construction from IFC Files (0802_Hack.ipynb)
The first notebook focuses on processing Industry Foundation Classes (IFC) files and converting them into a spatial graph where:

****Extracting IFC Data:****

Uses a simple Breadth-First Search (BFS) to traverse the IFC file and extract relevant spatial and structural information.
Writes the extracted data into graph nodes representing individual entities.
Graph Representation & Connectivity:

Each node represents an entity and is aware of its direct neighbors.
Indirect connections (corners) are identified using loop detection via Depth-First Search (DFS) with a maximum depth bound of 3 or 4.
If an entity can traverse back to itself within the depth limit, it is classified as a corner.
**Collision Detection:
**

Uses NumPy operations to determine intersecting vertices and faces between objects.
Checks for collisions by analyzing geometric intersections within the extracted IFC structure.
2. Material & Product Data Extraction using RAG (MaterialProductDataExtraction_RAG.ipynb)
The second notebook utilizes a Retrieval-Augmented Generation (RAG) approach powered by OpenAI's API to extract and embed textual information from PDF documents.
    
**Pipeline Overview:**

#Text Extraction from PDFs

1. Text data is extracted using PDFMiner.
The current version classifies text into titles or content based on font size.
Future versions will incorporate a small linear model to create a decision boundary using:
_Font size
Text length
Relative font size across the document
Summarization & Keyword Tagging_

2. Extracted text is processed using an LLM-based summarization model to generate key tags.
Embedding & Vector Storage

3. Keywords are converted into embeddings using an embedding model.
These embeddings are stored in ChromaDB for fast and efficient querying.


**Integration Between Notebooks:**
The output from the first notebook (spatial graph structure) is passed to the second notebook, where it is processed by the language model to generate embeddings.
These embeddings are then used to query the vector database (ChromaDB) for retrieval and analysis.
