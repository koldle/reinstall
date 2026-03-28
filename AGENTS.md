# bin456789/reinstall 的 nixos big efi 特化 fork

当前仓库原始上游是 https://github.com/bin456789/reinstall

## 需求

1. 针对原库的功能 1 的「安装 NixOS」这条路径，调整默认的 efi 分区大小为 512MB，并可以在运行脚本的时候通过环境变量动态设置

如果有其他发行版和 nixos 共用了代码，可以一并影响，在保证功能的前提下尽可能精简变动

2. 把脚本中指向原本上游的地方全部修正，如需国内网络下载 github 请改成使用 https://ghfast.top 加速

3. 针对两份 README，移除英文版，将中文版删减到只有功能 1 的使用说明, 并替换其中指向原库的链接为我的仓库。在 README 开头添加 fork 声明介绍本仓库的变动

4. 将所有改动（包含本文档）做成一个单独的 commit，放到一个独立的分支

后续上游更新后，我会用 ai 处理该仓库，应先用上游覆盖 main，再参考独立分支的 commit 回做修改

5. 把做的所有变动记录在下边的 `记录` 章节

## 记录

- 独立分支：`fork-nixos-big-efi`
- 已将 `main` 同步到独立分支对应的改动并推送到 `origin/main`，日常使用与功能测试应基于 `main`，独立分支继续保留为后续参考分支。
- 调整 NixOS 安装路径的 EFI 分区默认大小为 `512MB`，并新增运行时环境变量 `NIXOS_EFI_SIZE_MB`，该值会通过内核命令行传递到 `trans.sh`，确保重启进入安装环境后仍然生效。
- 保持 Alpine / Arch / Gentoo / AOSC 共用分区逻辑不变，仅在 NixOS 的 EFI 安装分支上改用新的默认值。
- 将 `reinstall.sh`、`reinstall.bat` 中的脚本源地址和手册地址切换到 fork 仓库 `koldle/reinstall`，国内 GitHub 下载改为通过 `https://ghfast.top` 加速。
- 清理脚本中指向原上游仓库的注释链接，避免继续指向原仓库。
- 删除英文 README，重写中文 README，仅保留功能 1「安装 Linux」说明，并补充本 fork 的变更说明、fork 仓库地址与 NixOS EFI 环境变量示例。
