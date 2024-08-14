Building a Retrieval-Augmented Generation (RAG) Application
RAG on the Holy Quran Text
1. Project Overview
This document provides a step-by-step guide on how to build a Retrieval-Augmented Generation (RAG) application. The application allows users to ask questions about the Quran, and it retrieves relevant verses and generates a response based on the context provided by those verses.
2. Setting Up the Environment
To build the RAG application, the following libraries and tools were used:
- `joblib`: For loading the Quran verses dataset.
- `transformers`: For utilizing a pre-trained text generation model.
- `pydantic`: For data validation.
- `gradio`: For building the user interface.
- `gdown`: For downloading files from Google Drive.
- `re`: For regular expression operations.
- `langchain`: For document management and vector store operations.
- `faiss`: For creating a vector database.
3. Data Download and Preparation
The dataset used in the RAG application was initially downloaded from Kaggle. The dataset contained the Quranic verses in a csv format, which were then cleaned and formatted for use in the application. The cleaning process involved removing any irrelevant information and standardizing the format of the verses to include chapter numbers, verse numbers, and the text of the verses. Once cleaned, the dataset was stored in a file on Google Drive for easy access and integration into the application.
4. Embedding Model Initialization
To convert the Quran verses into vector embeddings, the `HuggingFaceEmbeddings` model from the `langchain_community` library was used. The model 'thenlper/gte-small' was chosen for its efficiency and accuracy in generating embeddings.
5. Document Processing
Each verse was processed using a regular expression to extract the chapter number, verse number, and the verse text. These were then converted into `Document` objects with metadata. The metadata stored the chapter and verse numbers, allowing for easy retrieval and formatting later on.
6. Building the FAISS Vector Database
The processed documents were stored in a FAISS vector database, which allows for efficient similarity searches. The database was built using the `FAISS.from_documents` method, which took the list of documents and the embedding model as inputs.
7. Querying the FAISS Index
To retrieve relevant verses based on a user's query, the FAISS index was queried using the `similarity_search` method. This method returns the top-k most similar verses based on the query, which are then formatted with their corresponding chapter and verse numbers.
8. Context Preparation and Response Generation
The retrieved verses were combined into a context string, which was then passed to a text generation model from the `transformers` library. The model, 'openai-community/gpt2-xl', generated a concise answer based on the provided context.
9. Building the Gradio Interface
The user interface for the application was built using the `Gradio` library. The interface included a textbox for the user to input their question and an output box to display the generated answer. Custom CSS was used to style the interface.
10. Deploying the Application
The application was launched using Gradio's `launch` method, which started a local web server for testing and interaction. Users could interact with the application by entering questions related to the Quran, and the model would generate a response based on the retrieved verses.
11. Deploying the Application on Hugging Face Spaces
To deploy the RAG application on Hugging Face Spaces, I followed these steps:
1.	Created a Hugging Face Account and Space:
o	I logged into my existing Hugging Face account and navigated to the 'Spaces' section.
o	I created a new Space and selected 'Gradio' as the SDK since the application was built using Gradio.
2.	Prepared the Repository:
o	I cloned the newly created Space repository to my local machine using Git.
o	I added all necessary files to the repository, including the Python script containing the RAG application code, the quran_verses.joblib file, and a requirements.txt file listing all required dependencies (e.g., gradio, transformers, langchain, faiss).
3.	Configured and Launched the Application:
o	After ensuring all the files were in place, I committed the changes and pushed them to the Hugging Face Space repository.
o	The Space automatically built and deployed my application.
o	Once the deployment was complete, the application was live and accessible via the Hugging Face Space URL.
This process allowed me to successfully deploy my RAG application on Hugging Face Spaces, making it accessible to anyone with the link.
Link: https://huggingface.co/spaces/defoxtrotalpha/Ask-Holy-Quran
