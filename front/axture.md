### libfaketime

这是一个开源的程序库，其 GitHub 地址：`https://github.com/wolfcw/libfaketime`

这个库在 Linux 和 MAC 上都可以用，通常用来测试 Linux 上开发的软件。虽然 MAC 上可能会惯常用 UI 应用程序（就像 Axure 一样），其实也是可以找到对应的可执行程序来使用的。

话不多说，先安装起来。

打开终端，在本地创建一个目录后，`git clone https://github.com/wolfcw/libfaketime.git` 下载源码，然后进入目录执行 `sudo make install` 输入本机登录密码即可安装成功。

安装成功后，可通过 `faketime` 命令测试软件是否能达到效果。例如在 `date` 命令前置 `faketime` 以输出时间：

```shell
faketime -f '2022-04-01 00:00:00' date                            
2022年 4月 1日 星期五 00时00分00秒 CST
```

然后同样的道理可以用到应用程序上，将上面的 `date` 命令替换为 App 的全路径可执行程序即可。例如可以试试将 Axure RP 10 的可执行路径 `/Applications/Axure\ RP\ 10.app/Contents/MacOS/Axure\ RP\ 10` 放到 `faketime` 后执行：

```shell
faketime -f '@2022-04-01 00:00:00' /Applications/Axure\ RP\ 10.app/Contents/MacOS/Axure\ RP\ 10 
Environment version 6.0.0
Framework description .NET 6.0.0-rtm.21522.10
```



可以看到已正常启动软件，并且右上角也是提示还有 11 天过期：



我们进入到应用程序列表，双指点击 `Axure RP 10` 后单指点击“显示包内容”：打开后会看到当前目录下有一个名为 `info.plist` 的文件：然后编辑这个文件，在 `<dict>` 内加入如下代码后保存：

```xml
<key>LSEnvironment</key>
    <dict>
        <key>DYLD_FORCE_FLAT_NAMESPACE</key>
        <string>1</string>
        <key>DYLD_INSERT_LIBRARIES</key>
        <string>/usr/local/lib/faketime/libfaketime.1.dylib</string>
        <key>FAKETIME</key>
        <string>@2022-04-01 00:00:00</string>
   <key>FAKETIME_STOP_AFTER_SECONDS</key>
   <string>10</string>
</dict>
```

编辑完后重启电脑，或者打开终端执行命令： 

```shell
/System/Library/Frameworks/CoreServices.framework/Frameworks/LaunchServices.framework/Support/lsregister -v -f /Applications/Axure\ RP\ 10.app
```



设置完成后，打开启动台点击 Axure RP 10 的图标即可正常使用咯。

不过，此方法可能会在软件更新或升级后因重置了 `info.plist` 而失效，需要再次做上述操作后才可使用。


