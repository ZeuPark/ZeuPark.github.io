---
title: "Deploying LLM Services on a Minimal Server: Navigating the Constraints"  
date: 2025-06-18  
layout: single  
tags:  
  - llm  
  - project  
  - project  
excerpt: "This post explores the challenges and solutions for deploying LLM services on small, cost-constrained servers like Oracle Cloud Free Tier — a crucial skill for resource-limited developers."  
---

## Background  

In today’s AI landscape, there's a rising demand for engineers who can not only **fine-tune large language models (LLMs)** but also **deploy and serve** them in real-world applications.  

> However, as a student and an independent developer without corporate infrastructure or budget, deploying an LLM service feels nearly impossible.  

Most job postings today expect hands-on experience in deploying AI applications — especially with **LLM backends** integrated into full-stack services.  

---

## The Challenge  

Platforms like AWS or Azure are powerful, but their **costs are prohibitive** for individuals. Even Oracle Cloud Free Tier offers only:  
- 1 OCPU, 1 GB RAM for the free instance  
- No GPU  
- Strict resource limits (network, storage, ports)  

This means that deploying even a quantized LLM becomes a significant engineering challenge.  

---

## My Deployment Constraints  

To operate within these constraints, I focused on three goals:  
1. **Quantize and compress the LLM**  
2. **Keep the backend + DB + frontend stack minimal**  
3. **Run everything on a single Free Tier VM (Oracle)**  

---

## My Strategy  

### 1. Model Optimization  
I used:  
- **TinyLlama**, **Phi-2** or other 1~2B parameter models  
- 4-bit quantization with tools like `AutoGPTQ` or `GGUF`  
- Inference via CPU-based runtime (e.g. llama.cpp or vLLM on float16)  

### 2. Minimal Architecture  
- **FastAPI** backend  
- **SQLite or small PostgreSQL DB**  
- **React frontend hosted on Vercel**  
- All server-side components deployed in Oracle's free instance  

This configuration made it *just barely possible* to serve LLM responses on demand.  

---

## What I Learned  

- **Real constraints teach real skills**. Working within tight limits forced me to think deeply about memory, latency, and efficiency.  
- **Quantization isn't just an optimization — it's a necessity** in low-resource environments.  
- **A small, working deployment proves more than a massive, unserved model**.  

I realized that my strength isn't running the biggest model — it's running an efficient one **on zero budget**.  

---

## Reflection  

At first, I felt discouraged seeing companies ask for deployment experience while I had no access to paid servers. But that challenge became the catalyst for this learning process.  

Now, I believe:  
> Showing that I served an optimized model on a constrained platform is more impressive than spinning up a 40GB GPU instance with someone else's credit card.  

---

## Next Steps  

- Share deployment architecture diagrams in future posts  
- Measure actual performance (latency, memory) on Free Tier  
- Prepare a GitHub repo to showcase this fully working LLM service  

---
