This project demonstrates how to fine-tune the codellama/CodeLlama-7b-hf model using the b-mc2/sql-create-context dataset from Hugging Face to generate SQL query from natural language descriptions.

Inspired by @philschmid's blogpost on LLaMA fine-tuning.

## Project Overview

Model: CodeLlama-7b-hf

Dataset: b-mc2/sql-create-context

Training Samples: 10,000

Epochs: 3

Hardware: A100 80GB

Precision: 4-bit QLoRA (NF4)

Trainer: trl’s SFTTrainer with Hugging Face PEFT & bitsandbytes

## Dataset Format

Dataset contains messages with:
- `context`: Natural language description of a schema/table
- `question`: A user question in english
- `answer`: An sql query output to retrieve the data from table

## Training loss

| Step | Training Loss |
|------|----------------|
| 10   | 0.8202         |
| 20   | 0.5808         |
| 30   | 0.5359         |
| 40   | 0.5056         |
| 50   | 0.5090         |
| 60   | 0.4803         |
| 70   | 0.4778         |
| 80   | 0.4468         |
| 90   | 0.4378         |
| 100  | 0.4375         |
| 110  | 0.4410         |
| 120  | 0.4315         |
| 130  | 0.4295         |
| 140  | 0.3962         |
| 150  | 0.3728         |
| 160  | 0.3785         |
| 170  | 0.3740         |
| 180  | 0.3760         |
| 190  | 0.3798         |
| 200  | 0.3763         |

## Output from finetuned model
Query:
What is every institution with a nickname of Ravens?

Original Answer:
SELECT institution FROM table_262514_1 WHERE nickname = "Ravens"

Generated Answer:
SELECT institution FROM table_262514_1 WHERE nickname = "Ravens"
