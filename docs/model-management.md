# Model Management

Kasalix works with any model available in Ollama. This guide covers how to manage, switch, and optimize AI models.

## Available Models

To see which models are available on your server, use the **Model Selector** in the chat interface, or check via command line:

```bash
ollama list
```

The Server GUI also shows currently **loaded** models in the dashboard under **Running Models**.

## Selecting a Model

### In the Web UI

The model selector is located at the top of the chat window. Click it to see all installed models. Select one to switch — the next message will use the new model.

### In the Server GUI

The **Running Models** card shows which models are actively loaded in Ollama's memory. This helps you see what's consuming GPU VRAM.

### Via API

```bash
curl -X POST http://localhost:3001/api/chat \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{
    "model": "llama3.2",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

## Installing New Models

### Via Ollama CLI (Recommended)

```bash
ollama pull <model-name>
```

Examples:

```bash
ollama pull llama3.2:3b    # Small, fast (~2 GB)
ollama pull mistral         # Medium (~4 GB)
ollama pull llama3.1:8b    # Large (~4.7 GB)
ollama pull deepseek-r1:14b # Very large (~9 GB)
```

### Via the Web UI (Coming Soon)

Model installation directly from the web interface is planned for a future release.

## Model Categories

### General Purpose

Best for everyday chat, questions, and assistance.

| Model | Size | Strengths |
|-------|------|-----------|
| `llama3.2` | 8B | Well-rounded, good instruction following |
| `llama3.2:3b` | 3B | Fast, lightweight, good for basic tasks |
| `mistral` | 7B | Excellent reasoning, strong instruction following |
| `qwen2.5:7b` | 7B | Strong multilingual support, good coding |

### Code & Technical

Optimized for programming, debugging, and technical tasks.

| Model | Size | Strengths |
|-------|------|-----------|
| `deepseek-coder` | 6.7B | Excellent code generation |
| `codellama` | 7B | Code completion and analysis |
| `qwen2.5-coder` | 7B | Strong coding + general abilities |

### Specialized

| Model | Size | Use Case |
|-------|------|----------|
| `llama3.2-vision` | 11B | Image analysis (with Ollama) |
| `deepseek-r1` | 14B | Advanced reasoning, math |
| `phi` | 2.7B | Lightweight, good for CPU-only |

## Memory Management

Models consume varying amounts of RAM/VRAM:

| Model Size | RAM (CPU mode) | VRAM (GPU mode) |
|-----------|----------------|-----------------|
| 1.5B | ~3 GB | ~2 GB |
| 3B | ~6 GB | ~3 GB |
| 7B | ~12 GB | ~6 GB |
| 8B | ~14 GB | ~7 GB |
| 14B | ~24 GB | ~12 GB |
| 70B | ~120 GB | ~60 GB |

### Tips

- **CPU-only**: Use models ≤3B for acceptable speed
- **8 GB VRAM**: Can run 7B models comfortably
- **12 GB VRAM**: Can run 8B-14B models
- **Unused models**: Ollama automatically unloads models after inactivity
- **Manual unload**: `ollama stop <model-name>` to free memory immediately

## Modelfiles (Custom Models)

Ollama allows creating custom models using Modelfiles. This lets you:

- Adjust system prompts
- Set temperature and other parameters
- Add custom stop tokens

Example Modelfile:

```dockerfile
FROM llama3.2

# Set parameters
PARAMETER temperature 0.7
PARAMETER top_p 0.9

# Set system prompt
SYSTEM "You are a helpful coding assistant. Always provide code examples."
```

Create and use:

```bash
ollama create my-coder -f Modelfile
ollama run my-coder
```

The custom model will appear in Kasalix's model selector.

## Model Performance

### Quantization

Ollama automatically uses quantized versions of models (Q4_K_M by default), which reduces memory usage with minimal quality loss.

| Quantization | Quality | Memory | Speed |
|-------------|---------|--------|-------|
| Q2_K | Lowest | Lowest | Fastest |
| Q3_K | Low | Low | Fast |
| **Q4_K_M** | **Good** | **Good** | **Balanced (default)** |
| Q5_K_M | Better | Higher | Slower |
| Q8_0 | Best | Highest | Slowest |
| F16 | Original | Max | Slow |

### Context Length

You can adjust the context window (how much the model remembers):

```bash
# Set in environment
set OLLAMA_CONTEXT_LENGTH=8192

# Or in Modelfile
PARAMETER num_ctx 4096
```

Larger context uses more memory. Default is 2048 tokens.

## Troubleshooting

**Model not appearing in the selector:**
- Run `ollama list` to confirm it's installed
- Refresh the web page
- Restart the Kasalix server

**"Model not found" error:**
- The model name might be incorrect
- Some models require specific tags (e.g., `llama3.2:latest`)
- Pull the model with `ollama pull <exact-name>`

**Out of memory with a medium model:**
- Try a quantized version
- Reduce context length
- Close other GPU applications
- Use a smaller model variant
