# 如何排版图片

我们在 Markdown 语法的基础上，为云雀中的图片进行了扩展，使他进一步满足我们对图片排版的需求。普通的图片链接地址格式如下：

```markdown
![image](url)
```

而我们扩展后的完整语法如下：

```markdown
![image | ${定位方式} | ${宽}x${高}](url "title")
```

### 浮动方式

设置图片在**文档流**中的浮动方式：`center`、`left`、`right`，它将决定文档的展示方式，如下：

```
![image|center](url)
```

![image](https://zos.alipayobjects.com/basement/skylark/0ad6383d14736693623545602/attach/4/3/image.png "水平居中")

```
![image|left](url)
```

![image](https://zos.alipayobjects.com/basement/skylark/0ad680ae14736694292757910/attach/4/3/image.png "水平居左")

```
![image|right](url)
```

![image](https://zos.alipayobjects.com/basement/skylark/0ad6383d14736694850906884/attach/4/3/image.png "水平居右")

### 尺寸控制

在高清屏下，我们在屏幕截图的图片，可能会以 2x 倍的形式存在剪切板中，这时候上传会变大，需要还原最初的大小。我们提供了尺寸设置：`宽x高` 的方式。

```
![image||300x200](url)
```

如果只写了一个数值，那么图片的高将会以缩放的等比例缩放。

### 图片标题

在链接的最后，以引号的形式写入内容，就可以展示出来了。


