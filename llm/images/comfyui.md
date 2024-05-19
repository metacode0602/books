# ConmfyUI安装部署指南

## 安装

```shell
git clone https://github.com/comfyanonymous/ComfyUI.git

## Nvida
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu121

## AMD GPUs (Linux only)
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm6.0

## 安装依赖
pip install -r requirements.txt

## 启动服务
python main.py --listen 172.30.1.130
```

[Pretrained Models &mdash; Sentence-Transformers documentation](https://www.sbert.net/docs/pretrained_models.html)

## Image & Text-Models[图文模型](https://www.sbert.net/docs/pretrained_models.html#image-text-models "Permalink to this headline")

The following models can embed images and text into a joint vector space. See [Image Search](https://www.sbert.net/examples/applications/image-search/README.html) for more details how to use for text2image-search, image2image-search, image clustering, and zero-shot image classification.

The following models are available with their respective Top 1 accuracy on zero-shot ImageNet validation dataset.

| Model                                                                       | Top 1 Performance |
| --------------------------------------------------------------------------- | ----------------- |
| [clip-ViT-B-32](https://huggingface.co/sentence-transformers/clip-ViT-B-32) | 63.3              |
| [clip-ViT-B-16](https://huggingface.co/sentence-transformers/clip-ViT-B-16) | 68.1              |
| [clip-ViT-L-14](https://huggingface.co/sentence-transformers/clip-ViT-L-14) | 75.4              |

We further provide this multilingual text-image model:

- **clip-ViT-B-32-multilingual-v1** - Multilingual text encoder for the [clip-ViT-B-32](https://huggingface.co/sentence-transformers/clip-ViT-B-32) model using [Multilingual Knowledge Distillation](https://arxiv.org/abs/2004.09813). This model can encode text in 50+ languages to match the image vectors from the [clip-ViT-B-32](https://huggingface.co/sentence-transformers/clip-ViT-B-32) model.
