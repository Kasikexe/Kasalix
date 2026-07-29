# Ollama Setup

Ollama is the AI model runtime that powers Kasalix. It handles downloading, loading, and running language models on your hardware.

## Installing Ollama

### Windows

1. Download Ollama from [ollama.com](https://ollama.com)
2. Run the installer (standard Windows installer)
3. Ollama starts automatically as a background service

Verify installation:

```bash
ollama --version
```

You should see output like `ollama version 0.3.0` or similar.

### Other Platforms

Ollama supports macOS and Linux as well. See the [official Ollama documentation](https://github.com/ollama/ollama) for platform-specific instructions.

## Checking Ollama Status

Ollama runs an API server on `http://localhost:11434`. You can verify it's working by:

```bash
# Command line
ollama list

# Or via browser/curl
curl http://localhost:11434/api/tags
```

The Kasalix Server GUI checks this automatically during startup:
- ✅ Green indicator: Ollama is running
- ❌ Red indicator: Ollama is not detected

## Pulling Models

Download models using the `ollama pull` command:

```bash
# Small, fast models (2-3 GB)
ollama pull llama3.2:3b
ollama pull phi:latest
ollama pull qwen2.5:1.5b

# Medium models (4-8 GB)
ollama pull llama3.2
ollama pull mistral
ollama pull gemma2:9b
ollama pull qwen2.5:7b

# Large models (8+ GB)
ollama pull llama3.1:8b
ollama pull mixtral:8x7b
ollama pull deepseek-r1:14b
```

### View Downloaded Models

```bash
ollama list
```

This shows all models you've pulled, their sizes, and modification dates.

## Choosing the Right Model

| Model | Size | RAM Needed | Quality | Speed |
|-------|------|-----------|---------|-------|
| `phi` | 1.5B | 2 GB | Fair | Very Fast |
| `qwen2.5:1.5b` | 1.5B | 2 GB | Fair | Very Fast |
| `llama3.2:3b` | 3B | 4 GB | Good | Fast |
| `qwen2.5:7b` | 7B | 8 GB | Very Good | Moderate |
| `llama3.2` | 8B | 8 GB | Very Good | Moderate |
| `mistral` | 7B | 8 GB | Very Good | Moderate |
| `deepseek-r1:14b` | 14B | 16 GB | Excellent | Slow |

### GPU Acceleration

If you have an NVIDIA GPU with sufficient VRAM, Ollama automatically uses it for acceleration. Check GPU usage with:

```bash
nvidia-smi
```

The Kasalix Server GUI shows GPU utilization, VRAM usage, and GPU name in the dashboard.

## Running Models

Models are loaded into memory when you send the first request. They stay loaded until:

- You explicitly unload them: `ollama stop <model>`
- The server restarts
- Memory pressure causes Ollama to evict them

The Server GUI shows which models are currently loaded under **Running Models**.

## Troubleshooting

**Ollama won't start:**
- Check if another process is using port 11434
- Restart your computer
- Reinstall Ollama

**Model download fails:**
- Check internet connection
- Ensure sufficient disk space
- Try a different model

**Out of memory when running a model:**
- Use a smaller model (e.g., 3B instead of 8B)
- Close other applications to free RAM
- Check if GPU VRAM is sufficient

**Slow responses:**
- Use a smaller model
- Enable GPU acceleration
- Check if other applications are using the GPU
