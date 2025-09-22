# Ollama Docker Setup

Run large language models locally using Ollama in Docker.

## Quick Start

### 1. Pull the Ollama Docker Image
```bash
docker pull ollama/ollama
```

### 2. Run Ollama Container
```bash
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

### 3. Run Your First Model
```bash
docker exec -it ollama ollama run llama3.2:1b
```

## Available Models

### Large Models (require more RAM/VRAM)
```bash
docker exec -it ollama ollama run llama3:70b
docker exec -it ollama ollama run codellama:34b
docker exec -it ollama ollama run mistral:7b
```

### Smaller Models (faster, less resource-intensive)
```bash
docker exec -it ollama ollama run llama3:8b
docker exec -it ollama ollama run phi3:mini
docker exec -it ollama ollama run qwen2:7b
docker exec -it ollama ollama run gemma3:270m
```

### Specialized Models
```bash
docker exec -it ollama ollama run codellama:7b    # For coding
docker exec -it ollama ollama run vicuna:13b      # Chat optimized
docker exec -it ollama ollama run orca-mini:3b   # Very lightweight
```

## Model Management

### List Available Models
```bash
docker exec -it ollama ollama list
```

### Pull a Model Without Running
```bash
docker exec -it ollama ollama pull llama3
```

### Remove a Model
```bash
docker exec -it ollama ollama rm llama3
```

### Check Model Information
```bash
docker exec -it ollama ollama show llama3
```

## API Access

Once running, you can access the Ollama API at `http://localhost:11434`

### Example API Usage
```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2:1b",
  "prompt": "Why is the sky blue?"
}'
```

## GPU Support

For NVIDIA GPU support, use:
```bash
docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

## System Requirements

- **Small models (1-3B)**: 4GB RAM
- **Medium models (7-8B)**: 8GB RAM  
- **Large models (13B+)**: 16GB+ RAM
- **GPU**: NVIDIA GPU with 6GB+ VRAM recommended

## Troubleshooting

### Container not starting?
```bash
docker logs ollama
```

### Network issues?
```bash
docker restart ollama
```

### Check container status
```bash
docker ps
```

## Contributing

Feel free to submit issues and enhancement requests!
