+++
title = "Transformer Insights"
description = "Based on the paper, Attention Is All You Need."
date = 2025-03-28
draft = false

[taxonomies]
categories = ["technical"]
tags = ["nlp"]

[extra]
lang = "en"
toc = true
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

So, basically if you are new to this and don't have much experience in deep learning or maths, worry not. I got you.

You know how a neural netowrk works? It mostly plays with the weights and biases to make predictions. No? go find out... [chaper 1](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&ab_channel=3Blue1Brown)

![a basic neural network](/img/transformer-insights/neural-netv2.avif)

Let's learn about feed forward networks, and how it works differently from backpropagation...

Ever heard about the word "attention"?

The attention formula is given by, $ \text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V $.



