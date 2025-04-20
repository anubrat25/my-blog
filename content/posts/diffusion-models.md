+++
title = "Diffusion Models, Simply"
description = "Explaining the working of Diffusion Models"
date = 2025-04-20
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

Last night, I saw my friend drawing some anime girl while he had *"Diffusion Models"* opened on his laptop. And yes, that's enough motivation.

Basically, diffusion models are [generative models](https://en.wikipedia.org/wiki/Generative_model). As in *discriminative vs. generative?* Right? [Check out!](https://ai.stanford.edu/~ang/papers/nips01-discriminativegenerative.pdf)

These models learns to reverse the gradual corruption of data by any [noise](https://en.wikipedia.org/wiki/Noisy_data), which then consists of two main parts: *the Forward Process*, where the original data is progressively corrupted by adding noise over time, and *the Reverse Process*, where the model learns to denoise the corrupted data step-by-step, eventually recovering the original data or generating new, similar data from pure noise. The model is trained to predict the noise added at each timestep, and once trained, it can generate new data by progressively denoising random noise.

# Working Mechanism

*The forward process* is where we progressively add noise to the data. If we start with a clean image $\( \mathbf{x}_0 \)$, we apply noise at each timestep $\( t \)$. After several steps, the image becomes pure noise. The noise at each step is Gaussian noise, and the level of noise increases over time.

$$\mathbf{x}_t = \bar{\alpha}_t \mathbf{x}_0 + \sqrt{1 - \bar{\alpha}_t} \boldsymbol{\epsilon}$$

where, $\( \mathbf{x}_0 \)$ is the clean image, $\( \mathbf{x}_t \)$ is the noisy image at timestep \( t \) and $\( \boldsymbol{\epsilon} \)$ is random noise from a Gaussian distribution.

After the forward process, we want to recover the original data. This is where the *reverse process* comes into play. We train a neural network to learn how to predict the noise $\( \boldsymbol{\epsilon} \)$ that was added at each step.

$$
p_\theta(x_{t-1} \mid x_t) = \mathcal{N}(x_{t-1}; \mu_\theta(x_t, t), \sigma_t^2 I)
$$

where, $\mu_\theta(x_t, t)$ is the model’s predicted mean (the denoised image at step $t-1$) and $\sigma_t^2 I$ is the variance, often a fixed schedule.

By repeatedly applying this reverse process, starting with pure noise, the model can generate new data.

The loss function used to train the model is typically the Mean Squared Error (MSE) between the model's predicted noise and the true noise added during the forward process:

$$
L = \mathbb{E} [ (\epsilon - \epsilon_\theta)^2 ]
$$

where, $\epsilon$ is the true noise added to the data and $\epsilon_\theta$ is the noise predicted by the model.

{{ figure(src="/img/diffusion-models/denoising.avif", alt="denoising in diffusion models", caption="The denoising process used by Stable Diffusion") }}

After training, the model can generate new data by starting with pure noise and applying the reverse process. The model progressively denoises the image step-by-step until it has generated a new, clean image.

Stable Diffusion is a *latent diffusion model*, which means it operates in a compressed latent space rather than directly on high-dimensional image space. This makes the process much faster and less computationally expensive. By using a pre-trained [variational autoencoder (VAE)](https://en.wikipedia.org/wiki/Variational_autoencoder) to compress images into latent vectors, Stable Diffusion can generate high-resolution images in just a few seconds with reasonable GPU power.

Diffusion models are known for their *training stability*. Unlike [GANs](https://en.wikipedia.org/wiki/Generative_adversarial_network), where the generator and discriminator need to be carefully balanced, diffusion models are less prone to [mode collapse](https://en.wikipedia.org/wiki/Mode_collapse) and other training instabilities.

Recent advancements have made diffusion models more *computationally efficient*, with models like [LDM (Latent Diffusion Models)](https://en.wikipedia.org/wiki/Latent_diffusion_model) and [Score-based Model](https://fanpu.io/blog/2023/score-based-diffusion-models/) *using lower-resolution latent spaces*, reducing memory and computation time while maintaining high-quality outputs.

But that's a discussion for another blog.

See you soon.
