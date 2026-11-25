# Day 2 · Your 10% Task: Prompts, Memory & Python for Agents

This guide accompanies **Day 2 · Prompts, memory and the Python agents need** from the *AI Agents Workshop · Level 1 Fundamentals*.

## Today's Build Recap: A Sweet Crumbs Chatbot That Remembers

In today's build, we upgrade Day 1's single API call into a stateful, resilient assistant using Groq (`https://api.groq.com/openai/v1`) and `openai/gpt-oss-20b`:

- **Menu as a Python `dict`**: Stores `MENU = {"plum cake": 500, "chocolate cake": 650, "cupcake": 80}` and injects it into the system prompt via `json.dumps(MENU)`.
- **Four-part System Prompt**: Structures instructions into `ROLE`, `FACTS`, `RULES`, and `FORMAT`.
- **Function, Type Hints & Decorator**: Wraps `get_price(item: str, qty: int = 1) -> int` with `@log_call` to log inputs and outputs without changing the function body.
- **Manual Conversation Memory (`history`)**: Appends every `user` and `assistant` message to `history` and trims old turns (`[history[0]] + history[1:][-MAX_TURNS:]`) to manage token usage.
- **Graceful Error Handling**: Uses `try / except` around API calls (`RateLimitError`, `APIConnectionError`) so the bot never crashes on a customer.

---

## Your 10% Tasks (Implemented in `day2_your_10_percent_task.ipynb`)

1. **Prompt Parts**: Remove the `RULES` lines from `SYSTEM` and ask *"Can you deliver in 1 hour?"*, then restore `RULES` and compare the responses.
2. **Few-Shot Classifier**: Build a few-shot classifier with 3 worked examples (`order`, `question`, `complaint`) and test it on 5 new customer messages.
3. **Structured JSON Output**: Ask the bot to extract an order as JSON (`name`, `item`, `qty`, `date`, `eggless`) and parse it safely with `json.loads()` inside `try / except`.
4. **Memory & Trimming**: Set `MAX_TURNS = 2`, introduce your name, chat for three turns, and ask *"What is my name?"* to observe what happens when early turns are trimmed out of the context sent to the model.
5. **Your Business**: Rebuild Today's Build for a custom business with its catalogue as a `dict`, a priced function with type hints, a docstring, and `@log_call`, plus a tailored 4-part `SYSTEM` prompt.

---

## Before Level 2 (Day 3)

Bring your **10 most frequent customer questions** and your **business catalogue as a Python `dict`**. On Day 3, this chatbot evolves into an **agent**, and on Day 4 your Python functions become tools the model can invoke on its own.