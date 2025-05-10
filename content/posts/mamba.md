+++
title = "Mamba Nets"
description = "An alternative to transformers?"
date = 2025-04-27
draft = false

[taxonomies]
categories = ["technical"]
tags = ["ai"]

[extra]
lang = "en"
toc = false
comment = false
copy = true
outdate_alert = false
outdate_alert_days = 120
math = true
mermaid = false
featured = false
reaction = false
+++

Deep Mamba is a new type of neural network architecture designed to handle sequential data more efficiently than [transformers](https://en.wikipedia.org/wiki/Transformer_(deep_learning_architecture)). At its core, it builds on the idea of [Structured State Space Models (SSMs)](https://huggingface.co/blog/lbourdois/get-on-the-ssm-train), which model sequences by maintaining a continuous hidden state that evolves over time. Unlike transformers that use [self-attention](https://en.wikipedia.org/wiki/Attention_(machine_learning)) to look at all tokens at once, Mamba processes inputs in a streaming, step-by-step fashion, making it ideal for long sequences.

The key innovation in Deep Mamba is something called *selective state space modeling*. This means that instead of blindly updating the hidden state with every input token, the model learns to filter and control which information is important at each step. This is done through dynamically learned [convolution](https://en.wikipedia.org/wiki/Convolution) kernels and gating mechanisms, which selectively blend new input with the current state. This control mechanism gives Mamba the ability to focus on the most relevant features in a sequence without the quadratic cost of attention.

{{ figure(src="/img/mamba-nets/transformers.avif", alt="the transformers block", caption="The Transformer Block") }}

{{ figure(src="/img/mamba-nets/mamba.avif", alt="mamba block", caption="The Mamba Block") }}

From a computational standpoint, Deep Mamba is highly efficient. Its design allows for *linear-time complexity* in sequence length, which is a big improvement over the *quadratic time* of transformers. This means it can handle longer sequences with less memory, making it more scalable for tasks like language modeling, audio processing, or time-series prediction. Moreover, because it processes data sequentially, it’s also better suited for real-time inference tasks.

| Feature       | Transformer    | Mamba     |
|-------------------|--------------------|---------------|
| Architecture      | Attention-based    | SSM-based     |
| Complexity        | High               | Lower         |
| Inference speed   | O(n)               | O(1)          |
| Training speed    | O(n²)              | O(n)          |

One of the most exciting developments in this space is [Jamba](https://arxiv.org/html/2403.19887v1), a hybrid model from AI21 Labs that combines transformer and Mamba-style layers. With 52 billion parameters and a 256,000-token context window, Jamba stands as the largest and most powerful Mamba-variant to date.

But that's a story for another day.

See you soon.
