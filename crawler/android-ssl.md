# 安卓高版本HTTPS抓包：终极解决方案

> 之前发的这篇文章，引用了其他公众号的部分内容，没和作者提前打招呼被举报了，现已沟通好。重新发布下

虽然市面上有好多抓包工具，但是 Android 高版本都需要安装抓包工具的证书到系统目录，才能抓 https 协议的包。本文就以 `Charles`这个抓包工具来介绍，如何安装证书到 Android 的系统目录，实现 https 抓包。

### 修改证书名称

启动 Charles，通过菜单栏中的 `Help → SSL Proxying → Save Charles Root Certificate…` 将 Charles 的证书导出。使用 OpenSSL 查看证书在 Android 系统中对应的文件名，并重命名证书文件

```
openssl x509 -subject_hash_old -in charles-ssl-proxying-certificate.pem | head -n 1  #cdfb61bc
```

### 将证书安装到系统证书目录下

使用 adb push 命令将我们的证书文件放到 SD 卡中

```
adb push cdfb61bc.0 /sdcard/Download
```

使用 adb 连接手机并切换到 root 用户

```
adb shell
```

将证书文件移动到 `/system/etc/security/cacerts` 目录下，由于 `/system` 默认是只读的，所以要先重新挂载为其添加写入权限

```
cat /proc/mounts  #查看挂载信息，这里我的 /system 是直接挂载到 / 的
```

如果👆的步骤你都能成功，就不用继续往下看了。

### 终极解决方案

我用我手上的手机都试了一下，用上面的方式安装正式，发现不能成功，一直提示 `Read-only file system`，但是`HttpToolkit`这个软件却可以通过 `Android Device Via ADB`来抓 https 的包。它是怎么实现的呢？这下又开始了漫长的谷歌之旅，最后在他们官网找到一篇文章，详细讲述了 **通过有root权限的adb** 来写入系统证书的神奇方案。

1. 通过 ADB 将 HTTP Toolkit CA 证书推送到设备上。

2. 从 /system/etc/security/cacerts/ 中复制所有系统证书到临时目录。

3. 在 /system/etc/security/cacerts/ 上面挂载一个 tmpfs 内存文件系统。这实际上将一个可写的全新空文件系统放在了 /system 的一小部分上面。将复制的系统证书移回到该挂载点。

4. 将 HTTP Toolkit CA 证书也移动到该挂载点。

5. 更新临时挂载点中所有文件的权限为 644，并将系统文件的 SELinux 标签设置为 system_file，以使其看起来像是合法的 Android 系统文件。

关键点就是挂载一个 **内存文件系统**，太有才了。具体命令如下

```
# 创建一个独立的临时目录，用于存储当前的证书
```

**注意：由于是内存文件系统，所以重启手机后就失效了。可以将以上命令写成 shell 脚本，需要抓包的时候执行下就可以了。**


