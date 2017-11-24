# Markdown 语法：流程图

云雀通过 [flowchart.js](http://flowchart.js.org/) 支持流程图。 

```flow
开始=>start: 操作开始
结束=>end: 操作结束
操作1=>operation: 读取文件
操作2=>operation: 处理文件
条件=>condition: 是否报错？

开始->操作1->操作2->条件
条件(yes)->结束
条件(no)->操作2
```

<pre>
```flow
开始=>start: 操作开始
结束=>end: 操作结束
操作1=>operation: 读取文件
操作2=>operation: 处理文件
条件=>condition: 是否报错？

开始->操作1->操作2->条件
条件(yes)->结束
条件(no)->操作2
```
</pre>

```flow
开始=>start: Start:>https://www.alipay.com[blank]
结束=>end:>https://www.alipay.com
操作1=>operation: 打开网站
子区块1=>subroutine: 网站打开失败的子流程
条件=>condition: 能否打开?:>https://www.alipay.com
io=>inputoutput: 输出内容……

开始->操作1->条件
条件(yes)->io->结束
条件(no)->子区块1(right)->操作1
```

<pre>
```flow
开始=>start: Start:>https://www.alipay.com[blank]
结束=>end:>https://www.alipay.com
操作1=>operation: 打开网站
子区块1=>subroutine: 网站打开失败的子流程
条件=>condition: 能否打开?:>https://www.alipay.com
io=>inputoutput: 输出内容……

开始->操作1->条件
条件(yes)->io->结束
条件(no)->子区块1(right)->操作1
```
</pre>
