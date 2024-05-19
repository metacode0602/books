# Nginx相关配置

### 配置端口转发

```ini
server {
    listen 6006;

    # 如果你想要将此端口用于某个具体的服务，比如TensorBoard，可以添加如下location配置
    location / {
        proxy_pass http://localhost:11434; # 假设TensorBoard在本地的6006端口运行
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    # 其他可能需要的配置，比如访问日志、错误日志等
    access_log /var/log/nginx/6006_access.log;
    error_log /var/log/nginx/6006_error.log;
}
```
