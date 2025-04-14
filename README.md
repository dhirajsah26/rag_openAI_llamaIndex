🎬 Movie Recommendation RAG System
A Retrieval-Augmented Generation (RAG) pipeline for semantic movie recommendations, powered by OpenAI, LlamaIndex, and MongoDB Atlas.

GitHub License
Python 3.9+

🌟 Features
RAG Pipeline: Combines OpenAI embeddings with LLM generation for context-aware responses.

Semantic Search: MongoDB Atlas vector search retrieves relevant movies based on plot similarity.

Metadata Filtering: Optimizes LLM inputs by separating content (plots) from metadata (genres, cast).

Production-Ready: Scalable storage and retrieval using MongoDB.

🛠️ Tech Stack
Component	Technology
Embeddings	OpenAI text-embedding-3-small
LLM	OpenAI GPT (any model)
Orchestration	LlamaIndex
Vector Database	MongoDB Atlas (with Vector Search)
Data	TMDB Movie Dataset (cleaned)
⚡ Quick Start
Prerequisites
Python 3.9+

MongoDB Atlas cluster (with Vector Search enabled)

OpenAI API key

Installation
bash
Copy
git clone https://github.com/[Your-GitHub-Repo-Here].git  
cd movie-rag  
pip install -r requirements.txt  
Configuration
Rename .env.example to .env and add your keys:

ini
Copy
OPENAI_API_KEY=your_key_here  
MONGODB_URI=mongodb+srv://user:password@cluster.example.mongodb.net  
DB_NAME=movies  
COLLECTION_NAME=embeddings  
Usage
Embed Data:

python
Copy
python embed_data.py --dataset movies.json
Run Queries:

python
Copy
python query.py "Suggest a heartwarming holiday film for families"
Example output:

"I recommend 'The Polar Express' (2004) because its magical story about belief and generosity resonates across ages. The animation style and Tom Hanks' voice acting make it a festive classic."

📂 Project Structure
Copy
.
├── data/                   # Raw dataset (JSON format)
├── src/
│   ├── embed_data.py       # Data preprocessing & embedding pipeline  
│   ├── query.py            # Query engine with RAG  
│   └── utils/              # LlamaIndex helpers  
├── .env.example  
└── requirements.txt  
📊 How It Works
Data Flow:

Movie plots are split into nodes with metadata (genres, cast).

OpenAI generates embeddings for each node.

Vectors + metadata are stored in MongoDB Atlas.

Query Flow:

User question → Vector similarity search → Top 3 movie nodes retrieved.

Nodes + question → LLM → Grounded response.
