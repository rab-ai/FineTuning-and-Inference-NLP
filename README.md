# Fine-Tuning and Zero-Shot Inference for NLP Tasks

This repository contains the implementation for fine-tuning a multilingual masked language model (`bert-base-multilingual-cased`) and evaluating the zero-shot performance of a causal language model (`bigscience/bloomz-1b1`) for two NLP tasks:

- **Task 1**: Ideological classification of parliamentary speeches (left-leaning or right-leaning).
- **Task 2**: Power identification (government or opposition) based on parliamentary speeches.

## Dataset

The datasets used for this project are:

- `orientation-tr-train.tsv`: Used for **Task 1**, containing Turkish parliamentary speeches labeled for ideological classification (0 for left-leaning, 1 for right-leaning).
- `power-tr-train.tsv`: Used for **Task 2**, containing Turkish parliamentary speeches labeled for power identification (0 for government, 1 for opposition).

These datasets were preprocessed and split into 90% training and 10% testing sets. Preprocessed test datasets were saved as:

- `task1_bloomz_turkish_results_binary.csv`: Zero-shot inference results for Task 1 on Turkish text.
- `task1_bloomz_english_results_binary.csv`: Zero-shot inference results for Task 1 on English-translated text.
- Similar files for **Task 2** are generated upon running the code.

## Repository Structure

```
├── README.md                           # Project documentation
├── task1.ipynb                         # Fine-tuning and inference for Task 1
├── task1_bloomz_english_results_binary.csv  # Zero-shot results for Task 1 (English)
├── task1_bloomz_turkish_results_binary.csv  # Zero-shot results for Task 1 (Turkish)
├── task2.ipynb                         # Fine-tuning and inference for Task 2
```

Upon running the notebooks, the following files are generated:

- `orientation_train_processed.csv`: Preprocessed training set for Task 1.
- `orientation_test_processed.csv`: Preprocessed test set for Task 1.
- `power_train_processed.csv`: Preprocessed training set for Task 2.
- `power_test_processed.csv`: Preprocessed test set for Task 2.
- `results_task1/`: Directory containing fine-tuned model checkpoints for Task 1.
- `results_task2/`: Directory containing fine-tuned model checkpoints for Task 2.

## How to Run

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/username/FineTuning-and-Inference-NLP.git
   cd FineTuning-and-Inference-NLP
   ```

2. **Run Task 1 Notebook**:
   Open `task1.ipynb` in Jupyter Notebook or any supported environment, and execute the cells sequentially to fine-tune the BERT model and perform zero-shot inference using BLOOMZ.

3. **Run Task 2 Notebook**:
   Similarly, open `task2.ipynb` and execute the cells to repeat the process for power identification.

## Results

| **Task** | **Model**             | **Language**        | **Accuracy (%)** | **F1 Score (%)** |
|----------|-----------------------|---------------------|------------------|------------------|
| Task 1   | Fine-Tuned BERT       | Turkish (`text`)    | 78.62            | 78.51            |
| Task 1   | Zero-Shot BLOOMZ      | Turkish (`text`)    | 41.82            | -                |
| Task 1   | Zero-Shot BLOOMZ      | English (`text_en`) | 41.82            | -                |
| Task 2   | Fine-Tuned BERT       | English (`text_en`) | 79.18            | 79.13            |
| Task 2   | Zero-Shot BLOOMZ      | Turkish (`text`)    | 41.82            | -                |
| Task 2   | Zero-Shot BLOOMZ      | English (`text_en`) | 41.82            | -                |

## Key Notes

- **Fine-Tuning**: The `bert-base-multilingual-cased` model was fine-tuned on task-specific datasets to achieve high accuracy and F1 scores.
- **Zero-Shot Inference**: BLOOMZ struggled with both Turkish and English data due to the lack of fine-tuning on task-specific data.
- **Computational Resources**: Fine-tuning requires significant computational power; ensure a capable GPU is available.

## Acknowledgments

This project was developed for the NLP assignment involving parliamentary speeches. The `bert-base-multilingual-cased` and `bigscience/bloomz-1b1` models were integral to this study.
