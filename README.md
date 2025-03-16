# Optimizing-Article-Text-Summarization-with-DeepSeek-Enhanced-Ensemble-technique

Overview

This project focuses on text summarization using the CNN/Daily Mail dataset available on Hugging Face. The dataset was used to generate extractive and abstractive summaries using multiple LLMs, followed by an ensemble technique to refine the generated summaries. The evaluation of the summarization quality was carried out using multiple metrics to ensure a robust analysis.

Dataset

The dataset was sourced from Hugging Face: abisee/cnn_dailymail.

A subset of 315 data points was taken from the training set for experimentation.

Models Used

1. Extractive Summarization

Model: microsoft/Phi-3.5-MoE-instruct

Why this model?

Phi-3.5-MoE uses a Mixture of Experts (MoE) architecture where only 6.6B active parameters are used from a total of 441.9B parameters.

Designed to provide fact-based summaries.

2. Abstractive Summarization

Model: NousResearch/Hermes-2-Pro-Mistral-7B

Implementation Notes:

The model was quantized to 8-bit using Flash Attention.

Encountered a challenge in implementing its GGUF format in llama.cpp due to storage restrictions in the RC Cluster.

Could not use Pip install (RC Cluster restriction) and llama.cpp is unavailable in Conda, requiring an alternative approach.

Observations: The latency of this model was higher than Phi-3.5-MoE.

Purpose: To generate natural language summaries in its own style.

3. Ensemble Summarization

Model: deepseek-ai/DeepSeek-R1-Distill-Qwen-14B

Purpose:

Takes the summaries generated by the extractive and abstractive models.

Produces a refined summary that combines insights from both summaries.

Helps capture additional information or facts missed by either model.

Evaluation Metrics

Following best practices, three evaluation techniques were used to assess the summarization quality:

SummaScore - Measures content relevance and factual consistency.

QuestEval - Evaluates question-answering consistency within the summary.

BERTScore - Measures semantic similarity between the article and generated summaries.

Conclusion

This project successfully explored multiple summarization approaches, leveraging Mixture of Experts, quantization, and ensemble learning. The combination of extractive and abstractive summarization improved information retention while refining generated summaries. The evaluation metrics provided comprehensive insights into summarization quality, ensuring a robust and effective summarization pipeline.
