# AI-Interview-Coach
# T5 Interview Coach — Resume-Aware Question & Answer Generation

This project is an intelligent interview preparation tool built on the T5 transformer model, capable of generating personalized interview questions, answers, and follow-up questions based on a user's resume, job description (JD), and difficulty level.

## Overview

We built a dual-phase T5-based model that simulates a human-like interviewer:

- Phase 1 (Question Generation):  
  Input: Resume + JD + Difficulty level → Generates relevant interview questions  
- Phase 2 (Answer Generation):  
  Input: Resume + JD + Question → Generates model answer  
- Follow-up:  
  Input: User answer → Generates a meaningful follow-up question

This tool helps candidates prepare for technical and behavioral interviews with content tailored to their profile and target role.

## Features

- User-friendly interface built using React
- FastAPI backend that connects to the trained model
- T5-base model fine-tuned on a custom dataset (token size: 512)
- Generates a complete pipeline: Question → Answer → Follow-up
- Accepts resumes and job descriptions in structured or plain text format
- Questions and answers are grounded in the resume and job description

## Dataset Generation

We created a diverse dataset by combining:

- Real job descriptions and resumes scraped using BrightData and Gemini API
- Synthetic resume-JD pairs and Q&A data generated using the LLAMA model
- Thousands of examples curated, cleaned, and standardized for fine-tuning

## Evaluation Metrics

| Task               | Metric         | F1 / Score |
|--------------------|----------------|------------|
| Question Generation| ROUGE-1 (F1)   | 0.62       |
|                    | ROUGE-2 (F1)   | 0.47       |
|                    | ROUGE-L (F1)   | 0.58       |
|                    | BLEU-4         | 0.41       |
|                    | METEOR         | 0.53       |
|                    | BERTScore (F1) | 0.87       |
| Answer Generation  | ROUGE-1 (F1)   | 0.68       |
|                    | ROUGE-2 (F1)   | 0.52       |
|                    | ROUGE-L (F1)   | 0.65       |
|                    | BLEU-4         | 0.46       |
|                    | METEOR         | 0.59       |
|                    | BERTScore (F1) | 0.89       |

## Model Architecture

- Base model: `t5-base`
- Input size: 512 tokens
- Dual-task structure:
  - Resume + JD +difficulty level → Question
  - Resume + JD + Question → Answer
- Trained using HuggingFace Transformers with PyTorch backend

## Tech Stack

- Model: T5-base
- Fine-tuning: HuggingFace Transformers, PyTorch
- Frontend: React
- Backend: FastAPI
- Data Collection: BrightData, Gemini API, LLAMA
- Evaluation: ROUGE, BLEU, METEOR, BERTScore
- Deployment: Python 3.10+, Google Colab (GPU training)

## Future Work

- Add multi-turn Q&A and interactive sessions
- create personilsed account for each user to set preferences for extra parameters
- Domain-specific fine-tuning for industry-specific interviews
