# docker安装

## Ubantu安装

1. **安装必要依赖**：

```bash
sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```

2. **添加Docker的GPG密钥**：
   
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

3. **添加Docker的官方存储库**：
   
   Bash
   
   ```bash
   1sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```

4. **再次更新包列表**：
   
   Bash
   
   ```bash
   sudo apt update
   ```

5. **安装Docker CE（社区版）**：
   
   Bash
   
   ```bash
   sudo apt install docker-ce docker-ce-cli containerd.io
   ```

6. **启动Docker服务并设置开机启动**：
   
   Bash
   
   ```bash
   1sudo systemctl start docker
   2sudo systemctl enable docker
   ```

### 配置国内镜像加速（例如阿里云）

为了提高Docker镜像拉取速度，可以配置Docker加速器地址：

Bash

```bash
1sudo mkdir -p /etc/docker
2echo '{"registry-mirrors": ["https://<your-accelerator-url>"]}' | sudo tee /etc/docker/daemon.json
3sudo systemctl daemon-reload
4sudo systemctl restart docker
```
