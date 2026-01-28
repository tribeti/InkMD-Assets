---
name: "Skill Name (e.g., WebSearch, DataPlotter)"
version: "1.0.0"
author: "Your Name/Org"
tags: ["category1", "category2", "requires_internet"]
description: "A short, high-level summary of what this skill does (used for semantic routing/embeddings)."
---

# 🛠️ Skill Definition: [Skill Name]

## 1. Context & Trigger
**When to use this skill:**
Describe specifically the situation or user intent that triggers this skill.
*   *Example: "Use this when the user asks for current events, weather, or real-time data."*

**Constraints/Safety:**
*   List any limitations (e.g., "Do not use for financial advice").
*   List any required API keys or permissions.

## 2. Input Parameters (Schema)
The agent needs to know exactly what arguments to extract from the conversation.

| Parameter | Type | Required | Description | Default |
| :--- | :--- | :--- | :--- | :--- |
| `query` | String | Yes | The search query optimized for keywords | N/A |
| `max_results`| Integer| No | Number of results to return | 5 |
| `date_range` | String | No | Timeframe for the search | "anytime" |

## 3. Execution Steps / Logic
Instructions on how the agent should perform the task. This can be pseudo-code, Python code, or a chain of thought.

```python
# If this is an executable skill (e.g., Open Interpreter style)
def execute_skill(query, max_results=5):
    """
    Detailed docstring describing the function logic.
    """
    # 1. Connect to API
    # 2. Fetch results
    # 3. Parse and return JSON
    pass
```

*OR (for Prompt-based Skills):*
1.  Analyze the user's input `query`.
2.  Formulate 3 distinct search terms.
3.  Combine results and summarize.

## 4. Few-Shot Examples (Crucial for Quality)
Provide examples of User Input -> Agent Action to ground the LLM.

**Example 1:**
> **User:** "What is the stock price of Apple right now?"
> **Agent Action:** `WebSearch(query="Apple stock price current", date_range="last_24h")`

**Example 2:**
> **User:** "Find me the best Italian restaurants in Hanoi."
> **Agent Action:** `WebSearch(query="best Italian restaurants Hanoi reviews", max_results=10)`

## 5. Output Format
Describe how the result should be returned to the main conversation.
*   *Format:* [JSON / Markdown / Text Summary]
*   *Structure:*
    *   Title
    *   Source URL
    *   Summary Content
```

---

### 💡 Example: Implementing a "CurrencyConverter" Skill

Here is how the template looks when filled out for a real capability.

```markdown
---
name: "CurrencyConverter"
version: "1.2"
tags: ["finance", "utility", "calculation"]
description: "Converts values between global currencies using real-time exchange rates."
---

# 🛠️ Skill Definition: CurrencyConverter

## 1. Context & Trigger
**When to use:**
*   Use when a user asks to convert an amount of money from one currency to another.
*   Use when comparing prices in different currencies.

**Constraints:**
*   Cannot predict future rates.
*   Uses mid-market rates (not bank buy/sell rates).

## 2. Input Parameters

| Parameter | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `amount` | Float | Yes | The numerical value to convert. |
| `from_currency`| String | Yes | ISO 4217 code (e.g., USD, VND, EUR). |
| `to_currency` | String | Yes | ISO 4217 code to convert into. |

## 3. Execution Logic (Python)

```python
import requests

def convert_currency(amount, from_currency, to_currency):
    api_key = "ENV_API_KEY"
    url = f"https://api.exchangerate-api.com/v4/latest/{from_currency}"
    response = requests.get(url).json()
    rate = response['rates'][to_currency]
    return amount * rate
```

## 4. Few-Shot Examples

**Example 1:**
> **User:** "How much is 50 dollars in Vietnam Dong?"
> **Agent Action:** `convert_currency(amount=50, from_currency="USD", to_currency="VND")`

**Example 2:**
> **User:** "Convert 1000 yen to euros."
> **Agent Action:** `convert_currency(amount=1000, from_currency="JPY", to_currency="EUR")`

## 5. Output Format
Return a JSON object:
```json
{
  "original": "50 USD",
  "converted": "1,230,000 VND",
  "rate": "1 USD = 24,600 VND"
}
```
