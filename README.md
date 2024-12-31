# LangChainNeo4j
A repository showcasing the integration of LangChain, OpenAI, and Neo4j to build and visualize knowledge graphs from textual data. The project demonstrates entity extraction, graph construction, and hybrid search capabilities using advanced AI and graph technologies.

Neo4j Knowledge Graph with LangChain and OpenAI
This project demonstrates building a knowledge graph using Neo4j, LangChain, and OpenAI. It includes features such as entity extraction, knowledge graph visualization, and vector search capabilities.

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Usage](#usage)
   - [Environment Setup](#environment-setup)
   - [Loading and Processing Data](#loading-and-processing-data)
   - [Creating the Knowledge Graph](#creating-the-knowledge-graph)
   - [Graph Visualization](#graph-visualization)
   - [Vector Search](#vector-search)
   - [Entity Extraction](#entity-extraction)
6. [Technologies Used](#technologies-used)
7. [Future Enhancements](#future-enhancements)


---

## Introduction

This project combines the power of Neo4j's graph database, LangChain's modular framework, and OpenAI's language models to extract entities from text, create a knowledge graph, and visualize relationships. The project also incorporates hybrid search using vector embeddings.

---

## Features

- **Dynamic Knowledge Graph**: Automatically extracts relationships and entities from documents.
- **Graph Visualization**: Interactive graph visualizations using Neo4j and Cypher queries.
- **Vector Search**: Hybrid vector search capability to query documents based on embeddings.
- **Entity Extraction**: Extract structured data such as organizations and persons from text.

---

## Requirements

- Python 3.10+
- Neo4j Database
- OpenAI API Key
- Libraries: `langchain`, `langchain-community`, `neo4j`, `wikipedia`, `tiktoken`, `yfiles_jupyter_graphs`





## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   
2. Install dependencies:

````bash
pip install --upgrade langchain langchain-community langchain-openai langchain-experimental neo4j wikipedia tiktoken yfiles_jupyter_graphs
````
3. Set up environment variables for Neo4j and OpenAI API Key:

In the notebook, configure:

os.environ["OPENAI_API_KEY"] = "<YOUR_API_KEY>"
os.environ["NEO4J_URI"] = "your-neo4j-uri"
os.environ["NEO4J_USERNAME"] = "your-username"
os.environ["NEO4J_PASSWORD"] = "your-password"


## Usage

### 1. Setting Up the Environment
Initialize the environment by installing required libraries and configuring credentials for Neo4j and OpenAI.

### 2. Loading and Processing Documents
- Load documents from Wikipedia using `WikipediaLoader`.
- Preprocess documents by splitting text into manageable chunks.

### 3. Creating the Knowledge Graph
- Use `LLMGraphTransformer` to extract relationships and entities.
- Add extracted information to Neo4j as nodes and edges.

### 4. Visualizing the Knowledge Graph
- Run Cypher queries to visualize the graph:
  ```cypher
  MATCH (s)-[r:!MENTIONS]->(t) RETURN s,r,t LIMIT 50
- Render the graph using GraphWidget.

### 5. Vector Search Integration
- Generate embeddings for document nodes using `Neo4jVector` and OpenAI embeddings.
- Perform hybrid search with vector similarity and Cypher queries.

### 6. Entity Extraction
- Use `ChatPromptTemplate` and a structured entity class to extract information from text queries:
  ```python
  entity_chain.invoke({"question": "Where was Amelia Earhart born?"}).names

## Technologies Used
- **LangChain**: Framework for building LLM-powered applications.
- **Neo4j**: Graph database for relationship modeling.
- **OpenAI GPT**: Language model for processing and generating text.
- **WikipediaLoader**: Document loader for Wikipedia data.
- **Google Colab**: Optional environment for running notebooks.

## Future Enhancements
- Add support for multilingual text processing.
- Expand entity extraction to include additional entity types (e.g., locations, events).
- Integrate open-source embedding models for vector search.
- Provide a web-based frontend for querying the graph.

