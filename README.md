# LLM Model Evaluation

Comparison of three Qwen3.5 language models using 100 Turkish questions, sampling parameter experiments, and LLM-as-a-Judge evaluation.

## Project Overview

This project evaluates how different model sizes and sampling parameters affect the responses of Large Language Models (LLMs).

The experiments were developed in Python using Google Colab and the OpenRouter API.

## Models

Three models from the same Qwen3.5 family were selected to compare different model scales under similar test conditions.

| Model | Architecture | Purpose |
|---|---|---|
| Qwen3.5-9B | Dense | Small model |
| Qwen3.5-27B | Dense | Medium model |
| Qwen3.5-122B-A10B | Mixture of Experts (MoE) | Large model |

Using models from the same family allows us to investigate how model scale and architecture influence response quality.

## Dataset

The dataset contains 100 Turkish questions with reference answers.

Questions cover different subjects and difficulty levels. Reference answers are included for automated evaluation and require final source verification.

Each model receives the same questions, and its responses are stored in an Excel file.

## Sampling Parameters

The experiments examine three generation parameters:

- **Temperature:** Controls randomness during token selection.
- **Top-p:** Restricts token selection using cumulative probability.
- **Top-k:** Limits the number of candidate tokens.

Four parameter configurations were tested:

| Scenario | Temperature | Top-p | Top-k |
|---|---|---|---|
| Deterministic | 0.0 | 1.00 | 1 |
| Balanced | 0.7 | 0.90 | 40 |
| Creative | 1.25 | 0.85 | 50 |
| High Randomness | 1.85 | 1.00 | 0 |

Each configuration was tested twice on five prompts for each model, producing 120 sampling records.

## LLM-as-a-Judge

Claude Haiku 4.5 was used as an independent evaluator.

For each model response, the evaluator receives:

1. The original question
2. The reference answer
3. The generated model response

The evaluator assigns a score between 0 and 100 and provides a short explanation.

These scores represent rubric-based evaluations, not calibrated probabilities of correctness.

Some evaluation scores are still missing in the current results. Therefore, the evaluation is considered preliminary.

## Technologies

- Python
- Google Colab
- OpenRouter API
- OpenAI Python SDK
- Pandas
- OpenPyXL
- Microsoft Excel

## Project Files

- `LLM_Sade_3_Model_Claude (3).ipynb` — Python notebook for model inference, sampling experiments, and Claude evaluation.
- `LLM_Sade_100_Soru_Tablo(1).xlsx` — Original question-answer dataset.
- `LLM_Sade_Sonuclar (2).xlsx` — Generated responses, evaluation scores, and sampling results.

## How to Run

1. Open the notebook in Google Colab.
2. Create an OpenRouter API key.
3. Add the key to Colab Secrets as `OPENROUTER_API_KEY`.
4. Install the required Python libraries using the first notebook cell.
5. Upload the original Excel dataset.
6. Run the three model sections.
7. Run the sampling experiments.
8. Run the Claude evaluation section.
9. Export the final Excel file.

**Security:** Never add your API key directly to the notebook or commit it to GitHub.

## Research Objective

The primary goal is to investigate whether larger models consistently provide better answers and how Temperature, Top-p, and Top-k influence response variability.

The evaluation framework may also support future experiments involving Retrieval-Augmented Generation (RAG).

## Limitations

- Reference answers require final verification.
- LLM-as-a-Judge evaluations may contain errors or biases.
- Missing evaluation scores must not be interpreted as zero.
- Model performance may vary across API providers and inference settings.

## Academic Context

Developed as part of an Agent-Based Artificial Intelligence course assignment.

**Isparta University of Applied Sciences — Computer Engineering**

**November 2026**
