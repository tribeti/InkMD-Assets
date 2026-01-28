---
name: [Skill Name]  # Max 64 characters, human-friendly name
description: [Brief description of the skill's purpose, usage triggers, and what it does. Keep under 200 characters for Claude to use in deciding when to invoke it.]
dependencies: [Optional: List of software packages, e.g., python>=3.8, pandas>=1.5.0]  # Only if scripts are involved
---

# [Skill Title]  
# Often matches the name, or more descriptive

## Overview
[Detailed explanation of the skill's goals, scope, and high-level approach. Include any guidelines for consistency, such as tone, format, or key principles. Explain how it solves a specific, repeatable task.]

## Instructions
[Step-by-step workflow or guidelines for Claude to follow. Be clear, concise, and actionable. Number steps if sequential. Include decision points, error handling, or variations.]

## Examples
### Example 1: [Descriptive Title]
- **Input**: [Sample user query or input data]
- **Expected Output**: [Detailed sample response, including any formatting]

### Example 2: [Another Scenario]
- **Input**: [Another sample]
- **Expected Output**: [Corresponding output]

[Add more examples as needed to cover edge cases or variations.]

## When to Use
[Specify triggers, scenarios, or conditions for invoking this skill. Be specific to help Claude decide accurately, e.g., "Use when user asks for data analysis involving CSV files." Avoid overlap with other skills.]

## Resources
- [List any additional files, e.g., REFERENCE.md for data sources]
- [Folders like /resources/ for images, fonts, or scripts]
- [External references if applicable, but keep self-contained]

[Best practices reminder: Keep focused on one workflow; test incrementally; ensure clear invocation criteria.]
