# Git

## 简易的命令行入门教程:

## Git 全局设置:

    git config --global user.name "xxx"
    git config --global user.email "xxx@163.com"

## 创建 git 仓库:

    mkdir test
    cd test
    git init
    touch README.md
    git add README.md
    git commit -m "first commit"
    git remote add origin https://gitee.com/xxx/test.git
    git push -u origin master

## 已有项目?

    cd existing_git_repo
    git remote add origin https://gitee.com/xxx/test.git
    git push -u origin master

## 记住密码

    git config --global --list

    git config --global credential.helper store
