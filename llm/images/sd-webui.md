



### 配置环境变量

##### 安装Conda


通常，Conda会与Anaconda或Miniconda一起安装。Anaconda是一个面向科学计算的Python发行版，包含了Conda、Python以及一系列预安装的库和工具。Miniconda是一个更轻量级的发行版，只包含Conda和必要的Python。

基本命令

Conda是一个开源的包管理系统和环境管理系统，它主要用于安装和管理软件包以及创建和维护不同的软件环境。以下是Conda的一些常用使用方法：

### 安装Conda

通常，Conda会与Anaconda或Miniconda一起安装。Anaconda是一个面向科学计算的Python发行版，包含了Conda、Python以及一系列预安装的库和工具。Miniconda是一个更轻量级的发行版，只包含Conda和必要的Python。

### 基本命令

- **更新Conda**：
  
  ```bash
  conda update -n base -c defaults conda
  ```

- **创建新的环境**：
  
  ```bash
  conda create --name myenv python=3.8
  ```
  
  这将创建一个名为`myenv`的新环境，并安装Python 3.8。

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



## 执行安装

```shell
conda create --name sdwebui python=3.10

conda activate sdwebui

wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh

sh webui.sh

cd stable-diffusion-webui

python -m venv venv

pip install -r requirements.txt

./webui.sh --listen --port 8888  --share




```




