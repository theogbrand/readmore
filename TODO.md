- edit core logic to fetch 10 Docs with ANN SS and LLM to "needle in Haystack" answer

- agent flows:

  - https://cookbook.openai.com/examples/how_to_call_functions_for_knowledge_retrieval
  - start with engineered flows for getting "gist" of paper
    - Prompt Chaining
    - Tree of Thoughts (PanelGPT Prompt) + Reflexion

- highlight text, summarise
- exploding window for context
- retrieve and rerank as in: https://github.com/theogbrand/relari-examples

- code interpreter:

* minimum with exec() only https://github.com/theogbrand/min-code_interpreter
* Jupyter kernel https://github.com/theogbrand/code-interpreter-oss?tab=readme-ov-file
  Cite Sources by generation: https://docs.anthropic.com/claude/page/cite-your-sources

- Chain of Density better summaries: https://python.useinstructor.com/blog/2023/11/05/chain-of-density/
- try Cohere Embeddings + Reranker + Command (LLM)
- Domain-specific Embeddings Finetune (refer to BAAI + FlagOpen/FlagEmbedding[https://github.com/FlagOpen/FlagEmbedding/blob/master/FlagEmbedding/baai_general_embedding/README.md])
- Custom Tokenizer (from scratch like SentencePiece or possibly extending c100k GPT4)

# Summarisation TODO:

- Parsing sections with HTML
- "thinking" part to enable 2 modes: retrieve for qna or summarise for qna (different prompt)
  - framing as 2 tool (vector/summarise tool) to enable 2 modes
  - [https://docs.llamaindex.ai/en/stable/examples/query_engine/recursive_retriever_agents/]
- BRV [https://github.com/gkamradt/langchain-tutorials/blob/main/data_generation/5%20Levels%20Of%20Summarization%20-%20Novice%20To%20Expert.ipynb]
- Clustering [https://github.com/theogbrand/llm_summary_medium]
- Agentic Clustering (proposition method) to get semantic Chunks, then summarise (with multi-vector) on those

# Retrieval (for QnA) TODO:

## Note: optimise signal:noise ratio (smaller chunks have higher likelihood of being matched semantically!!)

1. MultiQuery -> gen 3 queries from original query to return more holistic docs
2. Agentic Chunking -> Proposition method [https://python.langchain.com/docs/templates/propositional-retrieval] with PDF(Doc) for Text splitting ONLY + Use AgenticChunker to determine a "semantic chunk" instead of cluster chunk (more explicit than clustering method) ==> powerful when chunk summary can be updated when new Proposition is added to it
3. Multi-Vector -> when storing chunk, store along with summary of it. VSS on summary, return raw text. (hence multi-vector)
4. for Hypothetical Questions, when Messages stored as KB, generate hypothetical qns using LLM as vector to search on, then return actual KB message as multi-vector VSS
5. Parent Document Retriever (HierarchicalNodeParser in LI) or like exploding window method
6. (maybe?) Graph based retrieval
