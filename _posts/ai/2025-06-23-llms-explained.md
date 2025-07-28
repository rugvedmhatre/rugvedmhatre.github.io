---
title: "LLMs Explained - From Tokenization to Transformers"
date: 2025-06-23T18:30:00+05:30
last_modified_at: 2025-06-23T18:30:00+05:30
toc: true
toc_label: Contents
category: ai
excerpt: Demystifying LLMs step by step - starting with tokenization and ending with the power of transformers
seo_title: LLMs Explained - From Tokenization to Transformers
seo_description: Demystifying LLMs step by step
---

Large Language Models (LLMs) like OpenAI's ChatGPT, Google's Gemini, and Meta's Llama are 
transforming how we search, write, code and even think. But how do these models work? If you've 
ever wondered how a machine can write essays, summarize texts, or solve coding problems, this post
is for you.

Let's demystify LLMs - step by step - starting with tokeninzation and ending with the power of 
transformers.

## What are LLMs?

At their core, LLMs are advanced text prediction engines. They analyze massive amounts of text
data and learn to predict the next word (or token) in a sequence. Over time, with enough data
and training, they start generating suprisingly coherent language, answering questions, and even
reasoning.

But how does it all work under the hood?

## Tokenization - Turning Text into Numbers

Computer's don't understand words; they understand numbers. So the first step is to break text
into smaller pieces called tokens. These might be words, subwords or even characters. 

But not all tokenizers are the same. In modern LLMs like GPT, we often use **Byte Pair Encoding (BPE)** or 
**SentencePiece**, which strike a balance between vocabulary size and representational flexibility.

Let’s take the word “unbelievable”.
- A character-based tokenizer would break it into: ["u", "n", "b", "e", "l", "i", "e", "v", "a", "b", "l", "e"]
- A word-based tokenizer would treat it as: ["unbelievable"]
- A BPE tokenizer might segment it like: ["un", "believ", "able"]

BPE wins here—it avoids both long sequences (like character-level) and out-of-vocabulary errors 
(which plague word-level tokenizers). It builds tokens based on frequency in the corpus, 
learning to represent recurring chunks efficiently.

From a developer’s lens: tokenization directly impacts model input size, training stability, 
and even downstream performance. Models fail silently just because of mismatched tokenizer versions 
between training and inference.

## Embeddings - Giving Meaning to Tokens

Once we’ve broken text into tokens, the next step is to convert them into something the model can operate on: vectors.

Each token is mapped to a high-dimensional vector—typically 768 dimensions or more depending on model size. These vectors are learned during training and capture semantic relationships. For instance:
 - The vector for "king" – "man" + "woman" ≈ "queen"
 - "Paris" is closer to "France" than to "Canada"

We often treat these embeddings as a learned dictionary of meaning. In practice, these embedding tables can be gigabytes in size.

## Positional Encoding – Teaching Order to Models

Transformers, unlike RNNs, don’t process tokens sequentially. That’s both a blessing (more parallelism!) and a curse—because without sequence, the model has no sense of word order.

Enter positional encoding.

The idea is simple but elegant: we add a position-specific signal to each token embedding, so the model knows, “This token is the 3rd word,” and so on.

There are two common ways to encode position:
- Sinusoidal functions (used in the original Transformer paper)
- Learned positional embeddings (used in GPT-style models)

Positional encoding is what makes the sentence “dog bites man” different from “man bites dog”.

## The Transformer

Now we’re ready for the core architecture: the Transformer.

Transformers are made of two main components:
1.	Self-Attention
2.	Feedforward Networks

Let’s break down self-attention, because it’s the beating heart of LLMs.

### Self-Attention

Imagine reading the sentence:
“The animal didn’t cross the road because it was too tired.”

What does “it” refer to? The model has to decide whether “it” refers to “animal” or “road.” Self-attention helps here: for each word, the model looks at all other words and weighs their relevance.

Mathematically:
- Each token is projected into three vectors: Query (Q), Key (K), and Value (V)
- Attention scores are computed using dot products between Q and K
- These scores are normalized (via softmax) and used to weight the V vectors

So each token representation is contextualized—it becomes aware of its surroundings. 

This mechanism is parallelizable (unlike RNNs), making training fast and scalable. During my [research project](https://github.com/rugvedmhatre/Efficient-ViT) on optimizing sequence models, we experimented with fused attention kernels (FlashAttention) that optimized our training times by 20%. *(Trust me, the hardware bottlenecks are real.)*

### Multi-Head Attention

To capture different types of relationships (e.g., syntactic vs. semantic), we don’t just compute attention once—we do it multiple times in parallel. That’s multi-head attention.

Each “head” learns to focus on different aspects of the sequence. One might learn grammar rules, another might model world knowledge.

After attention, we have feedforward layers, layer norm, and residual connections—all critical for depth, stability, and training convergence.

## Stacking It Up – Training the Model

A full LLM like GPT-3 has 96 transformer layers, each with attention and feedforward blocks. And it’s trained on hundreds of billions of tokens. The training objective is simple yet powerful: predict the next token.

This is called causal language modeling. Given:

“The capital of France is”

The model learns to predict “Paris.” That’s it. But over billions of examples, the model learns syntax, facts, reasoning patterns, and more.

Of course, this requires huge infrastructure. We’re talking weeks of training on thousands of GPUs.

## Inference – Making the Model Talk

Once trained, we can use the LLM to generate text by feeding a prompt and sampling from the output distribution. There are multiple sampling strategies:
- Greedy decoding: Always pick the most likely next token (fast but dull)
- Top-k or Top-p sampling: Introduce randomness for more diverse outputs
- Beam search: Keep multiple candidate sequences (used in translation)

In practice, decoding quality is heavily influenced by prompt design and temperature settings. I’ve seen models flip tone, verbosity, or logic just by tweaking the prompt slightly—prompt engineering is real and powerful.

## Final Thoughts

LLMs may seem like magic, but they’re built on solid engineering and mathematics. From tokenization to attention, each step plays a vital role in giving these models their power.

As someone who teaches this stuff and builds with it, I can tell you: understanding the internals isn’t just intellectually satisfying—it makes you better at using these models, debugging them, and building on top of them.