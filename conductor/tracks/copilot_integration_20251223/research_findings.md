# GitHub Copilot Extensibility Research

This document summarizes the findings from the investigation into GitHub Copilot's extensibility model.

## 1. Primary Extensibility Mechanisms

The primary way to extend GitHub Copilot is through **GitHub Copilot Extensions**. This feature is currently in public preview and allows for integration with a variety of tools and services.

There are two main approaches to building these extensions:

1.  **GitHub App:** This approach allows for interaction with Copilot via APIs and works across multiple environments (GitHub.com, VS Code, Visual Studio).
2.  **Visual Studio Code Extension:** This provides a more deeply integrated, in-client experience specifically for VS Code.

## 2. Key Technologies and Protocols

*   **Model Context Protocol (MCP):** This is a highly relevant technology. MCP provides a standardized way to connect AI models with external data sources and tools. This appears to be the most promising avenue for feeding Conductor's context (`product.md`, `plan.md`, etc.) to Copilot.
*   **Agents and Skillsets:** Copilot allows the creation of "agents" to automate tasks and "skillsets" to provide specialized knowledge. This could be used to create a "Conductor Agent" that guides Copilot based on the project's context.
*   **REST API for Management:** GitHub provides a REST API for managing Copilot usage, which is not directly relevant for the integration logic but could be useful for enterprise-level tooling around Conductor.

## 3. Potential Integration Strategy

Based on this initial research, a potential integration strategy would be to:

1.  Create a **GitHub Copilot Extension** using the **Model Context Protocol (MCP)**.
2.  This extension would act as an MCP server that reads the context from the `conductor/` directory.
3.  The context would then be provided to Copilot, allowing it to generate code that is aware of the project's goals, tech stack, and current plan.
4.  A custom **Copilot Agent** could be developed to leverage this context and provide a more guided experience for the user.

## 4. Next Steps

The next steps should be to:
*   Dive deeper into the documentation for the Model Context Protocol (MCP).
*   Explore the creation of a simple Copilot agent as a proof of concept.
*   Define the architecture for how the Conductor CLI and the Copilot Extension would interact.
