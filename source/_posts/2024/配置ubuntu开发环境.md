---
title: 配置ubuntu开发环境
date: 2024-03-28 08:00:00
tags: 
   - ubuntu
   - ssh
   - git
   - zsh 
   - nvm
categories: 
   - 开发环境
---

> 系统版本 (cat /proc/version)
> Linux version 5.15.0-94-generic (buildd@lcy02-amd64-096) (gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #104-Ubuntu SMP Tue Jan 9 15:25:40 UTC 2024


## 操作步骤

1. ### 配置远程免密码登录

   ```bash
   ssh-copy-id user@ip
   ```

2. ### 配置服务器ssh config
   用户github代码上传

   ```bash
   cd ~/.ssh
   ssh-keygen -t rsa -b 4096 -f github.com -C "email"
   vim config
   ```

   config 添加如下内容
   ```yaml 
   Host github.com
   Hostname github.com
   User git
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/github.com
   ```

3. ### github配置ssh公钥
   https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

4. ### 配置git config

   ```bash
   git config --global user.name "yuyidm"
   git config --global user.email "wx012357@gmail.com"
   git config --global core.editor "vim"
   ```

5. ### 配置服务器代理
   参考  *https://github.com/TyrantLucifer/ssr-command-client*

6. ### 安装zsh & ohmyzsh

   ```bash
   apt-get update
   apt-get install zsh -y
   chsh -s `which zsh`
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

   ```bash
   # 设置.zshrc

   # 查询出网地址
   alias ip="curl cip.cc"
   ```

7. ### 配置node环境 nvm

    *https://github.com/nvm-sh/nvm?tab=readme-ov-file#install--update-script*

    安装成功后

    ```bash
    nvm install --lts
    npm i -g nrm 
    nrm use taobao
    npm i -g pnpm pm2
    ```
