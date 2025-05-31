<h1 align="center">Text-Generation-Comparison</h1>

# 🤖 Text Generation Decoding Strategies with GPT-2
This project explores and compares different **text generation decoding strategies** using the GPT-2 language model.  
The goal is to better understand how methods like sampling and beam search influence the **diversity**, **fluency**, and **coherence** of generated text.

---

## 🧠 Decoding Strategies Explained
### 🔹 Top-k Sampling
Randomly selects the next word from the **top k most likely tokens**.  
✅ Generates diverse results  
⚠️ May lose coherence if k is too high

### 🔹 Top-p (Nucleus) Sampling
Samples from the **smallest set of tokens** whose cumulative probability ≥ *p*.  
✅ Balances randomness and relevance  
⚠️ Requires careful tuning of *p*

### 🔸 Temperature (🔥 Sampling Sharpness)
**Controls the confidence of the model when sampling.**

- Low values (e.g., `0.7`) → safer, more predictable outputs
- High values (e.g., `1.2`) → more diverse, creative, but potentially incoherent
- **Used in combination** with top-k and top-p

> Example: Top-p with temperature = 0.8 produces more grounded text than with temperature = 1.2

### 🔹 Beam Search
Generates multiple candidate sequences and selects the **most probable one overall**.  
✅ Often coherent and grammatical  
⚠️ May produce repetitive or dull text

### 🔹 Beam Search with N-gram Blocking
Like beam search, but blocks repeated **n-grams** (e.g. “the cat the cat”).  
✅ Reduces repetition  
⚠️ Slightly slower and more complex

📚 Resources:  
- [Hugging Face blog on decoding](https://huggingface.co/blog/how-to-generate)  
- [Top-k and Top-p Sampling Paper](https://arxiv.org/abs/1904.09751)

---

## 📋 Summary Comparison of Decoding Methods

| Method               | Diversity 🔀 | Fluency 🧠 | Repetition 🔁 | Speed ⚡ | Notes                                  |
|----------------------|--------------|------------|----------------|----------|----------------------------------------|
| Top-k Sampling       | High         | Medium     | Low            | Fast     | Needs `k` & `temperature` tuning           |
| Top-p Sampling       | High         | Medium     | Low–Medium     | Fast     | Adaptive; tune with `p` + `temperature`      |
| Beam Search          | Low          | High       | High           | Slow     | Safe but often repetitive              |
| Beam + N-gram Block  | Medium       | High       | Low            | Slow     | Improves beam search diversity         |

## 💡 When to Use What
✅ Use Top-p Sampling for creative tasks like story or poem generation

✅ Use Beam Search for structured output like summarization or question answering

✅ Use Top-k if you want fast generation with moderate randomness

✅ Use Beam + N-gram Blocking to reduce repetition in long-form generation


