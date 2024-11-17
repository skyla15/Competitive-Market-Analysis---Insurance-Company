# NLP Competitive Market Analysis Kedro Project
This porject is to analyze markets in different domains. Since the supervisor is familiar with the insurance domain, this project will be focused on the insurance domain. However there is many potentials for this project to be extended to.  

#### General work flow with LangChain 
- [LangChain Guide Reference](https://python.langchain.com/docs/how_to/#output-parsers)  
    1. Search: Query to url (e.g., using GoogleSearchAPIWrapper)   
    2. [Document Loader](https://python.langchain.com/v0.1/docs/modules/data_connection/document_loaders/): load data from various sources(web sites, databases, YouTube, arXiv) of various types(PDF, HTML, Json, PowerPoint, etc) as a list of [```document objects```](https://api.python.langchain.com/en/latest/documents/langchain_core.documents.base.Document.html)  
        - Example: [AsyncChromiumLoader](https://python.langchain.com/docs/integrations/document_loaders/async_chromium/) / [AyncHtmlLoader](https://python.langchain.com/docs/integrations/document_loaders/async_html/) - lightweight, load raw HTML files from a list of URLs concurrently
        - Possibly substitue current crawler and transformer to make use of meta data of documents ( read [HTML Loader](https://python.langchain.com/v0.1/docs/modules/data_connection/document_loaders/html/) ) :  
            - spider crawler, FireCrawl(Subpage serach, markdown output ), AzureAIDocumentIntelligenceLoader(different file format supports) 
    3. [Transformer](https://python.langchain.com/docs/integrations/document_transformers/)
        - Example) [HTML2Text](https://python.langchain.com/v0.1/docs/integrations/document_transformers/html2text/) : HTML2Text provides a straightforward conversion of HTML content into plain text (with markdown-like formatting) without any specific tag manipulation. It's best suited for scenarios where the goal is to extract human-readable text without needing to manipulate specific HTML elements.
    4. [Text Splitters](https://python.langchain.com/v0.1/docs/modules/data_connection/document_transformers/): Split up text into chunks. 
        - Common choice: [RecursiveCharacterTextSplitter](https://python.langchain.com/v0.1/docs/modules/data_connection/document_transformers/recursive_text_splitter/) ( [Blog : Understanding RecursiveCharacterTextSplitter](https://dev.to/eteimz/understanding-langchains-recursivecharactertextsplitter-2846) )
        - [Chunk visualization](https://chunkviz.up.railway.app)
        - [Chunking Strategies for LLM Applications](https://www.pinecone.io/learn/chunking-strategies/)
        - Further readings :
            - [Sementic Chunker : Langchain - How to split text based on semantic similarity](https://python.langchain.com/docs/how_to/semantic-chunker/)   
            - [How Chunk Sizes Affect Semantic Retrieval Results](https://ai.plainenglish.io/investigating-chunk-size-on-semantic-results-b465867d8ca1)
            - [Levels of Text Splitting](https://github.com/FullStackRetrieval-com/RetrievalTutorials/blob/main/tutorials/LevelsOfTextSplitting/5_Levels_Of_Text_Splitting.ipynb)
    5. [Embeddings Models](https://python.langchain.com/docs/how_to/embed_text/)
        - Common choice: OpenAIEmbedding ( paid, better to use cache ), uggingFace(OpenSource; BGE, Mistral)
            - [OpenAI Embeddings](https://platform.openai.com/docs/guides/embeddings#what-are-embeddings), [Huggingface Embeddings Benchmark](https://huggingface.co/spaces/mteb/leaderboard)
        - Cache: [Caching](https://python.langchain.com/docs/how_to/caching_embeddings/), [LocalFileStore](https://python.langchain.com/api_reference/langchain/embeddings/langchain.embeddings.cache.CacheBackedEmbeddings.html), [CacheBacekdEmbeddings](https://python.langchain.com/api_reference/langchain/embeddings/langchain.embeddings.cache.CacheBackedEmbeddings.html)
    
    6. [Vector Store](https://python.langchain.com/v0.1/docs/modules/data_connection/vectorstores/):
        - Common choise: Local: Chroma, FAISS(For us, FAISS can be a good choice ) / Cloud - Pinecone, Weaviate, ElasticSearch / etc - Lance, Qdrant(for asynchronous operations)
        - Vector store queries
            - Similarity search / Similarity search by vector / Maximum marginal releance search / Asynchronous operations 
            - Possible issue: the versions of two methods (```.embed_documents```, ```.embed_query```) might differ due to updates of embedding models(version control needed)
        - [TODO] Understanding Indexing 
    7. [TODO] [Retrievers Explanation](https://python.langchain.com/v0.1/docs/modules/data_connection/) / [Retrievers](https://python.langchain.com/v0.1/docs/modules/data_connection/retrievers/) : A retriever is an interface that returns documents given an unstructured query. It is more general than a vector store. A retriever does not need to be able to store documents, only to return (or retrieve) them. Vector stores can be used as the backbone of a retriever, but there are other types of retrievers as well. Retrievers accept a string query as input and return a list of Document's as output.

- [Research Automation](https://python.langchain.com/v0.1/docs/use_cases/web_scraping/)
- [RAG Architecture](https://python.langchain.com/v0.1/docs/use_cases/question_answering/)    
- [Youtebe : RAG & Agentic RAG ](https://www.youtube.com/watch?v=hKfQ-0jLw3I)
  
#### Further Steps 
Read carefully and get a grasp of which tools to use for the next stpes 
- [Tagging](https://python.langchain.com/docs/tutorials/classification/), schema & function design([tool calling/binding](https://python.langchain.com/docs/concepts/tool_calling/))   
- [Langsmith Prompt Library](https://smith.langchain.com/hub)    
- [Agent Approaches: Plan-Execute Agents](https://blog.langchain.dev/planning-agents/), [structured chat](https://python.langchain.com/v0.1/docs/modules/agents/agent_types/structured_chat/), ReAct( [Paper: ReAct](https://arxiv.org/abs/2210.03629), [Blog: ReAct](https://dottxt-ai.github.io/outlines/latest/cookbook/react_agent/), [How to create a ReAct agent from scratch](https://langchain-ai.github.io/langgraph/how-tos/react-agent-from-scratch/) ), 
- Multi Agent Approaches: LangGraph([A Comprehensive Guide about LangGraph](https://www.ionio.ai/blog/a-comprehensive-guide-about-langgraph-code-included)), Autogen ( Simple Version )
- Complementary Tools: BertTopics   
- Implement in Kedro / Streamlit 

#### Optional
[outlines](https://github.com/dottxt-ai/outlines)

##### etc 
[Tool List](https://python.langchain.com/v0.1/docs/integrations/tools/)    
[Langchain setup](https://python.langchain.com/v0.1/docs/get_started/installation/)    
[Paper: Adaptive-RAG](https://arxiv.org/abs/2403.14403)
Reference :   


---
Collecting references :  


  - LangChain  
      [1] [WebScraping with Langchain](https://python.langchain.com/v0.1/docs/use_cases/web_scraping/)   
      [2] [Langchain Tool List](https://python.langchain.com/v0.1/docs/integrations/tools/)    
      [3] [Langchain Setup](https://python.langchain.com/v0.1/docs/get_started/installation/)     
      [4] [RAG](https://python.langchain.com/v0.1/docs/use_cases/question_answering/)  
      [5] [Tool Calling](https://python.langchain.com/docs/concepts/tool_calling/)  
      [6] [Langchain Comprehensive Book: Wiki Doc in Korean](https://wikidocs.net/262595)  
  
- Videos :  
  테디노트
    - RAG
        - [RAG 파이프라인 1 연습](https://www.youtube.com/watch?v=1scMJH93v0M&t=572s)
        - [RAG 동작과정 쉽게 이해하기(1) : Storing into vectorstore](https://www.youtube.com/watch?v=zybyszetEcE&t=992s)
        - [RAG 동작과정 쉽게 이해하기(2) : Retriever + Prompt](https://www.youtube.com/watch?v=Fxc2AzrxOP8&t=76s)

  모두 AI : [Multi Agent Explanation](https://www.youtube.com/watch?v=1n_Kui6B43Y)      
