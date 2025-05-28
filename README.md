# Interview Question

This repository is a **15-20 minutes** exercise for the Data Eng-Sandpit interview about LLM.

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

Your two main tasks are to:

#### 1. Configure Docker Containers to Use GPUs
- Modify the provided Compose file to enable **GPU support**.
- Create two isolated **Ollama containers**, each configured to run a different LLM.
- Assign appropriate **GPU resources** and **ports** to each container.
- Mount dedicated **Docker volumes** to persist model data separately.

Your final Compose file should be saved as: 
`docker-compose.yml`


**Checkpoint A**: Launch **two** isolated Ollama containers using CPU-only configuration. (You may skip this and proceed directly to GPU setup if confident.)

**Checkpoint B**: Show the ability to configure the allocation of GPUs in each container appropriately.

**Checkpoint C**: Demonstrate how to list available GPUs on the VM and within each container.

**Checkpoint D**: Prove understanding of **Docker networking and port binding**, especially when running multiple containers from the same base image of Ollama.

#### 2. Deploy and Run Each LLM in Its Own Container

Each model should be deployed in its own environment, running simultaneously with GPU isolation and volume persistence.

**Checkpoint E**: Access each container and deploy the specified LLM using Ollama.

**Checkpoint F**: Demonstrate how to monitor **GPU and memory usage** while running inference to validate correct resource allocation.

---

## Configuration Requirements

You are required to deploy two separate Docker containers, each running an instance of Ollama configured with a different LLM model.

**Regardless of machine portability**, your configuration **must** ensure that:
- Each container is assigned **dedicated GPU resources** appropriate for the model it serves.
- The entire GPU capacity of the VM (4 × Tesla T4) is **fully** utilised across both containers.
- Each container has its own **dedicated volume** to prevent model/data overlap.
- Containers are reachable via **distinct external ports**.

Below are the details of each container.

#### Container 1: `ollama_small`

- **Container name**: `ollama_small`
- **Docker volume**: `ollama_small_volume`, mounted to `/root/.ollama`
- **Model to load**: `qwen2.5:3b`
- **GPU allocation**: 1 × Tesla T4

#### Container 2: `ollama_large`

- **Container name**: `ollama_large`
- **Docker volume**: `ollama_large_volume`, mounted to `/root/.ollama`
- **Model to load**: `gemma3:27b`
- **GPU allocation**: 3 × Tesla T4

---

## Technical Guidelines

- Use the `deploy.resources.reservations.devices` section in your Docker Compose file to specify GPU requirements:

## Demonstrate the Success of Configuration and Deployment

To ensure that your GPU configuration and container deployments are functioning correctly, you should be familiar with the necessary commands to:
- Verify the availability of GPUs on the host VM and within each container
- Access the shell of each running container 

You are also required to demonstrate that the LLMs deployed in each container are actively utilizing their assigned GPUs for inference and answer generation. 

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
