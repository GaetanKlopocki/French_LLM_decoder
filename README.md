# French LLM Decoder

This repository contains the training and inference code for a **decoder-only LLM trained on an 85M-token dataset** of natural-language instructions and answers, built for fine-tuning a French-speaking language model. The dataset comes from [angeluriot/French_instruct](https://github.com/angeluriot/French_instruct).

**The model's lightweight architecture allows it to be trained on a single Colab GPU** (free-tier T4, ~16 GB VRAM). After around 40,000 epochs, it is already able to produce sentences with readable syntax and vocabulary relevant to the prompt's context.

**A pre-trained model is available for inference testing.** It was trained for 60,000 epochs (~15 hours on a T4 Colab GPU). The model is accessible on Hugging Face: [GaetanKlopocki/French_LLM_decoder on Hugging Face](https://huggingface.co/GaetanKlopocki/French_LLM_decoder).

**You can also train the model yourself.** When training on Google Colab, progress can be saved to Google Drive so you can pause and resume training later.

## 📓 Open in Colab

| Notebook | Description | Link |
|---|---|---|
| `French_LLM_Decoder_training.ipynb` | Train the model from scratch | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GaetanKlopocki/French_LLM_decoder/blob/main/French_LLM_Decoder_training.ipynb) |
| `French_LLM_Decoder_inference.ipynb` | Test the pre-trained model | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GaetanKlopocki/French_LLM_decoder/blob/main/French_LLM_Decoder_inference.ipynb) |

## 📁 Repository structure

```
French_LLM_decoder/
├── data/                                  # Raw .jsonl instruction dataset files
├── Inference/                             # Resources needed for inference (model, tokenizer)
├── load.py                                # Utility functions to load and merge the dataset
├── French_LLM_Decoder_training.ipynb      # Model training notebook
├── French_LLM_Decoder_inference.ipynb     # Inference / text generation notebook
└── .gitignore
```

## 📊 Dataset

The data lives in the `data/` folder as `.jsonl` files (one instruction/answer example per line). The `load.py` module provides two functions:

- `load_dataset()`: walks through every file in `data/` and returns the examples as a list of dictionaries.
- `merge_dataset(path="./dataset.jsonl")`: merges all `.jsonl` files in `data/` into a single output file.

```python
from load import load_dataset, merge_dataset

data = load_dataset()          # load all examples into memory
merge_dataset("dataset.jsonl") # merge the files into a single .jsonl
```

## 🚀 Usage

### Clone the repository

```bash
git clone https://github.com/GaetanKlopocki/French_LLM_decoder.git
cd French_LLM_decoder
```

### Training

Open `French_LLM_Decoder_training.ipynb` (locally or via the Colab button above) to train the decoder model on the French instruction dataset.

### Inference

Open `French_LLM_Decoder_inference.ipynb` (locally or via the Colab button above), together with the resources in `Inference/` to generate responses with the trained model.

## 🔗 Resources

- Dataset: [angeluriot/French_instruct](https://github.com/angeluriot/French_instruct)
- - Pre-trained model: [GaetanKlopocki/French_LLM_decoder on Hugging Face](https://huggingface.co/GaetanKlopocki/French_LLM_decoder)

## 📄 License

Refer to the original repository for the dataset's and code's terms of use.
