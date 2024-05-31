---
title: 本地搭建知识库
date: 2024-04-07 14:19
---

pip3 install llama-index-core llama-index-readers-file llama-index-llms-ollama llama-index-embeddings-huggingface

sudo iptables -A INPUT -p tcp –dport 3000 -j ACCEPT

sudo iptables -I INPUT -p tcp --dport 3000 -j ACCEPT 

```
Environment="OLLAMA_HOST=0.0.0.0:11434"
```

```shell
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v ./open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:latest
```



开源Agent项目列表

```shell
https://github.com/vercel/ai-chatbot



https://github.com/zwq2018/Data-Copilot


https://github.com/leptonai/search_with_lepton


https://github.com/ItzCrazyKns/Perplexica.git


http://github.com/miurla/morphic 

https://github.com/alibaba/sreworks-ext
```
