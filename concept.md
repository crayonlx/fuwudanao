# 云雀概念

# 基本概念
下图展示了云雀中各种概念的基本关系：

![ea2f62bbdcfa858d.png](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/3/ea2f62bbdcfa858d.png) 

## 用户
云雀采用集团 BUC 用户体系，所有集团 BUC 用户都可以访问云雀。
1. 用户可以创建自己的仓库，该仓库属于用户自己。
2. 用户可以创建团队，并将其他用户加入团队使其成为团队成员。
3. 团队成员可以给团队创建仓库，该仓库属于团队。
4. 用户可以在仓库中创建文档，该文档被创建用户拥有，并包含在指定的仓库中。

## 团队
团队是云雀的顶层组织，在云雀的世界里，团队可以是 `一帮人`， `一件事情`， `一个项目`，或者`一个产品`。团队可以帮助管理权限和多人间的协作。
1. 第一个创建团队的用户自动成为团队的 Owner，团队必须至少有一个 Owner，并可以有多个 Owner 。
2. 团队的 Owner 可以将其他用户添加为团队的成员，一个用户可以被加入到多个团队中。
3. 团队的 Owner 可以将其他成员设置为 Owner 或者 Member。
4. 在团队存在多个 Owner 的情况下，一个 Owner 可以将自己降级为 Member 或退出团队。
5. 在自己是唯一 Owner 的情况下，Owner 无法对自己进行任何操作（保证团队至少有一个 Owner ）。

## 仓库
仓库是存放文档的容器。通过仓库，可以将一系列相关的文档组织在一起，方便阅读和管理。
1. 用户直接创建的仓库属于用户自己，用户在团队中创建的仓库属于团队。
2. 仓库分为“文档仓库”和“画板仓库”，文档仓库专门存放文本类文档，画板仓库专门存放设计类文档。
3. 可以将仓库设置为“私密仓库”（加锁），这样只有用户自己或团队成员才能访问该仓库。
4. 用户自己或团队 Owner 可以删除仓库，或者将仓库转移给其他用户或团队。

## 文档仓库
文档仓库用于存放以文字为主的文档。
1. 一个仓库可以存放多个文档，但一个文档只能包含在一个仓库中。
2. 可以通过设置“开启目录功能”为文档仓库创建目录。

## 画板仓库
画板仓库专门用于存放和展示设计资料的仓库，包括各种格式的设计稿和图文资料。
1. 画板仓库包含展示的画板和设计资料的源文件。
2. 通过“上传”操作可以将画板和源文件添加到画板仓库中。

## 文档
文档是以文字为主的知识内容，也是云雀中最重要的概念。
1. 文档只能在文档仓库中由用户创建产生，并通过各种编辑操作形成文档的具体内容。
2. 云雀文档必须包含且只能包含于一个文档仓库中。
3. 用户或团队成员可以给单一文档加锁，这样只有用户自己或团队成员才能访问该文档。

## 画板
画板是可展示的设计资料的通称，用于针对各种产品设计问题的展示、沟通和交流。
1. 画板通过上传设计稿产生，目前可以上传 Sketch、PSD 和多种图片格式。
2. 上传的画板可在线展示，同时保存了源文件以方便随时下载。
3. 访问画板的用户可在线标注与评论画板内容。

