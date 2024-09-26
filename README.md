---

# NVIDIA NIM and LangChain - RAG Document Q&A Application

This is a Streamlit-based application for performing Retrieval-Augmented Generation (RAG) to answer questions based on document data using NVIDIA's Natural Language Processing (NLP) Model (`NVIDIAEmbeddings` and `ChatNVIDIA`). This application utilizes LangChain components to build document loaders, embeddings, and a vector database using FAISS, enabling Q&A from loaded documents.

## Features

- **NVIDIA NIM Integration**: Uses the `ChatNVIDIA` model (`meta/llama3-70b-instruct`) for answering questions based on document context.
- **Document Ingestion**: Loads and processes PDF documents into chunks for embedding using FAISS.
- **Context-based Q&A**: Prompts are generated based on provided context from the ingested documents.
- **Vector Embeddings**: FAISS-based vector store for document embedding and similarity-based retrieval.
- **Streamlit User Interface**: Provides an easy-to-use interface for users to input questions and view answers based on document search results.

## Setup and Installation

### Prerequisites

Ensure you have the following installed:
- Python 3.10+
- [Anaconda](https://www.anaconda.com/products/individual) (optional but recommended)
- [Streamlit](https://streamlit.io)
- [LangChain](https://langchain.com)
- NVIDIA API Key for authentication.

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/nvidia-nim-rag-app.git
   cd nvidia-nim-rag-app
   ```

2. **Set up the environment**:
   If you're using Conda, create and activate a new environment:
   ```bash
   conda create -p venv python=3.10 -y
   conda activate ./venv
   ```

3. **Install the required dependencies**:
   Install the necessary Python packages:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up your environment variables**:
   Create a `.env` file in the root of the project and add your NVIDIA API Key:
   ```env
   NVIDIA_API_KEY=your_nvidia_api_key
   ```

5. **Prepare your data**:
   Place your documents in the `./us_census` directory (as specified in the script) for document loading. This project uses PDF documents by default.

### Running the Application

1. **Run the Streamlit app**:
   ```bash
   streamlit run main.py
   ```

2. **Using the App**:
   - Input a question in the text box.
   - Click the "Documents Embedding" button to process the documents and prepare the vector store.
   - The app will retrieve relevant information and provide answers based on document similarity.

## Code Overview

### Main Components

- **Document Loading**: Using `PyPDFDirectoryLoader`, documents in PDF format are loaded from the `./us_census` directory.
- **Document Splitting**: Splits large documents into smaller chunks using `RecursiveCharacterTextSplitter` for efficient embeddings.
- **Embeddings**: NVIDIA embeddings (`NVIDIAEmbeddings`) are used to embed documents into vectors stored in FAISS.
- **Question Answering**: `ChatNVIDIA` LLM model is used to generate responses based on document context.

### Functions

- `vector_embedding`: Loads documents, splits them, and generates vector embeddings.
- Streamlit interface to capture user input and display answers, alongside document similarity results.

## Dependencies

The application relies on the following key Python libraries:

- `streamlit`: For building the web interface.
- `langchain`: A framework for working with LLMs and document embeddings.
- `langchain_community`: For document loaders, vector stores, and integration with NVIDIA endpoints.
- `NVIDIAEmbeddings` and `ChatNVIDIA`: NVIDIA AI models for embedding and Q&A.
- `FAISS`: A vector store for fast similarity search.

## Project Structure

```bash
.
├── main.py                     # Main application file
├── requirements.txt             # Required dependencies
├── us_census/                   # Directory containing PDF documents
└── README.md                    # Project README file
```

## Contributing

Feel free to open issues or contribute to this project by submitting pull requests. Ensure you follow the proper code style and test your changes before submitting.

## License

This project is licensed under the MIT License.

---
