# Poetry Generator - Markov Chain NLP

A natural language processing project that generates poetry in the style of Robert Frost using second-order Markov chains. This implementation demonstrates fundamental concepts in statistical language modeling and text generation.

## 🎯 Project Overview

This project builds a probabilistic text generator that learns from Robert Frost's poetry corpus to create new poem lines with similar stylistic patterns. It uses a second-order Markov chain approach, considering the previous two words to predict the next word.

## 🧠 How It Works

### Domain Model Architecture

The generator uses three statistical models:

1. **Initial Distribution** (`initial`): Probability distribution of words that start poem lines
2. **First-Order Transitions** (`first_order`): P(word₂ | word₁) - probability of second word given first
3. **Second-Order Transitions** (`second_order`): P(word₃ | word₁, word₂) - probability of third word given previous two

### Generation Process

```
Line Start → Sample initial word
          ↓
          Sample second word (first-order)
          ↓
          Sample remaining words (second-order)
          ↓
          Continue until 'END' token
```

## 🚀 Quick Start

### Prerequisites

```bash
pip install numpy
```

### Usage

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/poetry-generator-nlp.git
cd poetry-generator-nlp
```

2. **Run the generator:**
```bash
python poetry_generator_nlpv1.py
```

3. **Sample Output:**
```
the road not taken by
and sorry i could not travel both
in leaves no step had trodden black
i shall be telling this with a sigh
```

## 📊 Technical Details

### Data Processing Pipeline

1. **Text Preprocessing**: Remove punctuation, convert to lowercase
2. **Tokenization**: Split text into individual words
3. **Probability Extraction**: Build transition matrices from corpus
4. **Normalization**: Convert counts to probability distributions

### Key Functions

- `remove_punctuation(s)`: Cleans text for processing
- `add2dict(d, k, v)`: Utility for building word transition lists
- `list2pdict(ts)`: Converts word lists to probability dictionaries
- `sample_word(d)`: Samples next word based on probability distribution
- `generate()`: Main generation function that produces 4 lines of poetry

### Statistical Foundation

The model learns these probability distributions:
- P(w₁) - Initial word probabilities
- P(w₂|w₁) - First-order transitions  
- P(w₃|w₁,w₂) - Second-order transitions
- P(END|w₁,w₂) - Line ending probabilities

## 🔧 Architecture Insights

### Memory Complexity
- **Vocabulary Size**: V words
- **Storage Requirements**:
  - Initial: V values
  - First-order: V × V values  
  - Second-order: V × V × V values
  
### Markov Assumption
The model assumes that the probability of the next word depends only on the previous two words, not the entire history. This is the **Markov property** that makes the model computationally tractable.

## 📈 Potential Improvements

### Exercises for Enhancement

1. **Vocabulary Analysis**: Calculate actual vocabulary size and compare dictionary storage efficiency
2. **Direct Counting**: Optimize by building count dictionaries directly instead of accumulating lists
3. **Higher-Order Models**: Implement third-order or variable-length context models
4. **Smoothing**: Add Laplace smoothing for unseen word combinations
5. **Multiple Authors**: Train on multiple poets and compare generated styles

### Advanced Features

- **Rhyme Scheme Generation**: Add phonetic similarity constraints
- **Meter Control**: Incorporate syllable counting for consistent rhythm
- **Topic Modeling**: Generate poetry around specific themes
- **Neural Enhancement**: Hybrid approach with LSTM/Transformer models

## 📚 Learning Outcomes

This project demonstrates:
- **Statistical Language Modeling**: Building probabilistic text models
- **Markov Chains**: First and second-order state transitions
- **Text Preprocessing**: Handling real-world text data
- **Probability Sampling**: Converting distributions to generated text
- **NLP Fundamentals**: Core concepts in computational linguistics

## 🔍 Educational Value

Perfect for understanding:
- How language models work at a fundamental level
- The relationship between statistical patterns and creative generation
- Trade-offs between model complexity and computational requirements
- Foundation concepts before diving into modern neural approaches

## 📝 Data Source

Uses Robert Frost poetry corpus from the [machine learning examples repository](https://github.com/lazyprogrammer/machine_learning_examples).

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Robert Frost for the beautiful poetry corpus
- LazyProgrammer for the educational ML examples
- The NLP community for foundational research in statistical language modeling

---

*"Two roads diverged in a wood, and I— I took the one less traveled by, And that has made all the difference."* - Robert Frost (and now our AI can continue the journey!)

---

<!-- demo-lab:start -->
## Explore this project

[Project page & walkthrough](https://eforus-overseer.github.io/demo-lab/projects/poetry_generation/) — Try an interactive explanation and inspect the original source and results. Browser teaching examples are distinguished from trained models.
<!-- demo-lab:end -->
