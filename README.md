docker image to host ollama

docker pull ollama/ollama:0.12.1-rc0

docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
