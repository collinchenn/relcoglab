# relcoglab

A Python toolkit for computational cognitive science research, providing reusable tools for analyzing how language models represent meaning.

## Installation

```bash
pip install git+https://github.com/relcoglab/relcoglab.git
```

> **Note:** This package requires [TransformerLens](https://github.com/TransformerLensOrg/TransformerLens) for model activations, but does not install it automatically since it's a heavy ML dependency. Install it separately in your environment:
> ```bash
> pip install transformer-lens
> ```

## Quick Start

```python
from transformer_lens import HookedTransformer
from relcoglab import RSA

model = HookedTransformer.from_pretrained("gpt2-small")

rsa = RSA(model)
rsa_scores, rsa_pvalues = rsa.run("data/pairs.txt")
```

## Tools

| Module | Description |
|--------|-------------|
| `rsa`  | Representational Similarity Analysis — compares model similarity matrices against human similarity judgments using Pearson correlation |

## Data Format

Similarity files should have one pair per line:

```
word1#meta    word2#meta    score
```

Scores are expected in the range [1, 10] and are normalized to [0, 1] internally.

## Project Structure

```
src/relcoglab/
├── __init__.py
├── rsa.py
└── parse.py
```
