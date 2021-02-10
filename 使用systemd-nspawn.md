# 使用systemd-nspawn


1. 进行chroot切换，指定语言为中文：

```bash
sudo systemd-nspawn -aD live -E "LANG=zh_CN.UTF-8"
```
2. 切换，并指定根目录
```bash
sudo systemd-nspawn -aD live --chdir=/
```
2. 不共享网络（定制工具定制防火墙）
```bash
 sudo systemd-nspawn -aD live -E "LANG=zh_CN.UTF-8" --private-network
```
3. 关闭工具本身的输出
```bash
sudo systemd-nspawn -q -D live -E "LANG=zh_CN.UTE-8" -a /bin/bash
```

4. 执行脚本，该脚本必须在切换的目录中
```bash
sudo systemd-nspawn -q -D live -E "LANG=zh_CN.UTF-8" -a /home/test.sh
```