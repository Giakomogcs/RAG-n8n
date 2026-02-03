# Antigravity n8n Project

This project integrates Antigravity (AI Agent) with n8n using the Model Context Protocol (MCP) to automate workflow creation and management.

## 🚀 Setup Guide

### 1. Prerequisites
*   **Node.js**: Installed and available in your PATH.
*   **n8n**: Installed and running on `http://localhost:5678` (default).
    ```powershell
    # Start n8n if not running
    n8n start
    ```

### 2. Installation
We use the `n8n-mcp` server to connect the AI with your n8n instance and `n8n-skills` for enhanced context.

1.  **Install n8n-mcp globally:**
    ```powershell
    npm install -g n8n-mcp
    ```

2.  **Clone n8n-skills:**
    Cloned into the project root for reference.
    ```powershell
    git clone https://github.com/czlonkowski/n8n-skills.git
    ```

### 3. Configuration (`mcp_config.json`)

The MCP server needs to be configured in your local user settings. 

**File Location:** `C:\Users\<USER>\.gemini\antigravity\mcp_config.json`

**Configuration Content:**
```json
{
  "mcpServers": {
    "n8n-mcp": {
      "command": "node",
      "args": [
        "C:\\Users\\<USER>\\AppData\\Roaming\\npm\\node_modules\\n8n-mcp\\dist\\mcp\\index.js"
      ],
      "env": {
        "MCP_MODE": "stdio",
        "LOG_LEVEL": "error",
        "DISABLE_CONSOLE_OUTPUT": "true",
        "N8N_API_URL": "http://localhost:5678",
        "N8N_BASE_URL": "http://localhost:5678",
        "N8N_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```
*Replace `<USER>` with your Windows username.*

### 4. Guide for the Agent (`Antigravity.md`)
We created `Antigravity.md` in the project root. This file contains specific instructions, tool definitions, and skill references that the AI uses to understand how to interact with n8n.

## ⚠️ Troubleshooting

### Error: "invalid character 'â' looking for beginning of value"
**Cause:** This usually happens if the `mcp_config.json` file is saved with a specific encoding (like UTF-8 BOM) that the MCP client doesn't like, or if there is corruption in the file.
**Solution:** Re-save `mcp_config.json` as plain **UTF-8** (without BOM) or let the agent recreate the file for you.

### Connection Refused (dial tcp [::1]:5678)
**Cause:** n8n is not running.
**Solution:** Open a terminal and run `n8n start`.

## 📂 Key Files
*   `Antigravity.md`: Main instruction set for the AI.
*   `prompts.txt`: User prompts history.
*   `n8n-skills/`: Directory containing specific skill documentation.
