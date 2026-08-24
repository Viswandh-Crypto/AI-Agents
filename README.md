# AI-Agents

# Multi-Agent Technical Blog Writer

A Python-based AI agent system that autonomously plans, validates, and writes high-quality technical blog posts. Built using the `google.adk` (Agent Development Kit) and Gemini models.

## Features

- **Multi-Agent Architecture**: Separates concerns into specialized agents (Planner and Writer).
- **Self-Correction & Validation**: Uses `LoopAgent` to validate outlines and drafts, retrying automatically if the output doesn't meet the specified criteria.
- **Tool-Calling Workflow**: The root agent coordinates the process by calling the sub-agents as distinct tools.
- **Targeted Output**: Specifically instructed to write for software engineers, providing code snippets and explaining the "how" and "why."

## Prerequisites

- Python 3.9+
- `google-adk==2.2.0`
- `python-dotenv`

## Setup

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd <your-repo-name>
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure Environment Variables:**
   Create a `.env` file in the project root and add your Google API key (do not commit this file to GitHub):
   ```env
   GOOGLE_API_KEY=your_google_api_key_here
   MODEL=gemini-flash-latest # Optional, defaults to gemini-flash-latest
   ```

## Architecture

- **Blogger (Root Agent)**: Takes the user's topic and orchestrates the workflow.
- **RobustBlogPlanner**: A loop agent that combines the `BlogPlanner` (creates an outline) and `OutlineValidationChecker` (ensures structural integrity).
- **RobustBlogWriter**: A loop agent that combines the `BlogWriter` (drafts the post) and `BlogPostValidationChecker` (ensures technical clarity).

## Usage

Import the `root_agent` from your module and pass it a topic:

```python
from agent import root_agent

# Example usage
response = root_agent.run("The benefits of Retrieval-Augmented Generation (RAG) in Enterprise Apps")
print(response)
```
