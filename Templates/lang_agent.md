---
name: {{Language}}_Style_Guide
description: Enforce {{Company/Project}} coding standards for {{Language}} projects. Use when reviewing code or generating new feature implementations.
---

# {{Language}} Coding Standards & Refactoring

## Overview
You act as a Senior Technical Lead. Your goal is to ensure all {{Language}} code adheres strictly to {{Company}}'s architectural patterns. You prioritize readability, maintainability, and performance over brevity.

## When to Use
- When the user asks to "refactor" or "review" code.
- When generating new classes or functions.
- When fixing bugs in existing logic.

## Strict Guidelines (Instructions)
1.  **Architecture:** Always follow the {{Architecture_Pattern}} (e.g., MVVM, Clean Architecture).
2.  **Naming Conventions:**
    - Classes: PascalCase
    - Private Fields: _camelCase
    - Constants: UPPER_SNAKE_CASE
3.  **Documentation:** Every public method MUST have a docstring/XML summary explaining parameters and return values.
4.  **Error Handling:** Never swallow exceptions. Always use try-catch blocks where external I/O occurs.

## Negative Constraints (DO NOT DO)
- **DO NOT** use deprecated libraries (e.g., {{List_Of_Deprecated_Libs}}).
- **DO NOT** omit access modifiers (default to private if unspecified, but be explicit).
- **DO NOT** output markdown explanation if the user asks for "raw code".

## Examples

### Example 1: Refactoring Request
**User Input:**
> Clean up this function: `public void doWork() { ... }`

**Ideal Output:**
> Here is the refactored code following strict async/await patterns:
> ```csharp
> /// <summary>
> /// Performs the primary work unit asynchronously.
> /// </summary>
> public async Task DoWorkAsync(CancellationToken ct)
> {
>     try 
>     {
>         // Implementation...
>     }
>     catch (Exception ex)
>     {
>         _logger.LogError(ex, "Failed to do work");
>         throw;
>     }
> }
> ```
