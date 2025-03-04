# Context-Sensitive Spelling Correction

This project implements a **context-sensitive spelling corrector** using an **N-gram language model** combined with **semantic similarity** and **keyboard-aware edit distance**. The goal is to correct spelling mistakes in text while considering the surrounding context, ensuring that corrections are both contextually and semantically appropriate.

## Features

- **N-gram Language Model**: Uses bigrams and fivegrams to capture contextual information for accurate corrections.
- **Edit Distance with Keyboard Neighbors**: Accounts for common typing errors by assigning lower costs to substitutions involving adjacent keys on a QWERTY keyboard.
- **Semantic Similarity with SpaCy Embeddings**: Incorporates SpaCy word embeddings to ensure corrections are semantically coherent.
- **Candidate Generation and Ranking**: Generates and ranks candidate corrections based on n-gram frequency, edit distance, and semantic similarity.
- **Efficiency Improvements**: Utilizes GPU acceleration with PyTorch for faster computations and efficient memory management.

## How It Works

1. **N-gram Data Loading**: The model loads n-gram frequency data from `bigrams.txt` and `fivegrams.txt` to understand word co-occurrences.
2. **Edit Distance Calculation**: A modified Levenshtein distance algorithm is used to account for keyboard typos and common misspellings.
3. **Candidate Generation**: For each misspelled word, the model generates potential corrections by considering words within an edit distance of 2.
4. **Ranking Corrections**: Corrections are ranked based on a combination of n-gram frequency, edit distance penalty, and semantic similarity.
5. **Context-Aware Correction**: The model selects the best correction by considering the surrounding words and semantic coherence.

## Usage

To use the spelling corrector, simply input a sentence with potential spelling errors, and the model will output the corrected sentence.

```python
sentence = "dking species"
corrected_sentence = correct_sentence(sentence, dictionary)
print("Original:", sentence)
print("Corrected:", corrected_sentence)

# Expected output:

# Original: dking species
# Corrected: dying species
