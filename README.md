# OpenCloudOS 安装

## 前言

* 本文档介绍在物理机上安装和配置 OpenCloudOS 系统的步骤，以及一些常用的系统维护命令。
  <br/>
* 首先通过[官网](https://www.opencloudos.org/)下载 OpenCloudOS 的 ISO 镜像文件，制作[启动U盘](https://rufus.ie/zh)，然后按照提示完成系统安装。
  <br/>
* 如果在国内，官网的下面是有镜像下载地址的链接。完整的ISO镜像大约有10GB，建议使用[IDM](https://www.internetdownloadmanager.com/)进行下载。

## 安装 SSH 服务
1. 安装 OpenSSH 组件。
  ```
  sudo dnf install -y openssh openssh-server
  ```
2. 启动服务并设为开机自启。
  ```
  sudo systemctl enable sshd
  sudo systemctl start sshd
  ```

## 配置防火墙
放行 SSH 服务端口，确保远程访问可用。
```
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

## 系统更新
```
sudo dnf check-update && sudo dnf upgrade -y && sudo dnf clean all
```

## 终端显示
关闭终端屏幕显示：
```
setterm --blank force
```
