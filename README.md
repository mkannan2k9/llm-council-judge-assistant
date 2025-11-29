# LLM Council Judge Assistant

A sophisticated automated legal reasoning system built on n8n. This workflow leverages RAG (Retrieval-Augmented Generation) to reference a Constitution and simulates a multi-judge tribunal. It deploys a Multi-Agent Mixture of Experts architecture to analyze cases from distinct philosophical perspectives before deriving a consensus-based verdict through rigorous voting protocols.

## Features

- **Multi-Perspective Analysis**: Simulates three distinct judicial personas (Strict Constitutionalist, Rehabilitative Humanist, Pragmatic Realist) to analyze cases.
- **RAG-Powered Legal Search**: Retrieves relevant legal sections from a Pinecone vector database using Google Gemini Embeddings.
- **Consensus Engine**: Implements a voting mechanism where multiple models rank verdicts to select the most rational outcome.
- **Model Agnostic**: Orchestrates Perplexity Sonar-Reasoning-Pro and Google Gemini 2.5 models to minimize bias.

## Tech Stack

- **Workflow Engine**: n8n
- **Vector Database**: Pinecone
- **LLMs**:
  - Perplexity AI (sonar-reasoning-pro)
  - Google Gemini (gemini-2.5-flash, gemini-2.5-pro)
- **Scripting**: Python (utilized for voting logic and JSON parsing)

## Prerequisites

The following components are required for execution:

1.  **n8n Instance**: A self-hosted or cloud-based instance of n8n.
2.  **API Keys**:
    - Pinecone API Key
    - Google Gemini API Key
    - Perplexity AI API Key
3.  **Vector Database Configuration**:
    - **Mandatory Requirement**: The full text of the Constitution and relevant penal codes must be indexed in the Pinecone vector database **prior to** workflow execution.
    - The embedding model must align with the workflow configuration (default: Google Gemini Embeddings).

## Installation and Configuration

1.  **Import Workflow**:
    - Obtain the JSON file from this repository.
    - In n8n, navigate to **Workflows** > **Import from File** and select the file.
2.  **Credential Configuration**:
    - Access the imported workflow.
    - Update the credential nodes for Pinecone, Google, and Perplexity with valid API keys.
3.  **Vector Store Verification**:
    - Confirm the Pinecone Vector Store node targets the correct index name (e.g., constitution-index).

## Operational Logic

1.  **Trigger**: The workflow initiates via a chat input describing a legal case.
2.  **Retrieval**: The system queries Pinecone to identify relevant constitutional articles and statutes.
3.  **Deliberation**:
    - **9 Parallel Agents** (3 personas x 3 models) independently draft verdicts.
    - **Personas**:
        - *Strict*: Emphasizes textualism and deterrence.
        - *Humanist*: Emphasizes empathy and rehabilitation.
        - *Realist*: Emphasizes efficiency and utilitarianism.
4.  **Voting and Consensus**: A "Chief Justice" layer reviews all 9 verdicts, ranks them, and identifies the statistical mode to determine the most reasonable judgment.
5.  **Output**: The final verdict is rendered with the recommended sentence and associated reasoning.

## License

This project is licensed under the MIT License.

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
