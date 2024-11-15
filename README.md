# NLP Competitive Market Analysis Kedro Project
This porject is to analyze markets in different domains. Since the supervisor is familiar with the insurance domain, this project will be focused on the insurance domain. However there is many potentials for this project to be extended to.  

#### General workflow of webscraping with Langchain
- Search: Query to url (e.g., using GoogleSearchAPIWrapper) 
- Loading: Url to HTML (e.g., using AsyncHtmlLoader, AsyncChromiumLoader, etc).
    - Document & Image loaders ( Currently only text )
- Transforming: HTML to formatted text (e.g., using HTML2Text or Beautiful Soup).

[Tool List](https://python.langchain.com/v0.1/docs/integrations/tools/)  
[Tool setup](https://python.langchain.com/v0.1/docs/get_started/installation/)   

#### Next Steps : Need a discussion.. 
- Split documents
    - ***Which splitter? ( Not discussed yet )***
    - Langchain [Splitter Explanation](https://python.langchain.com/v0.1/docs/modules/data_connection/document_transformers/)  
    - Langchain [Splitter Tool](https://js.langchain.com/v0.1/docs/modules/data_connection/document_transformers/)
    - [Chunk visualization](https://chunkviz.up.railway.app)
- Store data in the vector database 
    - ***Which Vectorstore? ( Not discussed yet ! )***
- Agent Approaches
    - Retrieve
        - [Retrievers](https://python.langchain.com/v0.1/docs/modules/data_connection/retrievers/)
    - Schema, Function design ( Tool Calling )  
        - How do we design the schema? ( need a resarch )
        - [Langsmith Prompt Library](https://smith.langchain.com/hub)
    - Explore Agent Approach ( Langchain )
- Evaluation 
- Explore Multi Agent Approaches
    - LangGraph
    - Autogen ( Simple Version )
- Complementary Tools
    - BertTopics 

- Implement in Kedro / streamlit 


#### Not sure..
- Output Format ?? ; [video ( 28:30 )](https://www.youtube.com/watch?app=desktop&v=NHeOMxa7VgU) ?? 
- Agents : Document search, online search -> comparison ? or just based on the documents? 

#### Required for me
- Explore RAG architecture : [RAG](https://python.langchain.com/v0.1/docs/use_cases/question_answering/)

Reference :   
- Documents :
      - LangChain
          - [1] [WebScraping with Langchain](https://python.langchain.com/v0.1/docs/use_cases/web_scraping/)   
          - [2] [Langchain Tool List](https://python.langchain.com/v0.1/docs/integrations/tools/)    
          - [3] [Langchain Setup](https://python.langchain.com/v0.1/docs/get_started/installation/)     
          - [4] [RAG](https://python.langchain.com/v0.1/docs/use_cases/question_answering/)  
          - [5] [Tool Calling](https://python.langchain.com/docs/concepts/tool_calling/)  
          - [6] [Langchain Comprehensive Book: Wiki Doc in Korean](https://wikidocs.net/262595)  
  
- Videos :  
  테디노트
    - RAG
        - [RAG 파이프라인 1 연습](https://www.youtube.com/watch?v=1scMJH93v0M&t=572s)
        - [RAG 동작과정 쉽게 이해하기(1) : Storing into vectorstore](https://www.youtube.com/watch?v=zybyszetEcE&t=992s)
        - [RAG 동작과정 쉽게 이해하기(2) : Retriever + Prompt](https://www.youtube.com/watch?v=Fxc2AzrxOP8&t=76s)

  모두 AI : [Multi Agent Explanation](https://www.youtube.com/watch?v=1n_Kui6B43Y)      
