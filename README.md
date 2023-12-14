# AI Youtube Assistant

</br>
<div align="center">
<a href="https://www.python.org/"><img src="./readme-content/Python.png" width="75" height="75"></a>
<a href="https://openai.com/"><img src="./readme-content/OpenAI.png" width="75" height="75"></a>
<a href="https://www.langchain.com/"><img src="./readme-content/Langchain.png" width="75" height="75"></a>
<a href="https://streamlit.io/"><img src="./readme-content/Streamlit.png" width="140" height="75"></a>
<a href="https://engineering.fb.com/2017/03/29/data-infrastructure/faiss-a-library-for-efficient-similarity-search/"><img src="./readme-content/FAISS.png" width="160" height="75"></a>
</div>

</br>

# Overview

- This repository is adapted from [this tutorial](https://www.youtube.com/watch?v=lG7Uxts9SXs) from Freecodecamp regarding how to build a Langchain agent that uses the OpenAI LLM to receive a Youtube video link and answer user inputted questions based on the content of that video
- The purpose of following this tutorial was to strengthen my Langchain skills, and to learn more about its [Document Loader](https://python.langchain.com/docs/integrations/document_loaders) functionality through a practical use case
- The content of this repository is split into two files; `langchain_helper.py` and `main.py`, which will be explained in detail below

# Content

## `langchain_helper.py`

This file is an implementation of a pipeline for processing YouTube video transcripts, creating a FAISS database, and generating detailed responses to user queries using langchain, OpenAI, and FAISS.

The `create_db_from_youtube_video_url` function initializes a FAISS database by processing the transcript of a YouTube video obtained from the specified URL. The transcript is segmented into documents using the RecursiveCharacterTextSplitter, and the FAISS database is created based on language embeddings.

The `get_response_from_query` function takes the FAISS database, a user query, and an optional parameter 'k' for the number of results to retrieve. It performs a similarity search in the FAISS database to obtain relevant documents. Subsequently, it constructs a prompt template using langchain's PromptTemplate, configuring an OpenAI language model (text-davinci-003) and a chain (LLMChain) to generate a detailed response to the user's query based on the retrieved documents.

## `main.py`

This file implements a Streamlit-based user interface that facilitates user interaction with langchain functionalities to process YouTube video transcripts and provide detailed responses to user queries. The UI includes text areas for entering a YouTube video URL and a user query, along with a submit button. The Streamlit layout is structured using the st.title for the main title and st.sidebar for the sidebar containing input fields.

Upon submitting the form, the code checks if both the YouTube video URL and the user query are provided. If so, it utilizes the langchain_helper module to create a FAISS (Facebook AI Similarity Search) database from the YouTube video transcript using the create_db_from_youtube_video_url function. Subsequently, it generates a response to the user query by calling the get_response_from_query function. The response and relevant document information are displayed in the Streamlit UI using st.subheader and st.text with text wrapping for improved readability.
