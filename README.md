# GROQ and LLAMA-3 Custom Retrieval Augmented Generation Bot for your Documents via Gradio

This project implements a powerful Retrieval Augmented Generation (RAG) system using GROQ and LLAMA-3-8B model, with a user-friendly Gradio interface. It allows users to upload PDF documents, process them, and ask questions about their content, leveraging advanced language models to provide accurate answers.

![Gradio Interface](https://github.com/iShshnk/groq-llama3-rag-bot/blob/main/media/A.png)

## Features

- PDF document upload and processing
- Question answering based on the content of the uploaded PDF
- User-friendly interface powered by Gradio
- Utilizes GROQ and LLAMA-3 and Langchain for natural language processing
- Document chunking and embedding storage is provided via ChromaDB Vector Database for efficient search and retrieval 
- Docker containerization for easy deployment
- Automated build and push to Docker Hub using GitHub Actions

## Prerequisites

Before you begin, ensure you have met the following requirements:

- Docker (for running the containerized version)
- Groq API key

## Getting a Groq API Key

To use this application, you'll need a Groq API key. Follow these steps to obtain one:

1. Go to the [Groq website](https://www.groq.com/) and sign up for an account if you haven't already.
2. Once logged in, navigate to the API section of your account dashboard.
3. Generate a new API key. Make sure to copy it immediately, as you might not be able to see it again.
4. Keep this API key secure and do not share it publicly.

## Setup

1. Fork this repository to your GitHub account.
2. In your GitHub repository settings, add the following secrets:
   - `DOCKERHUB_USERNAME`: Your Docker Hub username
   - `DOCKERHUB_TOKEN`: Your Docker Hub access token
   - `GROQ_API_KEY`: Your Groq API key
3. Push any changes to the main branch to trigger the GitHub Actions workflow, which will build and push the Docker image to Docker Hub.

## Usage

To run the Docker container:

```bash
docker run -p 7860:7860 [your-dockerhub-username]/groq-llama3-rag-bot:latest
```

Replace `[your-dockerhub-username]` with your actual Docker Hub username.

Then, open your web browser and go to `http://localhost:7860` to access the application.

## How It Works

1. **PDF Upload**: Use the file upload component in the Gradio interface to select and upload your PDF document.

2. **PDF Processing**: After uploading, click the "Process PDF" button. This will:
   - Extract text from the PDF
   - Split the text into chunks
   - Create embeddings for each chunk
   - Store the embeddings in the ChromaDB vector database for quick retrieval

3. **Asking Questions**: Once the PDF is processed, you can type your questions into the text input field and click "Submit" to get answers.

4. **Retrieving Answers**: The system will:
   - Convert your question into an embedding
   - Search the ChromaDB vector database for relevant chunks
   - Use GROQ and LLAMA-3 models to generate an answer based on the retrieved chunks and your question

## Development

If you want to run the application locally for development:

1. Clone the repository:
   ```
   git clone https://github.com/[your-github-username]/groq-llama3-rag-bot.git
   cd groq-llama3-rag-bot
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Set up your Groq API key as an environment variable:
   ```
   export GROQ_API_KEY=your_groq_api_key_here
   ```

4. Run the application:
   ```
   python app.py
   ```

5. Open your web browser and go to `http://localhost:7860`.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Groq](https://console.groq.com/keys) for providing the LLM API
- [LangChain](https://github.com/hwchase17/langchain) for the document processing and QA chain
- [Gradio](https://gradio.app/) for the user interface framework

© 2024 Shashank Ramesh
