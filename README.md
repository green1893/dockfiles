# 说明
本项目为各类基础镜像制作文件Dockerfile的备份项目，供参考和完善使用。

## JRE
基于Alpine的jre（8u242）环境，镜像大小 **68.89MB** 左右，适用于Spring Boot、Spring Cloud等应用。
- 支持中文字体
- 时区已设置为东八区（Asia/Shanghai）
- Alpine Linux Package仓库配置为阿里云仓库（本地加速）。软件包查询：https://pkgs.alpinelinux.org/packages
- 已安装`tini`、`bash`工具