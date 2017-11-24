# 从 GitBook 仓库 / GitLab Wiki 导入到云雀

云雀可以支持从 GitBook 仓库 / GitLab Wiki 直接导入数据了哦！

> 👹 NOTE: 想反过来，将云雀的数据导出到 GitBook，请阅读：[导出云雀文档为 GitBook 格式的本地文件](export-to-gitbook)

## 功能特点

- 完整支持从 GitBook 迁移到云雀，支持 `SUMMARY.md` 变为云雀的自定义目录；
- 支持从 GitLab Wiki 导入到云雀（需要自行编辑目录），请确定 GitLab Wiki 上的内容是 Markdown 编写，并且能在 GitLab Wiki 上正确浏览；
- 理论上支持任意类型的 Git 仓库（里面含有 `*.md`, `*.markdown` 文件的）导入到云雀；
- 只支持 Markdown 的文档迁移，其他格式暂时不行。

> NOTE: 目前只支持 macOS 系统。
> Linux 用户，请直接找 @自成(zicheng.lhs)
> Windows 暂时无法支持

**几个已经导入好的例子**

- https://lark.alipay.com/crystal/docs
- https://lark.alipay.com/rust/rust-book-chinese

## 安装导入工具

我们开发了一个叫 **gitbook2lark** 的小工具，可以方便你导入数据到云雀。

确保你的 macOS 已经安装了 [Homebrew](https://brew.sh/)，然后使用 [Homebrew](https://brew.sh/) 安装 gitbook2lark

```bash
$ brew update
$ brew tap homebrew/skylark http://gitlab.alibaba-inc.com/homebrew/skylark.git
$ brew install gitbook2lark

Updating Homebrew...
==> Installing gitbook2lark from homebrew/skylark
==> Downloading http://024028.oss-cn-hangzhou-zmf.aliyuncs.com/uploads/lark/homebrew-tap/3266bcda771819dcf465d91cfde54f2e/gitbook2lark.zip
######################################################################## 100.0%
🍺  /usr/local/Cellar/gitbook2lark/0.1.0: 3 files, 726.3KB, built in 1 second
```

于是你就有了 **gitbook2lark** 工具了。

## 使用方法

在使用前，请适当看一下 gitbook2lark 的帮助信息：

```bash
$ gitbook2lark -h
Usage:
gitbook2lark
    -h, --help                       Show this help
    -v                               Show version
    -t TOKEN, --token TOKEN          你的云雀账号的 TOKEN
    -s SOURCE, --source SOURCE       GitBook 源的 Git URL, 例如: https://github.com/foo/bar.git
    -o NAMESAPCE, --output NAMESAPCE 要导入的仓库的 namespace (group_name/repo_name), 例如这个仓库: lark/help
```

1. 从你的[云雀个人设置页面](https://lark.alipay.com/settings/privateToken)找到 `TOKEN` 信息。
2. 在云雀上手工创建好一个空的仓库，用于接收导入的数据。



### 迁移 GitBook

```bash
$ gitbook2lark -t "kskskks" -s https://github.com/KaiserY/rust-book-chinese.git -o lark/rust-book-chinese
```

然后就会开始导入了。

![image.png](http://alipay-rmsdeploy-image.cn-hangzhou.alipay.aliyun-inc.com/skylark/attach/3/2d565f5c8990d8a9/image.png) 

### 迁移 GitLab Wiki

自从 0.2.0 版本开始，这个工具也可以支持将 GitLab Wiki 了哦！

以这个仓库为例：

- http://gitlab.alipay-inc.com/lark/crystal-book/wikis/git_access

打开上面的链接，你可以看到:

![屏幕快照 2017-03-28 下午4.02.55.png](https://os.alipayobjects.com/skylark/212f34e3-c820-445f-bbdc-12d7dcca97e2/attach/3/8fb599aec442ff35e0afb6488c665b39) 

然后我们可以:

```bash
$ gitbook2lark -t "kskskks" -s git@gitlab.alipay-inc.com:lark/crystal-book.wiki.git -o crystal/crystal-book
```

> 注意！由于 GitLab 有权限验证，这个命令执行以后你可能需要输入域账号密码（http 协议的 Git 地址）

## 升级

我们可能会持续优化这个工具，你只需要执行 `brew upgrade` 就可以升级到最新版本。

```bash
$ brew upgrade gitbook2lark
```

## 更新历史

### 0.2.3

- 修正文件路径 `_` 字符被错误替换为 `-` 的问题。

### 0.2.2

- 修正目录里面文档 slug 包含多余的仓库前缀的问题；
- 不再将目录的缩进替换成 SoftTab，而是保持原有的，例如 Tab；

### 0.2.1

- 修正并发的实现，以达到真正并发创建文档，并发数量 50，效率大幅提升.

### 0.2.0

- 不再要求必须有 SUMMARY.md，以便于支持 GitLab 的 Wiki 导入；
- 当 title 无法解析出来的时候，用文件名作为 title；
- 增加 `.markdown` 扩展名的支持；

### 0.1.2

- 优化标题处理，正文里面去掉 Heading 1。

### 0.1.1

- 用并发的方式上传文档，提高导入效率。
- 执行结果日志输出优化。

### 0.1.0

- First release.

