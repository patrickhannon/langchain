# Prompt Engineering with LangSmith Playground 🤖🧠

This tutorial demonstrates how to use the **LangSmith Playground** and **Prompt Hub** to design, compare, optimize, version, and evaluate prompts for Retrieval-Augmented Generation (RAG).

Unlike the LangChain RAG application, this tutorial focuses entirely on the **prompt engineering workflow**. The retrieved context comes from the same **AG News** dataset used throughout the course.

---

# Learning Objectives


- Create prompt templates
- Use prompt variables
- Compare multiple prompt versions
- Test different LLMs
- Optimize prompts using AI
- Save prompts to the Prompt Hub
- Evaluate prompts on datasets
- Analyze latency, cost, and token usage

---

# Prerequisites

- LangSmith account
- OpenAI API Key
- GPT-5.5 (or another supported model)
- Retrieved documents from the LangChain RAG demo

---

# Dataset

This tutorial uses the **AG News** dataset from Hugging Face.

The dataset contains news articles from four categories:

- World
- Sports
- Business
- Science & Technology

For consistency, use the same retrieved documents throughout the tutorial.

---

# Step 1 — Open LangSmith Playground

Open:

https://smith.langchain.com/o/64f05e18-d0b3-5b52-b1a2-201ed3a50b18/playground

The Playground contains:

- Prompt editor
- Model configuration
- Variables
- Response panel
- Compare mode
- Prompt Hub integration

---

# Step 2 — Configure the Model

Choose:

| Setting | Value |
|----------|-------|
| Provider | OpenAI |
| Model | GPT-5.5 |
| Temperature | 0 |
| Max Output Tokens | 300 |

Keeping these settings fixed ensures that only the prompt changes during the experiment.

---

# Step 3 — Create Prompt Variables

Create two variables.

## System Prompt

```text
You are a grounded news assistant.

Use ONLY the retrieved context.

Never invent information.

Cite every factual statement.

If the context is insufficient, explicitly say so.
```

---

## User Prompt

```text
Retrieved Context

{context}

Question

{question}
```

LangSmith automatically detects variables inside `{}`.

---

# Step 4 — Provide Sample Inputs

## Context

```text
[Source 1]
Microsoft announced...

[Source 2]
Apple reported...

[Source 3]
Researchers developed...
```

---

## Question

```text
What do these articles say about technology companies?
```

Run the prompt.

Observe the generated answer.

---

# Step 5 — Improve the Prompt

Replace the system prompt with:

```text
You are a grounded research assistant.

Rules

• Use ONLY the supplied context.

• Never use outside knowledge.

• Cite every factual statement using [Source X].

• If the answer cannot be found in the context,
say that the available information is insufficient.

Response

• One introductory sentence

• Three bullet points

• One limitation

Maximum 180 words.

Professional tone.
```

Run the prompt again.

Compare both responses.

---

# Step 6 — Create Prompt Variants

Duplicate the prompt.

Create several versions.

---

## Version 1

Simple Assistant

```text
You are a helpful assistant.
```

---

## Version 2

Grounded Assistant

Uses citations and retrieved context only.

---

## Version 3

Beginner-Friendly

```text
Explain everything in simple language.

Avoid technical vocabulary.

Include one simple example.
```

---

## Version 4

Executive Summary

```text
Return:

Headline

Key Findings

Business Impact

Risks

Maximum 120 words.
```

---

## Version 5

JSON Output

```text
Return valid JSON only.

{
  "summary":"",
  "evidence":"",
  "confidence":"",
  "limitations":""
}
```

Run all versions using exactly the same context.

---

# Step 7 — Compare Models

Without changing the prompt:

Compare

- GPT-5.5
- GPT-4.1
- GPT-4o-mini

Observe differences in:

- Reasoning
- Writing quality
- Citations
- Token usage
- Latency

---

# Step 8 — Optimize the Prompt

Use the built-in AI optimization feature.

Click

**Polly → Optimize Prompt**

LangSmith suggests improvements such as:

- clearer instructions
- improved formatting
- stronger constraints
- better output structure

Compare:

Original Prompt

↓

Optimized Prompt

↓

Generated Response

---

# Step 9 — Save to Prompt Hub

Click

**Save**

or

**Commit**

Example name:

```
Grounded AG News Assistant
```

Add:

- Description
- Tags
- README
- Version notes

Each save creates a new version.

---

# Step 10 — Evaluate the Prompt

Create a small evaluation dataset.

Example questions:

```
What happened with Microsoft?

Explain the technology articles.

Summarize the business news.

Compare Microsoft and Apple.

What information is missing?
```

Run the evaluation.

Review:

- Accuracy
- Groundedness
- Helpfulness
- Conciseness
- Latency
- Token usage

---

# Compare Prompt Versions

| Version | Purpose |
|----------|----------|
| V1 | Simple assistant |
| V2 | Grounded RAG |
| V3 | Beginner explanation |
| V4 | Executive summary |
| V5 | JSON output |

Evaluate:

- Accuracy
- Structure
- Readability
- Hallucination reduction
- Citation quality
- Cost
- Latency

---

# Best Practices

- Keep the retrieved context identical.
- Change only one prompt element at a time.
- Use explicit instructions.
- Specify the desired output format.
- Require citations.
- Ask the model to acknowledge uncertainty.
- Compare prompts objectively.

---

# Key Takeaways

LangSmith provides a complete prompt engineering workflow by combining:

- Prompt editing
- Prompt variables
- Prompt versioning
- Prompt comparison
- AI-assisted optimization
- Dataset evaluation
- Model comparison
- Prompt Hub integration

Unlike a traditional playground, LangSmith helps you continuously improve prompts, measure their quality, and manage versions as part of a production-ready AI development workflow.