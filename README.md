# GitHub Repo Q&A Agent – Docker MCP Toolkit Example

This repository demonstrates a **real-world developer setup** for building an AI agent with the **Docker MCP Toolkit** that can connect to a GitHub repository and answer questions about its contents.  

The agent:
- Summarizes repositories
- Explains functions and modules
- Finds where specific API calls are made
- Retrieves code references with file/line details  

It uses:
- **Docker MCP Toolkit** for tool integration (GitHub API)
- **Docker Compose** for orchestration
- **OpenAI GPT-4o** for reasoning and natural language responses

---

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) & [Docker Compose](https://docs.docker.com/compose/)
- Python 3.10+
- [OpenAI API key](https://platform.openai.com/account/api-keys)
- [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) with at least:
  - `repo`
  - `read:org` (for private repos)

---

## Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

### 2. Start the MCP Gateway
```bash
docker compose up -d mcp-gateway-github
```
### 3. Configure GitHub Access
```bash
docker mcp secret set github.personal_access_token=<YOUR_GITHUB_TOKEN>
```
### 4. Create `.env` for OpenAI
Create a file named `.env` in the root directory and add your OpenAI API key:  

```env
OPENAI_API_KEY=sk-********************************
```
### 5. Install dependencies
Create and activate a Python virtual environment, then install dependencies from `requirements.txt`:  

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.tx
```
### 6. Run the agent
```bash
python app.py
```
### 7. Ask questions
Example usage:  

```text
Enter your query: Summarize https://github.com/owner/repo
```

## Extending the Setup

- Add more MCP connectors (e.g., Jira, Slack, Databases) by adding new services to `docker-compose.yml`.
- Containerize the agent itself for a fully portable deployment.
- Integrate with CI/CD pipelines using the same Compose file.
