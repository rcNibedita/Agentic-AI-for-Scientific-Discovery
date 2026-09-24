# Scientific Calculator Agent

A minimal LLM-powered scientific agent demonstrating the fundamentals of
tool calling and agentic workflows using Python, RDKit, and the Groq API.

This project is the introductory project of the
[Agentic-AI-for-Scientific-Discovery](../) repository.

---

## 1. Project Overview

The goal of this project is to understand how an LLM can interact with
deterministic scientific Python functions through tool calling.

Rather than asking the LLM to perform scientific calculations itself,
the LLM is used to:

1. Understand the user's request.
2. Decide whether a tool is required.
3. Select the appropriate tool.
4. Provide the required arguments.
5. Receive the result from the actual Python function.
6. Generate a final natural-language response.

The scientific calculations themselves are performed by Python and RDKit.

### Scientific tools

The agent currently has two tools:

- `calculate_area(length, width)`
- `calculate_molecular_weight(smiles)`

---

## 2. Agent Architecture

The project demonstrates the following workflow:

```text
                         USER
                           |
                           v
                    +-------------+
                    |     LLM     |
                    +------+------+
                           |
                    Tool selection
                           |
              +------------+-------------+
              |                          |
              v                          v
      calculate_area()       calculate_molecular_weight()
              |                          |
              +------------+-------------+
                           |
                    Scientific result
                           |
                           v
                    +-------------+
                    |     LLM     |
                    +------+------+
                           |
                           v
                    FINAL RESPONSE