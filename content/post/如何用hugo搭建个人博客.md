---
title: "如何用hugo搭建个人博客"
date: 2020-01-19T21:49:12+08:00
draft: false
---

# 前端学习

## 如何用 hugo 搭建个人博客

### 一、安装 Hugo

1. Mac 安装方式

```
brew install hugo
 hugo version
```

2. Windows 安装方式

- 去[Hugo releases 页面](https://github.com/gohugoio/hugo/releases)下载 hugo_xxxx_Windows-64bit.zip
- 解压，把 hugo.exe 放到 D:\Software\hugo\hugo.exe
- 把 D:\Software\hugo\加到 PATH
- 重启终端，运行 hugo version 查看版本

### 二、搭建博客

进入[Hugo 官网](https://gohugo.io/)，点击 Quick Start 快速开始。从 Step2 开始抄代码，直到 Step7，得到一个 public 目录，这就是我们的博客站点。此文在 Quick Start 的基础上做了一些修改。

具体步骤及详细代码如下：

1. 创建站点

在名为 cu2xin.github.io-creator 的文件夹中创建一个新的 Hugo 站点。

```
hugo new site cu2xin.github.io-creator
```

2. 设置主题

找一个喜欢的主题，本文使用的[jane 主题](https://github.com/xianmin/hugo-theme-jane)。

运行如下代码

```
cd cu2xin.github.io-creator所在路径
 git init
 git clone https://github.com/xianmin/hugo-theme-jane.git --depth=1 themes/jane
 cp themes/jane/exampleSite/config.toml ./
```

3. 自定义主题

ctrl+P 打开 config.toml。

- 将 title 替换为个人内容，例如：某某的博客。

```
title = "Jane - A super concise theme for Hugo"
```

- 设置默认语言，将“en”替换为“zh-cn”，一共有三处替换。

```
defaultContentLanguage = "en"           # Default language to use
 [languages.en]
 languageCode = "en"
```

- 设置作者，将 name 替换为个人名字。

```
[author]                  # essential                     # 必需
 name = "xianmin"
```

4. 添加内容

```
hugo new post/博客名称.md
```

- 可按需要修改 title、date 和 draft，注意：1、date 只能选择当前或以前的时间，选择将来的时间博客不会显示；2、“draft：ture”表示草稿不会被部署，“draft：false”表示非草稿会被部署，通常博客内容录入完成后改为“draft：false”。
- 在下方录入正文内容。

5. 启动 Hugo 服务器

   运行如下代码:

```
hugo server -D  #预览草稿
 hugo server     #预览非草稿
```

6. 建立静态页面

- 新建一个终端
- 运行如下代码：

```
hugo -D            #hugo也可以
```

### 三、博客上传到 GitHub

1. 上传 public

- 在 github 上新建一个仓库 cu2xin.github.io
- 在 cu2xin.github.io-creator 中新建一个文件.gitignore；
- 在.gitignore 中写入/public/；
- 运行如下代码：

```
cd public
 git init
 git add .
 git commit -v
 git remote add origin git@github.com:cu2xin/cu2xin.github.io.git
 git push -u origin master
```

2. 查看博客

- 在 cu2xin.github.io 处点击 Settings；
- 在弹出网页中的 GitHub pages 处找到链接点击查看博客。

### 四、添加第二个博客

运行如下命令添加第二篇博客：

```
cd ..
 hugo new post/博客名称2.md      #编辑博客2内容
 hugo
 cd public
 ga .
 gc
 gp
```

### 五、博客备份

1. 在 github 上新建一个仓库 cu2xin.github.io-creator。
2. 运行如下代码，查看是否有异常文件。

```
git add .
 git status
```

3. 查询异常文件中是否有.git 文件,可将.git 文件删除。

```
ls -a themes/jane/
 rm -rf themes/jane/.git
```

4. 运行如下命令完成备份：

```
git commit -v
 git remote add origin git@github.com:cu2xin/cu2xin.github.io-creator.git
 git push -u origin master
```

5. 注意：如果不小心上传了 https，则运行如下命令改为 ssh。

```
git remote set-url origin git@github.com:cu2xin/cu2xin.github.io-creator.git
 git push -u origin master
```

> 观书有会意处，题其衣裳，以记其事。
