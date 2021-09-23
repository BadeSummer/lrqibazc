# brew 安装
`brew` 是Mac上实现与Linux中的`apt-get`类似功能的一个命令，但是这个命令是需要额外安装的。
```[shell]
ruby -e"$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
若正常则会需要输入密码，然后等待安装完成即可。
结束后可以使用```brew --version```查看版本信息，验证是否安装成功。

噢记得换镜像源