# SmartDocs

SmartDocs is a PDF-based question-answering system that uses
Retrieval-Augmented Generation (RAG) to answer questions from
an uploaded document.

Instead of relying entirely on an LLM's general knowledge,
SmartDocs retrieves relevant information from the PDF and uses
that context to generate answers.

## Features

- Extracts text from PDF documents.
- Splits document content into overlapping text chunks.
- Generates semantic embeddings using Sentence Transformers.
- Uses FAISS for similarity-based document retrieval.
- Uses Google Gemini to generate answers from retrieved context.
- Provides source information, including document name and page number.
- Includes a fallback when relevant information is not found.

## Architecture

1. Upload a PDF.
2. Extract text from each page.
3. Split the text into chunks.
4. Generate embeddings for the chunks.
5. Store embeddings in a FAISS index.
6. Convert the user's question into an embedding.
7. Retrieve the most relevant chunks.
8. Pass the retrieved context to Gemini.
9. Return an answer with source references.

## Technology Stack

- Python
- PyPDF
- Sentence Transformers
- FAISS
- Google Gemini API
- Google Colab

## Getting Started

The current V1 implementation runs in Google Colab.

1. Open the notebook in the `notebooks` directory.
2. Install the required dependencies.
3. Add your Gemini API key to Google Colab Secrets using the name
   `GEMINI_API_KEY`.
4. Enable notebook access to that secret.
5. Run the notebook cells.
6. Upload a text-based PDF and ask questions about its contents.

## Current Scope

- Processes one active PDF at a time.
- Processing a new PDF creates a new document index.
- Supports text-based PDFs.
- Uses a hosted Gemini model for answer generation.

## Limitations

- Scanned PDFs requiring OCR are not supported yet.
- The document index is held in memory during the notebook session.
- This version is a notebook prototype; a web interface and Flask
  backend are not included yet.

## Future Improvements

- Flask-based backend API.
- Web-based user interface.
- OCR support for scanned PDFs.
- Improved retrieval and answer evaluation.
- Persistent document storage.
