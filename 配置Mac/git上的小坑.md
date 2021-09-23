# 使用Git上的一些小坑   （Mac）
## key
换电脑/重装系统之后，就算恢复了备份，ssh的公钥和密钥都在，也最好把它都删除，重新配置。不然会少了一个文件。导致
```shell
The authenticity of host '[ssh.github.com]:443 ([192.30.253.122]:443)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? 
```

## host
`Failed to connect to github.com port 443: Connection refused`如果出现这个报错。我遇到的直接处理就是找到`/private/etc/host`，对应其他系统应该就是host文件。打开后把所有跟github有关的配置都注释掉。就可以解决问题。  
详情排错可以参考[【已解决】git clone出错：Failed to connect to github.com port 443 Operation timed out](https://www.crifan.com/git_clone_failed_to_connect_to_github_com_port_443_operation_timed_out/)