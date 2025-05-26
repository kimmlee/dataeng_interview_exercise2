# Interview Question

This repository is an exercise for the Data Eng-Sandpit interview about LLM.

## VM Details & Pre-Installed Tools

You have been provided with a dedicated VM that includes:

- **4× NVIDIA Tesla T4 GPUs**
- **Docker** (pre-installed)
- **Ollama** (pre-installed)
- **NVIDIA Container Toolkit** (configured for Docker GPU access)

---

## Background

Imagine you're a Full-Stack Data Engineer supporting researchers and HDR students at ielab, UQ. They are working on **Agentic Retrieval-Augmented Generation (RAG)** projects that involve multiple LLMs. Your task is to deploy these models in a way that isolates them for performance and compatibility testing.

The target models for this task are:

1. **qwen2.5:3b**
2. **gemma3:27b**


## Your Task

You are provided with a starting Docker Compose file:  
`docker-compose-cpu.yml`

Your task is to:

- Modify this file to enable **GPU usage** via Docker
- Create two isolated **Ollama containers**, each running one of the LLMs above
- Assign appropriate **GPU resources** and **ports**
- Mount dedicated **volumes** to preserve model data separately

Your final Compose file must be named:
`docker-compose.yml`

---

## Configuration Requirements

You must deploy two separate containers with the following configurations:

### Container 1: `ollama_small`

- **Container name**: `ollama_small`
- **Docker volume**: `ollama_small_volume`, mounted to `/root/.ollama`
- **Model to load**: `qwen2.5:3b`
- **GPU allocation**: 1 × Tesla T4
- **Host port**: `11434`
- **Container port**: `11434`

### Container 2: `ollama_large`

- **Container name**: `ollama_large`
- **Docker volume**: `ollama_large_volume`, mounted to `/root/.ollama`
- **Model to load**: `gemma3:27b`
- **GPU allocation**: 3 × Tesla T4
- **Host port**: `21434`
- **Container port**: `11434`

---

## Technical Guidelines

- Use the `deploy.resources.reservations.devices` section in your Docker Compose file to specify GPU requirements:
  ```yaml

## License 

```
MIT License

Copyright (c) 2023 The University of Queensland

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```