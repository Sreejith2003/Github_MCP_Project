# Github MCP Project

## Overview

**Model Context Protocol (MCP)** is a FastAPI-based server that provides a standardized interface for connecting AI models, tools, and agents with external systems and APIs-especially GitHub. MCP enables seamless integration, orchestration, and automation of workflows involving large language models (LLMs), APIs, and custom tools.

## Features

- **Standardized API** for tool and model integration
- **Extensible**: Add custom tools and endpoints easily
- **Supports Orchestration**: Automate multi-step workflows
- **Real-time Communication**: SSE and streaming support
- **OpenAPI Compatible**: Easy to connect with AI agents and clients
- **GitHub Integration**: Create, update, and delete repositories and files

## Endpoints

- `GET /mcp/tools` - List available tools
- `POST /mcp/invoke` - Invoke a tool (e.g., create repo, add file)
- `POST /mcp/parse_prompt` - Parse natural language to tool calls
- `GET /mcp/sse` - Server-sent events for real-time updates

## Example Usage

- Register tools and APIs for LLMs to use
- Automate repository management, file creation, and more
- Integrate with Copilot, chatbots, or custom agents

## Quick Start

1. Clone the repository
2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Set up your `.env` file with your GitHub Personal Access Token:
   ```
   Github_PAT_API = "YOUR_GITHUB_PAT_API"
   ```
4. Run the FastAPI server:
   ```
   uvicorn github_mcpserver:app --host 0.0.0.0 --port 3000
   ```
5. Access the API docs at [http://localhost:3000/docs](http://localhost:3000/docs)

## Project Structure

- `github_mcpserver.py` - Main FastAPI server with MCP endpoints and GitHub integration
- `.env` - Environment variables
- `.gitignore` - Standard Python and project ignores
- `DockerFile` - Docker configuration for containerized deployment

## Requirements

- Python 3.8+
- FastAPI
- Uvicorn
- PyGithub
- python-dotenv
- pydantic

