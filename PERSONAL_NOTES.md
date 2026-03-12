# Personal Notes - LangChain

Forked for building RAG pipelines and LLM apps at Indosat Ooredoo.

## Patterns I Use

### Basic RAG pipeline
```python
from langchain.chains import RetrievalQA
from langchain_openai import AzureChatOpenAI
from langchain_community.vectorstores import Chroma

llm = AzureChatOpenAI(deployment_name="gpt-4", temperature=0)
qa_chain = RetrievalQA.from_chain_type(llm=llm, retriever=vectorstore.as_retriever())
```

### Agent with tools
```python
from langchain.agents import AgentExecutor, create_openai_tools_agent
agent = create_openai_tools_agent(llm, tools, prompt)
executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

## Notes
- AzureChatOpenAI needs AZURE_OPENAI_ENDPOINT and AZURE_OPENAI_API_KEY in env
- Use langgraph for stateful multi-step agents
- Chroma works best for local dev, migrate to Azure AI Search for prod
