+++
title = "Transformer Insights"
description = "Based on the paper, Attention Is All You Need."
date = 2025-03-31
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
mermaid = true
featured = false
reaction = false
+++

Okay.

So, basically if you are new to this and don't have much experience in deep learning or math, worry not. I got you.

You know how a neural network works? It mostly plays with the weights and biases to make predictions. No? Go find out... [Intro](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&ab_channel=3Blue1Brown)

{{ figure(src="/img/transformer-insights/neural-netv2.avif", alt="a basic neural network", caption="A basic neural network") }}

Let's learn more about feedforward networks, and how they work differently from backpropagation...

Well, backprop is like a good kid, who learns from its mistakes. When a neural net starts by making a prediction and calculating how far off it is using a [loss function](https://en.wikipedia.org/wiki/Loss_function#:~:text=In%20mathematical%20optimization%20and%20decision,cost%22%20associated%20with%20the%20event.). Then, using [gradient descent](https://www.youtube.com/watch?v=IHZwWFHWa-w&ab_channel=3Blue1Brown), it traces the error backward through the network, layer by layer, adjusting the weights based on how much each contributed to the mistake. This process, powered by the chain rule, helps the network improve step by step until it makes accurate predictions. [Watch this!](https://www.youtube.com/watch?v=Ilg3gGewQ5U&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&index=3&ab_channel=3Blue1Brown)

{{ figure(src="/img/transformer-insights/backprop2.avif", alt="chain rule", caption="Chain rule") }}

Why limit myself to human friends when I have ChatGPT that remembers my interests, never cancels plans, and can debug my code at 3 AM?

But have you ever thought how it works? These are known as *Large Language Models* or simply, LLMs.

Earlier, sequence-based tasks were done using [RNNs](https://en.wikipedia.org/wiki/Recurrent_neural_network), [LSTMs](https://en.m.wikipedia.org/wiki/Long_short-term_memory) and [GRUs](https://en.wikipedia.org/wiki/Gated_recurrent_unit). But it wasn't enough as they had problems. Problems such as [vanishing gradients](https://en.wikipedia.org/wiki/Vanishing_gradient_problem), slow training, poor handling of long range dependencies or tokens.

But in 2017, it changed.

Ever heard about the word "attention"? Yes. It's mostly the same thing that your girlfriend wants.

A group of researchers at Google came up with a paper named [*Attention Is All You Need*](/img/transformer-insights/aiayn.pdf), introducing transformers, which then replaced recurrence with [self-attention](https://en.wikipedia.org/wiki/Attention_(machine_learning)), allowing models to process entire sequences in parallel. This made training much faster, eliminated vanishing gradient issues, and improved handling of long-range dependencies. Unlike RNNs and LSTMs, Transformers scale well with data and compute, enabling breakthroughs in NLP and powering models like [GPT](https://en.wikipedia.org/wiki/Generative_pre-trained_transformer) and [BERT](https://en.wikipedia.org/wiki/BERT_(language_model)). Their ability to generalize across tasks with minimal fine-tuning further is what dominates modern AI.

# Breaking It Down

Self-attention helps a model focus on the most important words in a sentence, no matter where they appear. Instead of reading words one by one like older models, transformers look at the whole sentence at once and decide which words relate most to each other. For example, in the sentence *"The cat, which was sitting on the mat, was purring because it was happy"*, the word *"it"* refers to *"cat"*. Self-attention helps [machine translation](https://en.wikipedia.org/wiki/Machine_translation) and [natural language generation](https://en.wikipedia.org/wiki/Natural_language_generation).

<p align="center"> $ \text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V $ </p>

$Q$ (Query), $K$ (Key), and $V$ (Value) transform the input to determine word attention. The scaling factor $d_k$ stabilizes gradients, while softmax normalizes attention scores to ensure they sum to 1.

Transformers are built using layers that process information efficiently. The key parts include self-attention, which helps the model understand relationships between words, and feedforward layers, which refine the output. They also use [positional encoding](https://medium.com/@hunter-j-phillips/positional-encoding-7a93db4109e6) to remember the order of words, since they don’t process text sequentially like RNNs. By stacking multiple layers of these components, transformers can handle complex language tasks, making them much more powerful than older models.

{{ figure(src="/img/transformer-insights/ta2.avif", alt="transformer architecture", caption="(a) One encoder layer and one decoder layer. (b) Two encoder layers and two decoder layers.") }}

And because GPTs need a job, not just vibes, we fine-tune them, which basically means training it on a specific task with new data. Instead of training a model from scratch, fine-tuning allows a model to quickly adapt to new domains like medical diagnosis, legal analysis, or chatbots, just to save and computational power.

But are they perfect? No... transformers have some major challenges. They require a lot of computing power, making them expensive to train and run. They also struggle with bias, often reflecting the flaws in the data they were trained on. Additionally, they sometimes generate hallucinations, confident but incorrect answers, making them unreliable in certain situations. 

Lastly, while transformers lead today, the world's moving fast, and we get to see new innovations almost every day. For example, [Mixture of Experts (MoE)](https://en.wikipedia.org/wiki/Mixture_of_experts) reduces computation by activating only needed parts, while [Retrieval Augmented Generation (RAG)](https://en.wikipedia.org/wiki/Retrieval-augmented_generation) integrates real-world data.

But that's a discussion for another blog.

See you soon.
