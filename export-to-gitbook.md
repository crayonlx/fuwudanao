# 导出云雀文档为 GitBook 格式的本地文件

云雀可以支持将一个仓库的文档导出为 GitBook 的格式本地文件了哦！

> NOTE: 想反过来，将 GitBook 导入到云雀，请阅读：[从 GitBook 仓库 / GitLab Wiki 导入到云雀](import-from-gitbook)

## 功能特点

- 完整支持从云雀的一个仓库的文档导出成为一个 GitBook 的文件夹；

## 安装

### macOS

我们开发了一个叫 **lark2gitbook** 的小工具，可以方便你导出云雀的文档数据。

确保你的 macOS 已经安装了 [Homebrew](https://brew.sh/)，然后使用 [Homebrew](https://brew.sh/) 安装 lark2gitbook

```bash
$ brew update
$ brew tap homebrew/skylark http://gitlab.alibaba-inc.com/homebrew/skylark.git
$ brew install lark2gitbook

Updating Homebrew...
==> Installing lark2gitbook from homebrew/skylark
==> Downloading http://git.cn-hangzhou.oss-cdn.aliyun-inc.com/uploads/homebrew/homebrew-skylark/3d82872bed8e52041a23348c9be04c7d/lark2gitboo
######################################################################## 100.0%
🍺  /usr/local/Cellar/lark2gitbook/0.1.0: 3 files, 5.4MB, built in 4 seconds
```

于是你就有了 **lark2gitbook** 工具了。

### Windows

[lark2gitbook-windows-amd64.zip](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/zip/8b844b11-8c96-4809-bcad-7f52a3794630.zip) 

下载并解压获得 `lark2gitbook.exe`，请启动 CMD 来执行，这个程序是一个命令行工具。

```bash
C:/> lark2gitbook.exe -h
```

### Linux

[lark2gitbook-linux-amd64.tar.gz](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/gz/eee81784-52b7-4e6b-8b20-ef9f0d8932fd.gz) 

```bash
$ curl -ssL https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/gz/eee81784-52b7-4e6b-8b20-ef9f0d8932fd.gz
$ tar zxf eee81784-52b7-4e6b-8b20-ef9f0d8932fd.gz
$ sudo mv lark2gitbook /usr/local/bin/
```



## 使用方法

在使用前，请适当看一下 lark2gitbook 的帮助信息：

> Windows 用户请启动 CMD，`lark2gitbook.exe` 是一个命令行程序，下面的地方请注意替换到对应的路径。

```bash
$ lark2gitbook -h
NAME:
   lark2gitbook - 云雀数据导出到 GitBook

USAGE:
   lark2gitbook [global options] command [command options] [arguments...]

VERSION:
   0.0.1

COMMANDS:
     help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --token value, -t value   PrivateToken of your Lark account.
   --source value, -s value  Source of namespace of Lark for example: lark/help
   --output value, -o value  Path of markdown files to save, default: ./output
   --help, -h                show help
   --version, -v             print the version
```

1. 从你的[云雀个人设置页面](https://lark.alipay.com/settings/privateToken)找到 `TOKEN` 信息。
2. 你也可以设置 `LARK_TOKEN=xxxx` 的环境变量，避免每次都输入 `--token` 参数；



### 导出

```bash
$ lark2gitbook -t "kskskks" -s lark/help
```

然后就会开始导入了，最后文件会导出到当前目录的 `./output` 里面。

## 升级

我们可能会持续优化这个工具，你只需要执行 `brew upgrade` 就可以升级到最新版本。

```bash
$ brew update && brew upgrade lark2gitbook
```

## 更新历史

### 0.1.0

- 修正导出的 .md 文档缺少文档标题的问题；
- 支持 `LARK_TOKEN` 环境变量作为 token;

### 0.0.1

- First release.

 