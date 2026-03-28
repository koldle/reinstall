<!-- markdownlint-disable MD033 -->

# reinstall

本仓库基于 bin456789/reinstall 做了 NixOS Big EFI 特化，当前主要维护以下变动：

- NixOS 安装路径的 EFI 分区默认大小改为 `512MB`
- 支持在运行时通过环境变量 `NIXOS_EFI_SIZE_MB` 覆盖 NixOS EFI 分区大小
- 脚本下载地址与文档链接已切换到本 fork，国内 GitHub 下载改用 `https://ghfast.top` 加速
- 文档仅保留功能 1「安装 Linux」的使用说明

仓库地址：<https://github.com/koldle/reinstall>

## 功能 1：安装 Linux

当前文档只说明功能 1，也就是将机器重装为 Linux 发行版。

基本命令：

```bash
bash reinstall.sh <发行版> <版本> [选项]
```

Windows 下请先运行 `cmd`，再执行：

```batch
reinstall.bat <发行版> <版本> [选项]
```

常用选项：

- `--password PASSWORD`
- `--ssh-key KEY`
- `--ssh-port PORT`
- `--web-port PORT`
- `--frpc-config PATH`
- `--force-boot-mode bios|efi`

支持的 Linux 安装目标：

```text
anolis      7|8|23
opencloudos 8|9|23
rocky       8|9|10
oracle      8|9|10
almalinux   8|9|10
centos      9|10
fnos        1
nixos       25.11
fedora      42|43
debian      9|10|11|12|13
alpine      3.20|3.21|3.22|3.23
opensuse    15.6|16.0|tumbleweed
openeuler   20.03|22.03|24.03|25.09
ubuntu      16.04|18.04|20.04|22.04|24.04|25.10 [--minimal]
kali
arch
gentoo
aosc
redhat      --img="http://access.cdn.redhat.com/xxx.qcow2"
```

## 下载

Linux 当前系统，国外网络：

```bash
curl -O https://raw.githubusercontent.com/koldle/reinstall/main/reinstall.sh || wget -O ${_##*/} $_
```

Linux 当前系统，国内网络：

```bash
curl -O https://ghfast.top/https://raw.githubusercontent.com/koldle/reinstall/main/reinstall.sh || wget -O ${_##*/} $_
```

Windows 当前系统，国外网络：

```batch
certutil -urlcache -f -split https://raw.githubusercontent.com/koldle/reinstall/main/reinstall.bat
```

Windows 当前系统，国内网络：

```batch
certutil -urlcache -f -split https://ghfast.top/https://raw.githubusercontent.com/koldle/reinstall/main/reinstall.bat
```

## NixOS 说明

本 fork 对 NixOS 做了 EFI 分区特化：

- 默认 EFI 分区大小为 `512MB`
- 如需覆盖，运行脚本时设置环境变量 `NIXOS_EFI_SIZE_MB`

示例：

```bash
bash reinstall.sh nixos 25.11
```

```bash
NIXOS_EFI_SIZE_MB=1024 bash reinstall.sh nixos 25.11
```

## 反馈

- 仓库：<https://github.com/koldle/reinstall>
- Issues：<https://github.com/koldle/reinstall/issues>
