* agent flows: https://cookbook.openai.com/examples/how_to_call_functions_for_knowledge_retrieval
* highlight text, summarise
* exploding window for context
* retrieve and rerank as in: https://github.com/theogbrand/relari-examples
* code interpreter:
- minimum with exec() only https://github.com/theogbrand/min-code_interpreter
- Jupyter kernel https://github.com/theogbrand/code-interpreter-oss?tab=readme-ov-file
  Cite Sources by generation: https://docs.anthropic.com/claude/page/cite-your-sources
* Chain of Density better summaries: https://python.useinstructor.com/blog/2023/11/05/chain-of-density/
* try Cohere Embeddings + Reranker + Command (LLM)
* Domain-specific Embeddings Finetune (refer to BAAI + FlagOpen/FlagEmbedding[https://github.com/FlagOpen/FlagEmbedding/blob/master/FlagEmbedding/baai_general_embedding/README.md])
* Custom Tokenizer (from scratch like SentencePiece or possibly extending c100k GPT4)