---
name: Kubernetes_Ops
description: Executes kubectl commands to monitor cluster health, retrieve logs, and debug pod failures. Triggers: cluster status, logs, debugging. (Under 200 chars)
dependencies: subprocess, json  # Only if scripts are involved
---

# Kubernetes Cluster Manager

## Overview
Manages Kubernetes operations: monitors health, fetches logs, debugs failures. Focuses on read-only by default; requires confirmation for modifications. Solves repeatable tasks like status checks and error diagnosis with consistent JSON output.

## Instructions
1. Analyze user intent: classify as read (get, describe, logs) or write (delete, restart, scale, apply).
2. Check namespace: if unspecified/ambiguous, list namespaces.
3. Build command: append -o json for get; --tail for logs; require confirmation for writes.
4. Handle errors: if NotFound, query all resources to suggest corrections.
5. Execute via Python wrapper; return parsed output or error.

## Examples
### Example 1: Health Check
- **Input**: "Why is the payment service down?"
- **Expected Output**: kubectl get pods -n payment --field-selector=status.phase!=Running -o json (parsed JSON of non-running pods)

### Example 2: Log Retrieval
- **Input**: "Show me the last error logs for the auth api."
- **Expected Output**: First: kubectl get pods -n default | grep auth  
Then: kubectl logs auth-api-7d9cf -n default --tail=20 (log output)

### Example 3: High-Risk Action
- **Input**: "Restart the database deployment."
- **Expected Output**: "Executing rollout restart on database will cause temporary downtime. Confirm?" (No execution without confirmation)

## When to Use
Invoke for Kubernetes queries involving cluster status, pod/service details, logs, or debugging. Use for read operations; confirm writes. Avoid non-K8s tasks.

## Resources
- Implementation Wrapper: Python code for kubectl execution (included below)
- Tags: infrastructure, k8s, kubectl, debugging, logs
- Version: 2.1.0
- Author: SRE_Team
- Requires Confirmation: delete, restart, scale, apply

File name: kubernetes_ops.md
