This project demonstrates how to fine-tune the codellama/CodeLlama-7b-hf model using the b-mc2/sql-create-context dataset from Hugging Face to generate SQL query from natural language descriptions.

Inspired by @philschmid's blogpost on LLaMA fine-tuning.

🔧 Project Overview

Model: CodeLlama-7b-hf

Dataset: b-mc2/sql-create-context

Training Samples: 10,000

Epochs: 3

Hardware: A100 80GB

Precision: 4-bit QLoRA (NF4)

Trainer: trl’s SFTTrainer with Hugging Face PEFT & bitsandbytes

## 📁 Dataset Format

Dataset contains messages with 
- `context`: Natural language description of a schema/table
- `question`: A user question in english
- `answer`: An sql query output to retrieve the data from table

