# Corrective RAG (CRAG)
Corrective-RAG (CRAG) is a strategy for RAG that incorporates self-reflection / self-grading on retrieved documents.

In the paper <a href="https://arxiv.org/pdf/2401.15884.pdf">here</a>, a few steps are taken:

- If at least one document exceeds the threshold for relevance, then it proceeds to generation
- Before generation, it performns knowledge refinement
- This partitions the document into "knowledge strips"
- It grades each strip, and filters our irrelevant ones
- If all documents fall below the relevance threshold or if the grader is unsure, then the framework seeks an additional datasource
- It will use web search to supplement retrieval

We will implement some of these ideas from scratch using <a href="https://langchain-ai.github.io/langgraph/">LangGraph</a>:

- Let's skip the knowledge refinement phase as a first pass. This can be added back as a node, if desired.
- If any documents are irrelevant, let's opt to supplement retrieval with web search.
- We'll use <a href="https://python.langchain.com/v0.2/docs/integrations/tools/tavily_search/">Tavily Search</a> for web search.
- Let's use query re-writing to optimize the query for web search.



<br>![image](https://github.com/AshishCodeCraft26/Advance-RAG/assets/135592934/e703ae89-7c04-4656-9e55-32b560e41e84)</br>
