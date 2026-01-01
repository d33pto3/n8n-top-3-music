# 🎵 n8n Top 3 Music Workflow

This project runs an **n8n** instance in Docker, connected to a **Neon Postgres** database. It includes a workflow that fetches daily top music tracks and sends them via email with YouTube links.

## 🚀 Getting Started

### 1. Prerequisites
- Docker and Docker Compose installed.
- A Neon.tech (or other Postgres) database URL.

### 2. Setup
1.  **Environment Variables**: The `.env` file is already configured with your Neon database details.
2.  **Start n8n**:
    ```bash
    docker compose up -d
    ```
3.  **Access n8n**: Open [http://localhost:5678](http://localhost:5678) in your browser.

### 3. Importing the Workflow
1.  In the n8n UI, go to **Workflows**.
2.  Click **Add Workflow** (top right) > **Import from File**.
3.  Select the `top-3-music-n8n.json` file from this directory.

### 4. Configuration
To make the workflow fully functional, you need to configure two things inside the n8n editor:

- **Last.fm API**: 
    - The `HTTP Request` node uses a Last.fm API key.
    - If you want to use your own, get one from [Last.fm API](https://www.last.fm/api) and update the URL in the node.
- **Gmail Credentials**:
    - Click on the **Send a message** (Gmail) node.
    - Click on **Select Credentials** > **Create New**.
    - Follow the prompts to set up **OAuth2** for your Gmail account.
    - *Tip: You may need to create a project in the Google Cloud Console.*

## 🔒 Security
- **Encryption Key**: A secure `N8N_ENCRYPTION_KEY` has been generated and saved in your `.env`. This protects your saved credentials.
- **Database**: The instance is connected to Neon Postgres via SSL for security.

## 🛠 Project Structure
- `docker-compose.yml`: Defines the n8n service and its volume.
- `.env`: Contains database secrets and configuration.
- `top-3-music-n8n.json`: The exported workflow ready for import.
- `Dockerfile`: Standard n8n image setup.
