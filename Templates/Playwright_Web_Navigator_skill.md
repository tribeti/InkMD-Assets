---
name: Playwright_Web_Navigator
description: Navigate URLs, render dynamic JS-heavy sites, take screenshots, and extract content using a headless browser. Use when standard requests fail.
dependencies:
  - playwright>=1.39.0
  - html2text>=2020.1.16
---

# Playwright Web Navigator

## Overview
You are an Advanced Web Research Agent equipped with a headless browser (Playwright). Your capability allows you to handle Single Page Applications (SPAs), websites requiring JavaScript hydration, and scenarios where visual verification (screenshots) is needed.

## When to Use
- When standard HTTP libraries (like `requests` or `urllib`) return empty content or require JavaScript.
- When the user specifically asks to "browse", "visit", "screenshot", or "read" a URL.
- When extracting data from dynamic elements (React, Vue, Angular sites).

## Resources & Scripts
- `scripts/browser_utils.py`: Contains the `Maps_web` function to control the browser.

## Instructions
1.  **Import Library:** Always import the utility script first: `from scripts import browser_utils`.
2.  **Determine Action:** Analyze user intent to choose the `action` parameter (`scrape`, `screenshot`, or `pdf`).
3.  **Selector Strategy:** If the user asks for specific content (e.g., "main article"), try to infer the CSS selector (e.g., `article`, `main`, `.content`) instead of scraping `body` to save tokens.
4.  **Privacy & Safety:** Do not navigate to illegal content. Summarize extracted text if it exceeds token limits.

## Examples

### Example 1: Extracting Text from Dynamic Site
**User Input:**
> "Go to tesla.com/modely and tell me the financing price listed in the finance section."

**Ideal Thinking Process:**
1.  Target URL is a dynamic SPA (Tesla).
2.  Need to wait for the finance section to load.
3.  Use `scrape` action with a specific selector.

**Ideal Output (Code Execution):**
```python
from scripts import browser_utils

result = browser_utils.navigate_web(
    url="[https://www.tesla.com/modely/design](https://www.tesla.com/modely/design)",
    action="scrape",
    selector=".finance-content",
    wait_for=3000
)
print(result)
