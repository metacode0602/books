### github无密码推送代码

### 生成SSH key

```shell
ssh-keygen -t ed25519 -C "docsify@163.com"
```

输出

```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/Users/a123123/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/a123123/.ssh/id_ed25519
Your public key has been saved in /Users/a123123/.ssh/id_ed25519.pub
```

### 将你的 SSH 密钥添加到 ssh-agent

- 启动 ssh-agent 到后台

```shell
eval "$(ssh-agent -s)"
###Agent pid 25589
```

- 编辑`~/.ssh/config`

```shell
vim ~/.ssh/config
```

修改内容如下：

```ini
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

- 将你的 SSH 私钥添加到 ssh-agent 并把密码短语存储在钥匙串中。如果你用不同的名字创建了你的密钥，或者你正在添加一个有不同名字的现有密钥，将命令中的 id_ed25519 替换成你的私钥文件的名字。

```shell
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

> --apple-use-keychain` 选项允许你在将 SSH 密钥添加到 ssh-agent 时，自动将密码短语存储在你的钥匙串中。如果你选择不为你的密钥添加密码，那么在运行命令时不要使用 `--apple-use-keychain` 选项。

> `--apple-use-keychain` 选项是 Apple 标准版本的 ssh-add 工具的一部分。在 macOS Monterey (12.0) 之前的版本中，`--apple-use-keychain` 和 `--apple-load-keychain` 标志使用的是 `-K` 和 `-A` 这样的语法。

>  如果你没有安装 Apple 的标准版本的 ssh-add，你可能会收到错误信息。更多信息，请参阅“错误：ssh-add: 非法选项 --apple-use-keychain”。

> 如果你持续被提示输入你的密码短语，你可能需要将该命令添加到你的 `~/.zshrc` 文件中（或者对于 bash shell，添加到 `~/.bashrc` 文件中）。

```shell
pbcopy < ~/.ssh/id_ed25519.pub
```

- **添加 SSH 公钥到 GitHub 账户**：
  
  复制你的 SSH 公钥内容（`id_ed25519.pub` 文件的内容），然后登录到你的 GitHub 账户，访问 `Settings > SSH and GPG keys > New SSH key。在 `New SSH key` 页面，贴上你的公钥内容到`Key`字段，给你的密钥起一个标题，然后点击`Add SSH key`。

- **测试 SSH 连接**：
  
  添加 SSH 密钥后，你可以通过以下命令测试与 GitHub 的 SSH 连接：`ssh -T git@github.com`

如果是第一次连接到 GitHub，系统可能会询问你是否信任 GitHub 主机，输入 `yes` 继续。之后，如果你的 SSH 设置正确，你将看到一条欢迎消息。


