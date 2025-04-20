+++
title = "Basics of RAG"
description = "About the advantages of RAG above fine-tuning."
date = 2025-04-05
draft = false

[taxonomies]
categories = ["technical"]
tags = ["ai"]

[extra]
lang = "en"
toc = true
comment = false
copy = true
outdate_alert = false
outdate_alert_days = 120
math = true
mermaid = false
featured = false
reaction = false
+++

Behold! As a part of my *minor project*, I have decided to go with this.

Well, RAG stands for *Retrieval Augmental Generation.*

And at its core, it basically is a technique that enables [generative artificial intelligence (Gen AI)](https://en.wikipedia.org/wiki/Generative_artificial_intelligence) models to retrieve and imcorporate new information. It modifies interactions with [LLMs](https://en.wikipedia.org/wiki/Large_language_model) so that the model responds to user queries with reference to a specified set of documents, using this information to supplement information from its pre-existing training data.

As LLMs often hallucinate or become outdated, so RAG helps.

{{ figure(src="/img/rag-101/rag2.avif", alt="rag pipeline", caption="RAG Pipeline") }}

*Fine-tuning vs. RAG* comes down to internalization vs. real-time grounding. Fine-tuning updates a model’s weights with task-specific data, useful for static tasks requiring deep reasoning. RAG, on the other hand, retrieves updated content without retraining, offering lower cost and more flexibility. It’s ideal for dynamic, fact-heavy applications, while fine-tuning is better for logic-centric or controlled tasks.

Technically, RAG works in stages: *Indexing* involves converting reference documents into [vector embeddings of words](https://en.wikipedia.org/wiki/Word_embedding), which are stored in a database for fast retrieval. *Retrieval* follows, where a query triggers the retrieval of the most relevant documents from the database. In *Augmentation*, these retrieved documents are combined with the user’s query through prompt engineering, enriching the context. Finally, *Generation* occurs, where the LLM generates a response using both the augmented input and its internal training data, producing a more accurate, context-aware answer.

RAG is being enhanced with smarter chunking, hybrid retrieval (dense + sparse), and structured knowledge via [GraphRAG](https://medium.com/@zilliz_learn/graphrag-explained-enhancing-rag-with-knowledge-graphs-3312065f99e1), which uses [knowledge graphs](https://en.wikipedia.org/wiki/Knowledge_graph#:~:text=A%20knowledge%20graph%20formally%20represents,allowing%20queries%20requesting%20explicit%20knowledge.) instead of raw text for more precise retrieval. These advances make RAG more *interpretable, efficient, and domain-adaptable.*

Enough with the theory. Implementation is next.

See you soon.
