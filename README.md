# localLLM
Enabling users to run LLMs locally on their own GPUs and skip the expensive APIs

# Test docker for Nvidia
docker run --rm --gpus all myimage nvidia-smi

# Setup Ollama
docker run -d --gpus all --name ollama -p 11434:11434 -v ollama_data:/root/.ollama ollama/ollama

# Pull a model (Qwen 3.5 2B — current Ollama-library tag, ~1.6GB)
docker exec ollama ollama pull qwen3.6:27b



# Test it with curl
curl http://localhost:11434/api/generate -d '{
  "model": "qwen3.6:27b",
  "prompt": "How do you spell relief?",
  "stream": false
}'