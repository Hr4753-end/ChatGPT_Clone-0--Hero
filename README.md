# ChatGPT Clone – Zero to Hero 🤖

A small GPT (Generative Pre-trained Transformer) built **from scratch in Python and PyTorch**, following Andrej Karpathy's lecture *"Let's build GPT: from scratch, in code, spelled out."*

The goal of this repo is learning: understand every part of the Transformer that powers ChatGPT by writing it line by line, then train it on a small dataset and generate text.

> **Reference video:** [Let's build GPT: from scratch, in code, spelled out](https://youtu.be/kCc8FmEb1nY)

---

## What this project does

- Loads a text dataset (Tiny Shakespeare) and converts characters into integer tokens
- Builds a decoder-only Transformer language model
- Trains the model to predict the next character
- Generates new text, one character at a time, in the style of the training data

This is a character-level language model, the same core idea behind ChatGPT, only much smaller. It is **not** a chat app with a UI or a pretrained assistant.

---

## Concepts covered

| Topic | What you learn |
|---|---|
| Tokenization | Turning text into integer sequences (character-level encode/decode) |
| Bigram baseline | A simple first language model and how to generate from it |
| Self-attention | Query, key and value vectors, and how tokens "communicate" |
| Masked attention | Using a lower-triangular mask so tokens only see the past |
| Matrix-multiplication trick | Efficient weighted averaging of previous tokens |
| Scaled attention | Why attention scores are scaled to keep variance stable |
| Multi-head attention | Several attention heads in parallel, concatenated |
| Feed-forward layers | Letting each token process what it gathered |
| Residual connections | Skip connections that make deep networks easier to optimize |
| Layer normalization | Stabilizing training |
| Dropout | Regularization to reduce overfitting |
| Scaling up | Tuning hyperparameters for a larger model |
| Pre-training vs. fine-tuning | How GPT becomes ChatGPT (conceptual overview) |

---

## Tech stack

- Python 3.9+
- PyTorch
- Jupyter Notebook / Google Colab (optional)

---

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/Hr4753-end/ChatGPT_Clone-0--Hero.git
cd ChatGPT_Clone-0--Hero
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install torch
```

### 4. Get the dataset

Download Tiny Shakespeare and save it as `input.txt` in the project folder:

```bash
wget https://raw.githubusercontent.com/karpathy/char-rnn/master/data/tinyshakespeare/input.txt
```

### 5. Run

```bash
python <your_script_name>.py
```

*(Replace `<your_script_name>.py` with the main file or notebook in this repo.)*

---

## Project structure

```
ChatGPT_Clone-0--Hero/
├── input.txt          # Training dataset (Tiny Shakespeare)
├── <main file>        # Model, training loop and text generation
└── README.md
```

*(Update this section to match your actual files.)*

---

## How the model works

```
Input characters
      ↓
Token + position embeddings
      ↓
┌─────────────────────────────┐
│  Transformer Block (× N)    │
│   • LayerNorm               │
│   • Multi-head self-attention
│   • Residual connection     │
│   • LayerNorm               │
│   • Feed-forward network    │
│   • Residual connection     │
└─────────────────────────────┘
      ↓
LayerNorm → Linear layer
      ↓
Probabilities for the next character
```

---

## Hyperparameters

Edit these at the top of the script to experiment:

| Parameter | Meaning |
|---|---|
| `batch_size` | Sequences processed in parallel |
| `block_size` | Maximum context length |
| `n_embd` | Embedding dimension |
| `n_head` | Number of attention heads |
| `n_layer` | Number of Transformer blocks |
| `dropout` | Dropout probability |
| `learning_rate` | Optimizer step size |
| `max_iters` | Training steps |

Training is much faster on a GPU (for example, a free Google Colab GPU).

---

## Example output

After training, the model generates text that looks like Shakespeare, though it is not always meaningful:

```
<paste a sample of your model's generated text here>
```

---

## Ideas for improvement

- [ ] Train on a different dataset (your own notes, code, or a language of your choice)
- [ ] Switch from characters to a subword tokenizer (BPE)
- [ ] Add a simple chat interface with Gradio or Streamlit
- [ ] Save and load model checkpoints
- [ ] Plot training and validation loss

---

## Acknowledgements

- [Andrej Karpathy](https://karpathy.ai/) for the lecture and the *Neural Networks: Zero to Hero* series
- *Attention Is All You Need* (Vaswani et al., 2017), the original Transformer paper
- Tiny Shakespeare dataset from Karpathy's `char-rnn`

---

## Author

**Master H**, Computer Science student, IILM University
GitHub: [@Hr4753-end](https://github.com/Hr4753-end)

---

## License

Add a license of your choice (MIT is common for learning projects).
