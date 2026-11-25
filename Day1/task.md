# Day 1 · Your 10% Task: Sweet Crumbs Home Bakery Experiments

This guide accompanies **Day 1 · How LLMs work and your first API call** from the *AI Agents Workshop · Level 1 Fundamentals*.

## Today's Build Recap: Sweet Crumbs Home Bakery

In today's core build, we connect to Groq's OpenAI-compatible endpoint (`https://api.groq.com/openai/v1`) using the `openai` Python SDK and `openai/gpt-oss-20b`:

- **System prompt (`SYSTEM`)**: Defines the bakery's role, facts (24 hours' notice for orders, eggless versions available, Plum cake Rs 500, Chocolate cake Rs 650, Cupcake Rs 80), rules (never promise delivery times, say `"I'll check with the owner."` if unknown), and format constraints (under 50 words, friendly, matching English or Telugu).
- **Low temperature (`0.2`)**: Keeps factual and pricing responses focused and consistent.
- **Usage inspection**: Prints `response.choices[0].message.content` along with `response.usage` to see token consumption.

---

## Your 10% Tasks (Implemented in `day1_your_10_percent_task.ipynb`)

1. **Temperature (`0.2` vs `1.2`)**: Ask *"Write a tagline for Sweet Crumbs"* three times at `temperature=0.2` and three times at `temperature=1.2`, then compare consistency vs. variety.
2. **Hallucination**: Remove the `FACTS` line from the system prompt and ask *"Do you deliver to Kakinada?"* to observe how the model may guess or invent details without grounded facts.
3. **No Memory**: Make two separate API calls (*"My name is Ravi."* then *"What is my name?"*) to see statelessness in action, then pass the full conversation history in a single `messages` list so it "remembers."
4. **Tokens (English vs. Telugu)**: Ask the same customer question in English and in Telugu and compare `response.usage.prompt_tokens`.
5. **Your Business**: Rewrite `SYSTEM` for a business of your choice (5 facts, 3 rules) and test it with 3 realistic customer questions.

---

## Security & API Key Note

The provided Groq API key (`GROQ_API_KEY`) is included in the notebook for immediate testing as requested. In real projects or public repositories (such as GitHub), store API keys in environment variables or **Google Colab Secrets** (`userdata.get("GROQ_API_KEY")`) rather than hardcoding them in source files.

## Before Day 2

Write down the **10 questions customers ask your business most**—on Day 2, you will turn them into a system prompt, a stateful chatbot, and your first test file.