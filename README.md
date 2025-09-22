docker image to host ollama
#
docker pull ollama/ollama
#
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
#
docker exec -it ollama ollama run llama3.2:1b

# Large models (require more RAM/VRAM)
#
docker exec -it ollama ollama run llama3:70b
docker exec -it ollama ollama run codellama:34b
docker exec -it ollama ollama run mistral:7b

# Smaller models (faster, less resource-intensive)
#
docker exec -it ollama ollama run llama3:8b
docker exec -it ollama ollama run phi3:mini
docker exec -it ollama ollama run qwen2:7b

# Specialized models
#
docker exec -it ollama ollama run codellama:7b    # For coding
docker exec -it ollama ollama run vicuna:13b      # Chat optimized
docker exec -it ollama ollama run orca-mini:3b   # Very lightweight

List Available Models: docker exec -it ollama ollama list

Pull a Model Without Running: docker exec -it ollama ollama pull llama3

Remove a Model:docker exec -it ollama ollama rm llama3

Check Model Information: docker exec -it ollama ollama show llama3
