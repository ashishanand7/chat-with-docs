# Chat With Docs (CWD): Local Document Question-Answering System

CWD is a powerful tool that allows you to ask questions about your documents without an internet connection, leveraging the capabilities of Large Language Models (LLMs).

## Setup

1. Clone this repository.

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Download the LLM model (default: ggml-gpt4all-j-v1.3-groovy.bin) and place it in a directory of your choice.

4. Update the `.env` file in the root directory with appropriate values for your setup.
    - PERSIST_DIRECTORY is directory of stored embeddings.
    - SOURCE_DIRECTORY is directory of documents.
    - You can change the embedding model by modifying the `EMBEDDINGS_MODEL_NAME` in the `.env` file.
    - To use a different LLM, update the `MODEL_TYPE` and `MODEL_PATH` in the `.env` file.
    - MODEL_N_CTX is the model's context length to use for chunking purposes.

## Usage

1. Place your documents in the `source_documents` directory.

2. Run the document ingestion script:
   ```
   python load_docs.py
   ```
   This script processes the documents, creates embeddings, and stores them in a local vector database.

3. Start the question-answering system:
   ```
   python docGPT.py
   ```

4. Enter your questions when prompted. Type 'exit' to quit the program.

## How it works

1. `load_docs.py` processes documents from the `source_documents` directory, splits them into chunks, creates embeddings using the specified model, and stores them in a Chroma vector database.

2. `docGPT.py` sets up the question-answering system using the LangChain library. It loads the stored embeddings and the specified LLM model.

3. When you ask a question, the system retrieves relevant document chunks from the vector database and uses the LLM to generate an answer based on the retrieved information.