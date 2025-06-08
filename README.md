# GitHub MCP (Model Context Protocol) Server

A FastAPI-based MCP server implementation for GitHub operations. This server provides a bridge between AI models and GitHub, allowing automated repository and file management through a standardized API.

## Features

- Create/delete GitHub repositories
- Create/update/delete files in repositories
- Get file contents from repositories
- Push entire project directories
- Built-in rate limiting handling
- Support for large files (up to 100MB)
- Natural language command parsing
- Server-Sent Events (SSE) support

## Available Tools

1. **create_repository**
   - Create new GitHub repositories
   - Optional: Set private/public status
   - Optional: Initialize with README

2. **create_file**
   - Create new files in repositories
   - Support for all file types
   - Custom commit messages

3. **update_file**
   - Update existing files
   - Preserves file history
   - Custom commit messages

4. **delete_file**
   - Remove files from repositories
   - Custom commit messages

5. **delete_repository**
   - Delete entire repositories
   - Safety checks included

6. **get_file**
   - Retrieve file contents
   - Support for all text files
   - Includes file metadata

7. **push_project**
   - Push entire project directories
   - Intelligent file filtering
   - Handles large projects
   - Automatic retries for rate limits

## Setup

1. Clone the repository
2. Install dependencies:
   `ash
   pip install -r requirements.txt
   `

3. Create a .env file with your GitHub PAT:
   `env
   Github_PAT_API=your_github_pat_here
   `

4. Run the server:
   `ash
   python github_mcpserver.py
   `

## Usage Examples

### Create a Repository
`json
{
    "tool": "create_repository",
    "inputs": {
        "repo_name": "my-new-repo",
        "private": true,
        "initialize_readme": true
    }
}
`

### Create a File
`json
{
    "tool": "create_file",
    "inputs": {
        "repo_name": "owner/repo",
        "file_path": "src/main.py",
        "content": "print('Hello, World!')",
        "commit_message": "Add main script"
    }
}
`

### Push a Project
`json
{
    "tool": "push_project",
    "inputs": {
        "repo_name": "owner/repo",
        "project_path": "/path/to/project",
        "commit_message": "Initial project upload"
    }
}
`

## Natural Language Support

The server includes natural language parsing for commands. Examples:

- "Create a repository named test-repo"
- "Create a file main.py in test-repo with content: print('Hello')"
- "Update the file README.md in test-repo with content from local-readme.md"
- "Delete the file config.json in test-repo"

## Error Handling

- Automatic retries for rate limits
- Detailed error messages
- Size limit checks
- File existence validation
- Encoding handling for binary files

## Security Features

- GitHub PAT required
- File size limits
- Excluded sensitive directories
- Error message sanitization

## Contributing

Feel free to submit issues and enhancement requests!

## License

MIT License