# YouTube Transcript RAG System

A robust Retrieval-Augmented Generation (RAG) system designed to fetch YouTube video transcripts and enable intelligent question-answering capabilities using AI. This system is built with Flask, FAISS, and Transformers, optimized for CPU-only operation.

## Table of Contents
1. [Features](#features)
2. [Project Structure](#project-structure)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Configuration](#configuration)
6. [Technical Details](#technical-details)
7. [System Requirements](#system-requirements)
8. [Troubleshooting](#troubleshooting)
9. [Version 2.0 Improvements](#version-20-improvements)
10. [Contributing](#contributing)
11. [License](#license)
12. [Acknowledgments](#acknowledgments)

## Features

### Transcript Fetching
- Multiple retrieval methods with automatic fallback
- Support for English variants (US, UK, CA, AU) and auto-detection
- Intelligent retry logic with error handling
- Playlist processing via YouTube API

### Manual Input System
- Automatic timestamp removal and text cleaning
- Quality validation and duplicate detection
- Content length analysis

### Core Functionality
- FAISS vector store creation for semantic search
- Question-answering with Microsoft Phi-2 model
- Responsive web interface (Flask)
- CPU-only operation

### Error Handling
- Context-aware error messages
- Multiple flash message types
- Progress tracking
- Targeted recovery suggestions

## Project Structure

```
youtube_rag-system/
├── main.py                 # CLI interface
├── app.py                  # Flask web application
├── backend/
│   ├── transcript_fetcher.py  # YouTube transcript fetching
│   ├── vector_store.py        # FAISS vector database
│   └── rag_engine.py          # RAG question-answering
├── content/                   # Stores transcript files (.txt)
├── vector_db/                 # FAISS vector databases
├── static/
│   └── style.css             # Web interface styling
├── templates/
│   └── index.html            # Web interface template
├── requirements.txt          # Python dependencies
└── README.md                # Documentation
```

## Installation

### Recommended Method: Virtual Environment

1. Clone the repository:
   ```bash
   git clone https://github.com/Rishirajbal/youtube_rag-system.git
   cd youtube_rag-system
   ```

2. Create and activate virtual environment:

   **Linux/Mac:**
   ```bash
   python3 -m venv youtube_rag_env
   source youtube_rag_env/bin/activate
   pip install --upgrade pip
   ```

   **Windows:**
   ```cmd
   python -m venv youtube_rag_env
   youtube_rag_env\Scripts\activate
   python -m pip install --upgrade pip
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the application:
   ```bash
   python app.py
   ```

The web interface will be available at `http://localhost:12001`

## Usage

### Web Interface

1. **Single Video Processing**:
   - Enter YouTube URL in the fetch section
   - System automatically attempts multiple retrieval methods
   - Provides detailed error messages if unsuccessful

2. **Manual Input**:
   - Enter video title and paste transcript text
   - Automatic cleaning of timestamps and formatting
   - Quality validation before processing

3. **Playlist Processing**:
   - Enter playlist URL
   - System processes all available videos
   - Shows progress and summary statistics

4. **Question Answering**:
   - Select processed transcript
   - Enter natural language questions
   - View AI-generated answers with source context

### CLI Interface

Run `python main.py` for command-line access to:
- Transcript fetching
- Vector store creation
- Query functionality
- Data listing

## Configuration

### YouTube API
The system includes a pre-configured API key:

### Model Selection
Default models:
- Embeddings: `all-MiniLM-L6-v2` (SentenceTransformers)
- Language Model: `microsoft/phi-2` (Transformers)

## Technical Details

### Processing Pipeline
1. Transcript extraction using multiple methods
2. Text chunking (500-character chunks with 50-character overlap)
3. Embedding generation with SentenceTransformers
4. FAISS index creation for similarity search
5. RAG-based answer generation

### Key Components
- Flask web framework
- FAISS for vector similarity
- LangChain for RAG pipeline
- YouTube API integration

## System Requirements

- Python 3.8+
- 4GB RAM minimum
- Internet connection for initial setup

### Dependencies
Full list in requirements.txt including:
- Flask 2.3.3
- youtube-transcript-api 0.6.1
- sentence-transformers 2.2.2
- faiss-cpu 1.7.4
- transformers 4.35.2

## Troubleshooting

### Common Issues

1. **Module Not Found**:
   - Ensure virtual environment is activated
   - Verify all dependencies are installed

2. **Windows Installation**:
   - Use provided `fix_windows_install.py` if needed
   - Run as Administrator if encountering permission issues

3. **Transcript Fetching**:
   - Check video availability and transcript settings
   - Try manual input if automatic methods fail

4. **Memory Issues**:
   - Close other applications
   - Consider processing smaller batches

### Error Handling
The system provides specific error messages for:
- Transcript availability issues
- Network problems
- Processing failures
- Quality warnings

## Version 2.0 Improvements

### Enhanced Functionality
- Multi-language retry system
- Improved error detection
- Better fallback logic
- Detailed progress feedback

### User Experience
- Automatic text cleaning
- Quality validation
- Contextual help messages
- Improved error recovery

### Technical Improvements
- Robust URL handling
- Safe filename generation
- Better exception handling
- Automatic retry logic

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## Acknowledgments

- YouTube Transcript API for transcript extraction
- Hugging Face for transformer models
- FAISS team for vector search
- Flask developers
- Google for YouTube API access
