### 配置环境变量

##### 安装Conda

通常，Conda会与Anaconda或Miniconda一起安装。Anaconda是一个面向科学计算的Python发行版，包含了Conda、Python以及一系列预安装的库和工具。Miniconda是一个更轻量级的发行版，只包含Conda和必要的Python。

基本命令

Conda是一个开源的包管理系统和环境管理系统，它主要用于安装和管理软件包以及创建和维护不同的软件环境。以下是Conda的一些常用使用方法：

### 安装Conda

通常，Conda会与Anaconda或Miniconda一起安装。Anaconda是一个面向科学计算的Python发行版，包含了Conda、Python以及一系列预安装的库和工具。Miniconda是一个更轻量级的发行版，只包含Conda和必要的Python。

##### 安装

```bash
## 下载
curl --output anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2024.02-1-Linux-x86_64.sh

## 进行安装
bash anaconda.sh 

## 如果在安装过程中出现以下错误：
## If you'd prefer that conda's base environment not be activated on startup,
## run the following command when conda is activated:
## conda config --set auto_activate_base false

## 执行以下脚本：
eval "$(/root/anaconda3/bin/conda shell.bash hook)" 

## 激活conda环境
source ~/.bashrc 
```

### 基本命令

- **更新Conda**：
  
  ```bash
  conda update -n base -c defaults conda
  ```

- **创建新的环境**：
  
  ```bash
  conda create --name myenv python=3.10
  ```

- **激活环境**：
  
  ```bash
  conda activate myenv
  ```

- **退出环境**：
  
  ```bash
  conda deactivate
  ```

- **列出所有环境**：
  
  ```bash
  conda env list
  ```

- **删除环境**：
  
  ```bash
  conda env remove --name myenv
  ```

### 管理软件包

- **在当前环境中安装软件包**：
  
  ```bash
  conda install numpy pandas
  ```

- **在特定环境中安装软件包**（先激活环境）：
  
  ```bash
  conda install -n myenv numpy pandas
  ```

- **更新软件包**：
  
  ```bash
  conda update numpy
  ```

- **卸载软件包**：
  
  ```bash
  conda remove numpy
  ```

### 管理依赖和通道

- **列出当前环境中的软件包**：
  
  ```bash
  conda list
  ```

- **搜索软件包**：
  
  ```bash
  conda search scipy
  ```

- **使用特定通道的软件包**（例如，使用conda-forge）：
  
  ```bash
  conda install -c conda-forge scipy
  ```

### 配置Conda

- **设置Conda的通道优先级**：
  
  ```bash
  conda config --add channels conda-forge
  ```

- **查看Conda配置**：
  
  ```bash
  conda config --show
  ```

### 环境导出与共享

- **导出当前环境的列表**（可以用于分享或迁移）：
  
  ```bash
  conda list --export > environment.yml
  ```

- **从列表文件创建环境**：
  
  ```bash
  conda create --name myenv --file requirements.txt
  ```

### 清理空间

- **清理未使用的软件包和缓存**：
  
  ```bash
  conda clean --all
  ```

Conda是一个非常强大的工具，可以用于管理复杂的Python项目依赖。上述命令覆盖了Conda的大部分基本用法，但是Conda的功能远不止这些。对于更高级的使用，建议查阅[官方文档](https://docs.conda.io/projects/conda/en/latest/)。

## 前期准备

```shell
sudo apt-get install libgoogle-perftools4 libtcmalloc-minimal4 libgl1 libglib2.0-0

sudo apt install libgl1-mesa-glx
```

## 执行安装

```shell
conda create --name sdwebui python=3.10

conda activate sdwebui

wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh

sh webui.sh

cd stable-diffusion-webui

python -m venv venv


pip install -r requirements.txt

./webui.sh --skip-torch-cuda-test --listen --share


## 如果没有安装GPU，执行以下命令：

./webui.sh --skip-torch-cuda-test


## 后台启动，并可以安装扩展

nohup ./webui.sh --listen --skip-torch-cuda-test --share --enable-insecure-extension-access &
```

#### 下载模型

##### 使用huggingface下载模型

假设`stable-diffusion-webui`的git 目录是`/home/user/github/stable-diffusion-webui`

```bash
## 下载完成后，需要放在 stable-diffusion-webui/models/Stable-diffusion 目录
$ huggingface-cli download  Stable-diffusion/v1-5-pruned-emaonly.safetensors --local-dir Stable-diffusion/v1-5-pruned-emaonly.safetensors


## 下载完成后，需要将sentence-transformers放在 stable-diffusion-webui 目录下，跟webui.sh 同级，否则会启动报错。
$ huggingface-cli download sentence-transformers/clip-ViT-B-32  --local-dir sentence-transformers/clip-ViT-B-32


$ huggingface-cli download sentence-transformers/clip-ViT-B-32-multilingual-v1  --local-dir sentence-transformers/clip-ViT-B-32-multilingual-v1


$ huggingface-cli download openai/clip-vit-large-patch14   --local-dir openai/clip-vit-large-patch14
```

完成后的目录结构如下：

```shell
├── cache
├── CHANGELOG.md
├── CITATION.cff
├── CODEOWNERS
├── configs
├── config_states
├── embeddings
├── environment-wsl2.yaml
├── extensions
├── extensions-builtin
├── html
├── javascript
├── launch.py
├── LICENSE.txt
├── localizations
├── models
├── modules
├── openai
├── outputs
├── package.json
├── params.txt
├── __pycache__
├── pyproject.toml
├── README.md
├── repositories
├── requirements_npu.txt
├── requirements-test.txt
├── requirements.txt
├── requirements_versions.txt
├── screenshot.png
├── script.js
├── scripts
├── sentence-transformers
├── style.css
├── test
├── textual_inversion_templates
├── _typos.toml
├── ui-config.json
├── venv
├── webui.bat
├── webui-macos-env.sh
├── webui.py
├── webui.sh
```

### extensions目录结构

```bash
.
├── canvas-zoom
│   ├── detect_extension.py
│   ├── dist
│   ├── install.py
│   ├── javascript
│   ├── README.MD
│   ├── scripts
│   └── style.css
├── extensions.txt
├── facechain
│   ├── app.py
│   ├── doc
│   ├── dwpose
│   ├── facechain
│   ├── facechain_adapter
│   ├── facechain_animate
│   ├── facechain_demo.ipynb
│   ├── face_module
│   ├── install.py
│   ├── LICENSE
│   ├── onnx_helper.py
│   ├── onnx_ijbc.py
│   ├── partial_fc_exp.py
│   ├── poses
│   ├── __pycache__
│   ├── README.md
│   ├── README_ZH.md
│   ├── requirements.txt
│   ├── resources
│   ├── run_inference_inpaint.py
│   ├── run_inference.py
│   ├── run_inference_talkinghead.py
│   ├── run_inference_tryon.py
│   ├── scripts
│   ├── style_image
│   ├── styles
│   └── train_lora.sh
├── multidiffusion-upscaler-for-automatic1111
│   ├── javascript
│   ├── LICENSE
│   ├── README.md
│   ├── scripts
│   ├── tile_methods
│   └── tile_utils
├── put extensions here.txt
├── SadTalker
│   ├── app_sadtalker.py
│   ├── cog.yaml
│   ├── docs
│   ├── examples
│   ├── inference.py
│   ├── launcher.py
│   ├── LICENSE
│   ├── predict.py
│   ├── __pycache__
│   ├── quick_demo.ipynb
│   ├── README.md
│   ├── req.txt
│   ├── requirements3d.txt
│   ├── requirements.txt
│   ├── scripts
│   ├── src
│   ├── webui.bat
│   └── webui.sh
├── sd-webui-controlnet
│   ├── annotator
│   ├── example
│   ├── extract_controlnet_diff.py
│   ├── extract_controlnet.py
│   ├── install.py
│   ├── internal_controlnet
│   ├── javascript
│   ├── LICENSE
│   ├── models
│   ├── patch_version.py
│   ├── preload.py
│   ├── __pycache__
│   ├── pyproject.toml
│   ├── README.md
│   ├── requirements.txt
│   ├── samples
│   ├── scripts
│   ├── style.css
│   ├── tests
│   ├── unit_tests
│   └── web_tests
├── sd-webui-EasyPhoto
│   ├── api_test
│   ├── COVENANT.md
│   ├── COVENANT_zh-CN.md
│   ├── images
│   ├── install.py
│   ├── javascript
│   ├── LICENSE
│   ├── models
│   ├── README.md
│   ├── README_zh-CN.md
│   └── scripts
├── sd-webui-prompt-all-in-one
│   ├── group_tags
│   ├── i18n.json
│   ├── install.py
│   ├── javascript
│   ├── LICENSE
│   ├── models
│   ├── README_CN.MD
│   ├── README_JP.MD
│   ├── README_KR.MD
│   ├── README.MD
│   ├── README_RU.MD
│   ├── README_TW.MD
│   ├── scripts
│   ├── src
│   ├── storage
│   ├── style.css
│   ├── styles
│   ├── tags
│   ├── tests
│   ├── translate_apis.backup.json
│   └── translate_apis.json
└── sd-webui-segment-anything
    ├── install.py
    ├── javascript
    ├── local_groundingdino
    ├── models
    ├── README.md
    ├── requirements.txt
    ├── sam_hq
    ├── scripts
    └── style.css

62 directories, 68 files

```



#### models目录结构

```bash

```





### 在 Debian 系统上使用 Easy-RSA 通常涉及以下步骤：

1. **安装 Easy-RSA**：
   可以通过 Debian 的包管理器安装 Easy-RSA。根据搜索结果[^5^]，有三种方法可以安装 Easy-RSA：使用 `apt-get`、`apt` 或 `aptitude`。以下是使用 `apt` 命令的示例：
   
   ```bash
   sudo apt install easy-rsa
   ```

2. **创建 PKI 目录**：
   安装完成后，需要创建一个目录结构来存放 Easy-RSA 的配置文件和生成的证书。这通常在用户的主目录下完成。例如：
   
   ```bash
   mkdir ~/easy-rsa
   ```

3. **初始化 PKI**：
   在新的目录中初始化 PKI 结构：
   
   ```bash
   cd ~/easy-rsa
   ./easyrsa init-pki
   ```

4. **配置 Easy-RSA**：
   编辑 `vars` 文件来配置 Easy-RSA。这个文件包含了一些默认值，你需要根据你的组织信息进行修改：
   
   ```bash
   nano vars
   ```

5. **生成 CA**：
   创建一个根证书颁发机构（CA）：
   
   ```bash
   ./easyrsa build-ca nopass
   ```
   
   这个命令会生成一个 CA 证书和一个私钥。`nopass` 选项意味着不会为私钥设置密码。

6. **生成服务器和客户端证书**：
   生成服务器和客户端的密钥对以及证书签名请求（CSR）：
   
   ```bash
   ./easyrsa gen-req server nopass
   ./easyrsa gen-req client1 nopass
   ```
   
   这将为服务器和客户端创建私钥和 CSR 文件。

7. **签名请求**：
   使用 CA 来签署服务器和客户端的 CSR：
   
   ```bash
   ./easyrsa sign-req server server
   ./easyrsa sign-req client client1
   ```
   
   这会生成服务器和客户端的证书。

8. **生成 Diffie-Hellman 参数**：
   为了设置密钥交换，你需要生成 Diffie-Hellman 参数：
   
   ```bash
   ./easyrsa gen-dh
   ```

9. **生成 TA 密钥**：
   生成一个 TA（信任锚点）密钥，用于 HMAC 认证：
   
   ```bash
   sudo openvpn --genkey secret ta.key
   ```

10. **复制文件**：
    将生成的证书、密钥和 TA 密钥复制到 OpenVPN 服务器的配置目录中：
    
    ```bash
    sudo cp pki/ca.crt /etc/openvpn/
    sudo cp pki/issued/server.crt /etc/openvpn/
    sudo cp pki/private/server.key /etc/openvpn/
    sudo cp ta.key /etc/openvpn/
    ```

请注意，这些步骤可能需要根据你的具体需求进行调整。例如，如果你正在为 OpenVPN 设置 Easy-RSA，你可能还需要配置 OpenVPN 服务器和客户端的配置文件。此外，确保在生成证书时遵循最佳安全实践，例如，不要在生产环境中使用自签名的 CA。[^1^][^2^][^4^]
