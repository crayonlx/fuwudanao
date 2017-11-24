# HTML 代码

云雀允许一部分 HTML 代码直接插入文档。

## style 属性

如果你有设置样式的需求，可以采用`style`属性。下面是文本置中的例子。

<div style="text-align: center;">这行文本置中。</div>

```html
<div style="text-align: center;">这行文本置中。</div>
```

## 允许的标签

目前，云雀允许的 HTML 标签有以下这些。

>  "a", "article", "audio", "b", "blockquote", "br", "caption", "code", "del", "details", "div", "em", "embed", "h1", "h2", "h3", "h4", "h5", "h6", "hr", "i", "iframe", "img", "input", "ins", "kbd", "li", "link",  "main", "object", "ol", "p", "pre", "section", "source", "span", "strike", "strong", "sub", "summary",  "sup", "table", "tbody", "td", "th", "thead", "tr", "u", "ul", "video",

注意，`iframe`、`embed`标签开启了白名单过滤，而`object`标签只允许用来插入 SVG 图片。

## iframe

iframe 标签只能用来插入 Riddle 代码演示和一些视频网站。

<iframe src="https://riddle.alibaba-inc.com/riddles/a070fb14/iframe" height="360" frameborder="no" allowtransparency="true" allowfullscreen="true" style="width: 100%; border: 1px solid #e9e9e9;"></iframe>

```html
<iframe src="https://riddle.alibaba-inc.com/riddles/a070fb14/iframe" height="360" frameborder="no" allowtransparency="true" allowfullscreen="true" style="width: 100%; border: 1px solid #e9e9e9;"></iframe>
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/_dMgh4Hh1cY" frameborder="0" allowfullscreen></iframe>

```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/_dMgh4Hh1cY" frameborder="0" allowfullscreen></iframe>
```

<iframe frameborder="0" width="640" height="498" src="https://v.qq.com/iframe/player.html?vid=g0022pmqwol&tiny=0&auto=0" allowfullscreen></iframe>

```html
<iframe frameborder="0" width="640" height="498" src="https://v.qq.com/iframe/player.html?vid=g0022pmqwol&tiny=0&auto=0" allowfullscreen></iframe>
```