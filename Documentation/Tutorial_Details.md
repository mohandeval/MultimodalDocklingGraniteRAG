Reference: https://www.ibm.com/think/tutorials/build-multimodal-rag-langchain-with-docling-granite#824202000


# Multimodal retrieval-augmented generation

In this tutorial, you will use IBM’s Docling and open source IBM Granite vision, text-based embeddings and generative AI models to create a RAG system. These models are available via various open source frameworks. In this tutorial, we will use Replicate to connect to the IBM Granite vision and generative AI models and HuggingFace to connect to the embeddings model.


Retrieval-augmented generation (RAG) is a technique used with large language models (LLMs) to connect the model with a knowledge base of information outside the data the LLM has been trained on without having to perform fine-tuning. Traditional RAG is limited to text-based use cases such as text summarization and chatbots.

Multimodal RAG can use multimodal LLMs (MLLM) to process information from multiple types of data to be included as part of the external knowledge base used in RAG. Multimodal data can include text, images, audio, video or other forms. Popular multimodal LLMs include Google’s Gemini, Meta’s Llama 3.2 and OpenAI’s GPT-4 and GPT-4o.

For this recipe, you will use an IBM Granite model capable of processing different modalities. You will create an AI system to answer real-time user queries from unstructured data in a PDF.

Tutorial overview
Welcome to this Granite tutorial. In this tutorial, you’ll learn how to harness the power of advanced tools to build an AI-powered multimodal RAG pipeline. This tutorial will guide you through the following processes:

Document preprocessing: Learn how to handle documents from various sources, parse and transform them into usable formats and store them in vector databases by using Docling. You will use a Granite MLLM to generate image descriptions of images in the documents.
RAG: Understand how to connect LLMs such as Granite with external knowledge bases to enhance query responses and generate valuable insights.
LangChain for workflow integration: Discover how to use LangChain to streamline and orchestrate document processing and retrieval workflows, enabling seamless interaction between different components of the system.
This tutorial uses three cutting-edge technologies:

Docling: An open-source toolkit used to parse and convert documents.
Granite: A state-of-the-art LLM that provides robust natural language capabilities and a vision language model that provides image to text generation.
LangChain: A powerful framework used to build applications powered by language models, designed to simplify complex workflows and integrate external tools seamlessly.
By the end of this tutorial, you will accomplish the following:

Gain proficiency in document preprocessing, chunking and image understanding.
Integrate vector databases to enhance retrieval capabilities.
Use RAG to perform efficient and accurate data retrieval for real-world applications.
This tutorial is designed for AI developers, researchers and enthusiasts looking to enhance their knowledge of document management and advanced natural language processing (NLP) techniques. The tutorial can also be found in the IBM Granite Community’s Granite Snack Cookbook GitHub in the form of a Jupyter Notebook.


Step 3: Preparing the documents for the vector database
In this example, from a set of source documents, we use Docling to convert the documents into text and images. The text is then split into chunks. The images are processed by the MLLM to generate image summaries.

Use Docling to download the documents and convert to text and images
Docling will download the PDF documents and process them so we can obtain the text and images the documents contain. In the PDF, there are various data types, including text, tables, graphs and images.