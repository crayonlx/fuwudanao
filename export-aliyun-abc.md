# 导出云雀文档为阿里云 ABC 平台支持的格式

云雀可以支持将一个仓库的文档导出为[阿里云 ABC 平台](http://abc.aliyun-inc.com)支持的格式本地文件了哦！

## 功能特点

- 完整支持从云雀的一个仓库的文档导出成为一个 [阿里云 ABC 平台](http://abc.aliyun-inc.com) 格式的文件夹；

> NOTE: 目前只支持 macOS 系统。
> Linux 用户，请直接找 @自成(zicheng.lhs)
> Windows 用户: [lark2abc-windows-64bit.zip](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/zip/3/ed61542baa6ecdb0.zip) 

## 安装

我们开发了一个叫 **lark2abc** 的小工具，可以方便你导出云雀的文档数据。

确保你的 macOS 已经安装了 [Homebrew](https://brew.sh/)，然后使用 [Homebrew](https://brew.sh/) 安装 lark2abc

打开 “终端”，并执行：

```bash
$ brew update
$ brew tap homebrew/skylark http://gitlab.alibaba-inc.com/homebrew/skylark.git
$ brew install lark2abc

Updating Homebrew...
==> Installing lark2abc from homebrew/skylark
==> Downloading http://git.cn-hangzhou.oss-cdn.aliyun-inc.com/uploads/homebrew/skylark/5aff340325d72bd82ec1f038f200eac9/lark2abc-darwin-amd64.zip
######################################################################## 100.0%
🍺  /usr/local/Cellar/lark2abc/0.1.5: 3 files, 5.4MB, built in 4 seconds
```

于是你就有了 **lark2abc** 工具了。

## 使用方法

在使用前，请适当看一下 lark2abc 的帮助信息，打开 “终端” (Windows 叫 CMD)，并执行：

```bash
$ lark2abc -h
NAME:
   lark2abc - 云雀数据导出到 ABC 平台 (abc.aliyun-inc.com)

USAGE:
   lark2abc [global options] command [command options] [arguments...]

VERSION:
   0.1.5

COMMANDS:
     help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --token value, -t value   你的云雀 Token
   --source value, -s value  仓库路径 (group/repo)，例如云雀帮助那个仓库就是: lark/help
   --output value, -o value  导出文件路径 (default: "./output")
   --public                  开启此项，将会把图片转存到公共的 OSS 空间，便于外部网络访问
   --help, -h                show help
   --version, -v             print the version
```

从你的[云雀个人设置页面](https://lark.alipay.com/settings/privateToken)找到 `TOKEN` 信息。



### 导出

```bash
$ lark2abc -t "kskskks" -s lark/help
```

然后就会开始导入了，最后文件会导出到当前目录的 `./output` 里面。

## 升级

我们可能会持续优化这个工具，你只需要执行 `brew upgrade` 就可以升级到最新版本。

```bash
$ brew upgrade lark2abc
```

## 更新历史

### 0.1.5

- 修正 404 的文档未处理导致的异常;

### 0.1.4

- 修正对非图片附件的转存支持。

### 0.1.3

- 用 `仓库slug$$仓库名称` 做为顶层目录。

### 0.1.2

- 修正某些情况下目录层次问题；
- 忽略 body 为空的文件，不生成；
- 导出的 .md 文件改为 `$$1.md` 的后缀；

### 0.1.1

- 修正对仓库目录带有外部仓库链接的文档导出支持。

### 0.1.0

- 新增 `--public` 参数，让使用者决定是否将文档内的图片转存到外网 OSS 空间。

### 0.0.1

- First release.

  