1) Resume Optimization (Beginner)
----------------------------------
An effective yet time-consuming part of applying for jobs is adapting your resume to different job descriptions. While automating this task would have been an advanced project a few years ago, with today’s large language models, it is as simple as an API call.

Here’s a step-by-step breakdown of how to implement such an automation.

** Create a markdown version of your resume (Note: ChatGPT can do this for you).
** Experiment with different prompt templates that take your markdown resume and a job description and output a new resume in markdown.
** Use OpenAI’s Python API to prompt GPT-4o-mini to rewrite your resume dynamically.
** Convert the markdown file to HTML and then to PDF with the markdown and pdfkit libraries, respectively.

Libraries: openai, markdown, pdfkit

While we could readily use ChatGPT for this, the upside of implementing this with Python is that we can easily scale up the process. Here’s some starter code for Step 3.

Note: ChatGPT is super helpful for writing short code snippets (and prompts) like this. If you get stuck, try it for Step 4.


2) YouTube Lecture Summarizer (Beginner)
-------------------------------------------
Although I love adding technical talks to my YouTube “watch later” playlist, it might be a while before I watch them (if I ever get around to it 😅). A project that can help with this is a tool that watches the videos for me and generates concise summaries with key points.

Here’s one way to do that:

** Extract YouTube video ID from video link using regex
** Use video ID to extract transcript using youtube-transcript-api
** Experiment with different ChatGPT prompts that effectively summarize the transcript
** Use OpenAI’s Python API to automate the process

Libraries: openai, youtube-transcript-api

From a technical perspective, this is very similar to the first project. A key difference, however, is that we will need to automatically extract video transcripts, which we can feed into the LLM.



3) Automatically Organizing PDFs (Intermediate)
----------------------------------------------
My watch later playlist is not the only place I hoard technical information. Another cache is my desktop, which is riddled with (118) research papers. Since manually reviewing these papers would be (very) time-consuming, let’s see how AI can help.

One could build a tool that analyzes the contents of each PDF on my desktop and organize them into folders based on topics. Text embeddings can translate each paper into a dense vector representation, from which similar articles could be clustered using a traditional machine learning algorithm like K-Means.

Here’s a more detailed breakdown:

** Read the abstract of each research article using PyMuPDF
** Use the sentence-transformers library to translate abstracts into text embeddings and store them in a Pandas DataFrame
** Use your favorite clustering algorithm from sklearn to group the embeddings based on similarity
** Create folders for each cluster and move the files into the appropriate folder.

Libraries: PyMuPDF, sentence_transformers, pandas, sklearn

The key step for this project is generating the text embeddings. Here’s a code snippet for doing that with sentence_transformers.

4) Multimodal Search (Intermediate)
-----------------------------------
A couple of months ago, I helped a company create a basic RAG system for a set of technical reports. One of the challenges with searching such reports is that key information is often presented in plots and figures rather than text.

One way to incorporate this visual information into the search process is to use a multimodal embedding model to represent text and images in a shared space.

Here’s a basic breakdown:

** Given a PDF, chunk it into sections and extract the images using PyMuPDF
** Use a multimodal embedding model (e.g. nomic-ai/nomic-embed-text-v1.5) to represent the chunks and images as dense vectors and store them in a dataframe
** Repeat for all PDFs in the knowledge base
** Given a user query, pass it through the same embedding model used for the knowledge base
** Compute the cosine similarity score between the query embedding and every item in the knowledge base
** Return top k results

Libraries: PyMuPDF, transformers, pandas, sklearn

The most important part of this project is how the PDFs are chunked. The simplest way would be to use a fixed character count with some overlap between chunks. It is also helpful to capture metadata such as filename and page number for each chunk.

Here’s some basic boilerplate code to do that (courtesy of ChatGPT). If you get stuck, try asking it to extract the images.

5) Knowledge Base QA (Advanced)
--------------------------------
Over the past year, I’ve helped almost 100 businesses and individuals build AI projects. By far, the most common project people ask about is a document question-answering system. Building on the previous project, we can implement this in a straightforward way.

If we’ve already chunked and stored our documents in a DataFrame, we can convert the multimodal search tool into a multimodal RAG system.

Here are the steps:

** Perform a search over the knowledge base (like the one created in Project 4)
** Combine user query with top k search results and pass them to a multimodal model.
** Create a simple Gradio user interface for the QA system.

Libraries: PyMuPDF, transformers, pandas, sklearn, together/openai, Gradio

Note: Llama 3.2 Vision is free until 2025 via Together AI’s API

This project essentially combines projects 2 and 4. However, it includes the essential component of a user interface. For that, we can use a dashboarding tool like Gradio, which allows us to create a chat UI with a few lines of code.


-> What’s next?
---------------
Thanks to tools like ChatGPT and Cursor, it’s never been easier to build AI projects fast. Things that used to block me for hours (if not days) a few years ago can now be resolved in minutes with advanced coding assistants.

