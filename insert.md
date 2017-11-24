# 如何内嵌视频&PDF

### 视频

进入一篇文档的编辑界面，选择工具栏上 ==“视频”== 按钮。在弹出的窗口里选择文件进行上传即可。

![Screen Shot 2017-05-26 at 11.03.28.png | center](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/3/8e2c6e58bd8ac28e.png "")


**注意：云雀只能在线播放 H.264 格式编码的视频。如果你的视频使用 MP4V 格式编码，必须转码为 H.264 格式，才能在云雀上播放。**

### PDF

目前云雀支持两种查看 PDF形式，一种内嵌，一种打开新窗口查看。

#### 如何在文档中加入内嵌PDF？

1.将 PDF 文件先拖入文档编辑器中，等待上传完成。  
2.在 PDF 文件 Markdown 语法中 加入 `embed：`即可将显示模式改成内嵌。

比如这是上传 PDF 文件后云雀显示的 Markdown 语法：

```markdown
[pdf测试文件.pdf](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/pdf/3/be7f620b4a6cf441.pdf)
```

需加入 `embed：`字符到 Markdown 语法中，具体如下：

```markdown
[embed: pdf测试文件.pdf](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/pdf/3/be7f620b4a6cf441.pdf)
```

PDF内嵌模式：

[embed: pdf测试文件.pdf](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/pdf/3/be7f620b4a6cf441.pdf)



PDF 新开窗口模式：

[pdf测试文件.pdf](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/pdf/3/be7f620b4a6cf441.pdf)

