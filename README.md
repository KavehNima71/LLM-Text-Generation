<h1 align="center">LLM-Text-Generation</h1>

# **1. Top-k Sampling with Temperature:**
**Overview**

Fan et. al (2018) introduced a simple, but very powerful sampling scheme, called Top-K sampling. In Top-K sampling, the K most likely next words are filtered and the probability mass is redistributed among only those K next words. GPT2 adopted this sampling scheme, which was one of the reasons for its success in story generation.

Top-k sampling with temperature is a powerful text generation technique that combines two key methods for controlling output quality and diversity:

- Top-k filtering: Limits selection to only the k most probable next tokens
- Temperature scaling: Modifies the probability distribution to control randomness

This approach is widely used in modern language models to generate more coherent and contextually appropriate text compared to simple greedy decoding.

**How It Works:**
1. Top-k Sampling:
  - The model first predicts the probability distribution over all possible next tokens (logits)
  - Only the top k most probable tokens are kept (others are set to zero probability)
  - Next token is sampled from this truncated distribution

2. Temperature Scaling:
- Before applying softmax, logits are divided by temperature T

- Temperature effects:
    - T < 1.0: Sharpens distribution (favors high-probability tokens)
    - T = 1.0: No change to original distribution
    - T > 1.0: Flattens distribution (increases randomness)

**Why This Matters**

Top-k with temperature provides better control than basic sampling methods:

- Prevents low-probability nonsense tokens (via top-k)
- Allows tuning of "creativity dial" (via temperature)
- More reliable than pure random sampling
- More flexible than greedy decoding

For most applications, we recommend starting with top_k=40-60 and temperature=0.7-1.0 and adjusting based on your specific needs.

   
