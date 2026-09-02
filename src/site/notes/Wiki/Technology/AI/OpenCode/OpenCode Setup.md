---
{"dg-publish":true,"permalink":"/wiki/technology/ai/open-code/open-code-setup/","dg-note-properties":{}}
---


See [[Wiki/Technology/AI/OpenClaw/Kimi K3 Agent Team\|Kimi K3 Agent Team]].

1. Put an OpenRouter API key in `.env` at the repo root (gitignored):

```bash
# Install
npm i -g opencode-ai
```

Set an environment variable for openrouter:
```
OPENROUTER_API_KEY=<YOUR_KEY>
```


# Remote Mobile Setup

```bash
cd ../mnt/user/Media/Documents/Working

git clone https://ethanimproving:<YOUR_KEY>@github.com/ethanimproving/reflexia.git

cd reflexia/.devcontainer 

# Make  setup.sh  executable and run it
chmod +x setup.sh
./setup.sh

# Create .env file 
cat > .env << 'EOF'
OPENROUTER_API_KEY=<YOUR_KEY>
EOF

# Build the image (from repo root)
docker build -t reflexia-dev -f .devcontainer/Dockerfile .


# Run the container (env file + setup)
docker run -dit --name reflexia-dev \
  --restart unless-stopped \
  --env-file .env \
  -e AGENT_BROWSER_EXECUTABLE_PATH=/usr/bin/chromium \
  -v "$(pwd)":/workspace:cached \
  -w /workspace \
  reflexia-dev \
  tail -f /dev/null
  
  
# Run  setup.sh  and  opencode  inside
docker exec -it reflexia-dev bash .devcontainer/setup.sh


# Run opencode
docker exec -it reflexia-dev opencode
```

Here is a docker image to serve as the base for your OpenCode team:
```dockerfile
FROM mcr.microsoft.com/devcontainers/typescript-node:24

WORKDIR /workspace

# Install opencode (Go binary via install script)
RUN curl -fsSL https://opencode.ai/install | bash

# opencode installs to ~/.opencode/bin
ENV PATH="/root/.opencode/bin:${PATH}"

ENV AGENT_BROWSER_EXECUTABLE_PATH=/usr/bin/chromium
```

Here is a docker compose file to run OpenCode in an isolated container on Ubuntu or OpenCode:
```yaml
services:
  opencode:
    build:
      context: .
      dockerfile: .devcontainer/Dockerfile
    container_name: OpenCode
    user:  1000:1000
    cpus: 2
    mem_limit: 8g
    restart: unless-stopped
    env_file:
      - .env
    environment:
      - AGENT_BROWSER_EXECUTABLE_PATH=/usr/bin/chromium
    ports:
      -  4096:4096
    volumes:
      - /mnt/user/appdata/opencode/opencode-data:/home/node/.local/share/opencode
      - /mnt/user/appdata/opencode:/appdata:cached
      - /mnt/user/Media/Documents/Working:/workspace:cached
    working_dir: /workspace
    entrypoint: []
    command: opencode serve --hostname 0.0.0.0 --port 4096
```



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



## Install Docker Compose

1. In Unraid WebGUI → Apps tab
2. Search for "Docker Compose Manager.”
3. Click Install
4. Accept and restart if prompted
5. Go to Docker tab in WebGUI
6. Scroll to the very bottom
7. You'll see "Add Stack" button
8. Click it and enter:
   - Name: supabase
   - Data path: /mnt/user/appdata/supabase
5. Click the gear icon next to your stack
6. Click "Edit Stack"
7. Paste your docker-compose.yml in the compose file box
8. Paste your .env variables in the environment file box
9. Click "Compose Up" to start
10. Enable "Autostart" if desired



</div></div>


In your `opencode.json`, add a llama.cpp provider:
```json
"provider": {
	"llama.cpp": {
	      "npm": "@ai-sdk/openai-compatible",
	      "name": "llama-server (local)",
	      "options": {
	        "baseURL": "http://192.168.1.149:8080/v1"
	      },
	      "models": {
	        "openai/Qwen3.6-27B": {
	          "name": "Qwen3.6 27B",
	          "limit": {
	            "context": 88064,
	            "output": 8192
          }
        }
      }
    },
    "openrouter": {
      "options": { "apiKey": "{Y}" },
      "models": {
        "inclusionai/ling-3.0-flash": {
          "name": "Ling 3.0 Flash",
           "limit": { "context": 262144, "output": 32768 }
        },
        "z-ai/glm-5.3-flash": {
          "name": "GLM-5.3 Flash",
          "limit": { "context": 1048576, "output": 131072 }
        },
        "deepseek/deepseek-v4-flash-0731": {
          "name": "DeepSeek V4 Flash 0731",
          "limit": { "context": 1310720, "output": 943718 }
        },
        "openai/gpt-5.6-luna-pro": {
          "name": "GPT-5.6 Luna Pro",
          "limit": { "context": 1050000, "output": 128000 }
        },
        "qwen/qwen3.8-flash": {
          "name": "Qwen3.8 Flash",
          "limit": { "context": 1000000, "output": 131072 }
        }
      }
    },
}
```

---
[^1]: “OpenCode.” *App Store*, 2026. 