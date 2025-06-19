# GPT-2 Keyword Prompt Optimization Framework

## Overview

This repository implements a **Prompt Optimization Framework** using the **Greedy Coordinate Gradient (GCG)** algorithm to optimize GPT-2's output for specific use cases. The framework aims to:

1. Uncover vulnerabilities in GPT-2's output generation by optimizing for specific keywords.
2. Implement constraint-based prompting techniques that adhere to token limitations.
3. Analyze response patterns and evaluate compliance with given constraints.

## Key Features

* **Prompt Optimization via GCG**: Utilizes GCG to iteratively refine prompts for targeted keyword generation.
* **Constraint-Based Prompting**: Ensures prompts meet requirements such as token count limits and absence of specific keywords.
* **Keyword Presence Evaluation**: Tests if generated outputs contain specific keywords within a limited number of tokens.
* **Scalable Testing**: Supports batch evaluation of multiple keywords and constraints.

## Use Case

This framework was developed as part of research into language model security and prompt engineering. It identifies potential risks in text generation models by targeting specific outputs under strict constraints, enabling better understanding and mitigation of vulnerabilities.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/llm-attacks/llm-attacks.git
   cd llm-attacks
   ```

2. Install dependencies:

   ```bash
   pip install -e .
   pip install livelossplot transformers==4.28.1
   ```

3. Verify installation:

   ```bash
   python -m torch --version
   ```

## Usage

### Step 1: Initialize the Framework

Load the GPT-2 model and tokenizer:

```python
from transformers import GPT2LMHeadModel, GPT2Tokenizer

# Load model and tokenizer
model = GPT2LMHeadModel.from_pretrained('gpt2').eval()
tokenizer = GPT2Tokenizer.from_pretrained('gpt2')
```

### Step 2: Find Optimal Prompts

Use the `GPT2KeywordPromptFinder` class to optimize prompts for targeted keyword generation:

```python
finder = GPT2KeywordPromptFinder()
keyword = "radagon"
prompt, success, seed = finder.find_prompt(keyword)

print(f"Prompt: {prompt}")
print(f"Success: {success}")
```

### Step 3: Evaluate Prompts

Run tests to ensure compliance with constraints:

```python
run_tests(model, tokenizer, {"radagon": prompt}, ["radagon"], verbose=True)
```

### Example Output

```text
Keyword: radagon
Prompt: PATH Tib jewelry vibr Alf unsuccessful 1969 observes 257 imprison
Success: True
TESTS PASSED: 1 of 1
```

## Testing

To test the framework on a batch of keywords:

```python
keywords = ["radagon", "godfrey", "morgott", "marika", "radahn"]
run_tests(model, tokenizer, prompts, keywords, verbose=True)
```

## Results

This framework has been tested across five attack vectors:

1. Targeted keyword generation with token constraints.
2. Analysis of GPT-2’s response patterns.
3. Identification of vulnerabilities in output generation.
4. Verification of compliance with constraints.
5. Generation diversity and adaptability analysis.

## Dependencies

* Python 3.8+
* Transformers 4.28.1
* PyTorch
* NumPy
* LiveLossPlot

## License

This project is open-source under the MIT License.

## Acknowledgments

This work is part of the **Language Model Security Testing via Prompt Optimization** project:

* Developed a prompt optimization framework using the **Greedy Coordinate Gradient (GCG)** algorithm.
* Implemented techniques to achieve targeted keyword generation while adhering to strict token limitations.
* Conducted analysis on GPT-2 model response patterns across multiple attack vectors.


