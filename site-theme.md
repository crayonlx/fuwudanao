# 主题开发帮助文档

## 🐯 Hugo

云雀小站的站点是基于 hugo 实现的，Hugo 是一个静态站点生成器，更详细的介绍可见[官网](https://gohugo.io/about/what-is-hugo/)。
==目前小站使用 hugo v0.20 版本，推荐本地安装一样的版本，避免兼容性问题。==

跟着 [教程](https://gohugo.io/getting-started/quick-start/) 安装好 hugo 后，用 hugo 内置的脚手架生成一个简单站点

```markup
hugo new site [yoursitename]
```

可以看到 `yoursitename/` 下会包含以下内容：

```markup
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
```

我们来一一看下这些文件和目录都有什么作用。

### 🐱 config.toml

阅读[官方文档](https://gohugo.io/getting-started/configuration/)，可以了解到 config 文件对于一个 hugo 站点主要有以下作用：

1. 一般在 config 文件里默认包含几个变量  
   1.1. **baseURL：**站点的根目录  
   1.2. **theme: **站点使用的主题  
   1.3. **title: **站点标题
2. 你可以在 config 文件里指定全站范围的参数，参数放在 `[params]` 下，在模板里则通过 `.Site.Params.xxx` 来访问。例如在云雀小站提供的数据包中， `config.toml` 里的 `params` 就有：`slug`（创建云雀小站时填写的 `slug`）；`description`（创建云雀小站时填写的站点描述）。
3. 另外 config 文件里一般还包含站点的菜单，在模板里可以通过 `.Site.Menus` 访问。


### 🦁 content

指路[相关文档](https://gohugo.io/content-management/)。

当我们在小站后台里绑定一个云雀仓库时，就会数据包的 content 目录下生成对应的一个文件夹，以仓库的 slug 命名，如 `authors/`。该文件夹下则包含该云雀仓库下的所有文档，文档为 markdown 格式，以文档的 slug 命名， `john-doe.md`。在 Hugo 站点中，以 `yoursite.com/authors/john-doe` 路径就能访问到对应的已转换成 html 页面的文档内容。而访问 `yoursite.com/authors/` 则会访问到 `authors/` 目录下的 `_index.md`，默认是根据云雀仓库目录中的第一篇文档内容生成的。

```markup
.
└── content
    ├── authors
    |   ├── _index.md     // <- yoursite.com/authors/
    |   ├── john-doe.md   // <- yoursite.com/authors/john-doe/
    |   └── jane-doe.md   // <- yoursite.com/authors/jane-doe/
    └── events
    |   ├── _index.md     // <- yoursite.com/events/
    |   ├── event-1.md    // <- yoursite.com/events/event-1/
    |   ├── event-2.md    // <- yoursite.com/events/event-2/
    |   └── event-3.md    // <- yoursite.com/events/event-3/
    └── posts
    |   ├── _index.md     // <- yoursite.com/posts/
    |   ├── event-1.md    // <- yoursite.com/posts/event-1/
    |   ├── event-2.md    // <- yoursite.com/posts/event-2/
    |   ├── event-3.md    // <- yoursite.com/posts/event-3/
    |   ├── event-4.md    // <- yoursite.com/posts/event-4/
    |   └── event-5.md    // <- yoursite.com/posts/event-5/
```

每一篇文档的 `md` 文件中都包含以下信息：

```json
{
  "title": "导航栏",
  "section": "api", // 所属仓库的 slug，即当前所在文件夹的名称
  "book": "API", // 所属仓库的名称
  "slug": "ui-navigate", // 文档自己的 slug
  "date": "2017-05-10T03:09:49.000Z" // 文档最后更新时间
}
```

在模板里则可以通过 `.title`，`.section`，`.slug` 这样的形式访问到这些变量。具体的使用方法见[模板](#template)。

### 🐶 data

云雀小站在数据包里提供了以下数据供开发使用：

* `main.json`：包含所有文档的目录，在模板中通过`.Data.main`来获取。通常用于生成站点的目录树。其数据格式适用于在==模板==中进行调用。
* `sitemap.json`：包含所有文档的目录，在模板中通过 `.Data.Sitemap` 来获取。通常用于生成站点的目录树。其数据格式适用于在 ==js== 中进行调用。
* `pages.json`：包含所有文档的内容，在模板中通过 `.Data.Pages` 来获取。因为包含了所有文档的内容，所以一般很大，在使用时请小心，避免造成性能问题。


==注：以上内容都是云雀小站在打包时根据您在站点后台的配置为您自动生成好的，您只需理解其含义，并会在模板中进行调用，方便主题开发即可。==

## 🐼 themes

如何自己开发一个 hugo 主题，[官方文档](https://gohugo.io/themes/creating/)做了很详细的介绍。简单再介绍一下几个重点内容：

* layouts: 页面框架，hugo 中的页面框架有两种，一种是 single 页面，一种是 list 页面。single 页面用于展示单篇文档，list 页面用于展示文档列表。
* single content: 默认的 single 页面使用 `layouts/_default/single.html` 作为 layout。
* list content: 默认的 list 页面使用 `layouts/_default/list.html` 作为 layout。
* partial templates: 片段式模板，可在各模板中通过 `{{ partial "breadcrumb.html" . }}` 这种方式被引用。
* static: 静态资源。`static/` 目录下存放 css、js 等静态资源，在页面中引入即可生效。


### 🐣 模板

hugo 内置了一套模板语言，十分简单易学，掌握了基本语法之后，其他只需在用到时查阅[文档](https://gohugo.io/templates/introduction/)即可。

* 常用的方法：[functions](https://gohugo.io/functions/)
* 常用的变量：[variables](https://gohugo.io/variables/)


## 🐻 教程

跟我来一起实现一个最简单的云雀小站。对云雀小站的创建及使用有疑问的请查看[帮助文档](https://lark.alipay.com/lark/help/sites-help)。

这里参考我们的[默认 single 主题模板](http://gitlab.alibaba-inc.com/lark-site-themes/default)实现。

* step 1: 打开 terminal 执行以下命令：


```markup
hugo new site single

cd single

hugo new theme single
```

* step 2: 到 gitlab [lark-site-themes](http://gitlab.alibaba-inc.com/groups/lark-site-themes) 组里创建代码仓库（==注意：仓库必须是 public 的==），并提交刚刚创建的 [single 主题](http://gitlab.alibaba-inc.com/lark-site-themes/single)。
* step 3: 到云雀小站后台页面设置主题路径，并下载开发包(==//todo 请联系 @西临(xilin.zss) 咨询==)。用开发包里的 `content/`、`data/` 和 `config.toml` 替换本地创建的站点内容。
* step 4: 打开 `config.toml`，设置 `theme = "single"`，`baseURL = "/"`。


现在我们得到了以下文件结构：

```markup
.
├── archetypes
├── config.toml
├── content
    ├── nkeowo            // 我在小站里关联的仓库
    |   ├── _index.md     // <- yoursite.com/nkeowo/
    |   ├── cbadu2.md     // 仓库里的文档，通过 yoursite.com/nkeowo/cbadu2/ 访问
    |   ├── ……
    |   └── _index.md     // <- yoursite.com
├── data
├── static
└── themes
    └── single
        ├── archetypes
        ├── layouts
        |   ├── _default
        |   |   ├── list.html
        |   |   └── single.html
        |   ├── partials
        |   |   ├── header.html
        |   |   └── footer.html
        |   ├── 404.html
        |   └── index.html
        ├── static
        |   ├── js
        |   └── css
        └── theme.toml
```

然后就可以开始开发了。

在 terminal 中执行 `hugo server`，浏览器打开 [localhost:1313](http://localhost:1313/)，现在看到还是一片空白，我们试下在 `layouts/index.html` 中加一段文字，保存后刷新页面即可看到变化。

### 🐨 主页

如果你需要一个非常定制化的主页，在 `layouts/index.html` 中编写 html 即可。如果你只需要在主页里展示文档列表，可以把 index.html 删除，当 hugo 找不到 index.html 时，会找到 `_default/list.html` 来展示内容。在 `single` 主题里，我们就使用了这一小窍门。

### 🐵 公用模板

在多处页面需要用到的 html 片段，我们把它提取到 partials 下，变成独立的文件，例如 header.html，footer.html。

在 header.html 中写头部片段，header 比较简单，只需用到一些全局变量。一般情况下，我们可以通过 `.`来访问当前上下文， [$.](https://gohugo.io/templates/introduction/#2-use-to-access-the-global-context) 来访问到全局上下文。如果是 [partial](https://gohugo.io/templates/partials/#readout) 片段的话，需要在引入的时候将全局上下文传入，下面的 header 中将全局上下文赋值给了 `$.ctx`。更多上下文相关内容，请查阅[官方文档](https://gohugo.io/templates/introduction/#context-aka-the-dot)。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">

    <meta name="base-url" content="{{ $.ctx.Site.BaseURL }}">

    <!-- required, 指定页面 baseURL -->
    <base href="{{ $.ctx.Site.BaseURL }}">
    <link href="css/default.css" rel="stylesheet">
    
    <!-- 引入 css, js -->
    <link href="css/default.css" rel="stylesheet">
    <link href="https://a.alipayobjects.com/g/lark/lark-markdown/1.3.1/default.css" rel="stylesheet">
    <script src="https://a.alipayobjects.com/g/component/jquery/3.1.0/jquery.min.js" type="text/javascript" charset="utf-8"></script>
    
    <!-- 自定义页面 title -->
    <title>{{ $.ctx.Site.Title }} {{ $.ctx.Params.title }}</title>
  </head>
  <body data-url="{{ .RelPermalink }}">
    <div class="header">
      <div class="themebox"> 
        <div class="header-wrapper">
          <div class="logo">
            <a href="https://lark.alipay.com">
              <img class="logo-image" src="https://zos.alipayobjects.com/rmsportal/jwYNYECPqQYbpwpLhcry.svg" />
            <h1 class="lark-logo-text">云雀</h1>
            </a>
            <a href="." class="logo-link">
              {{ $.ctx.Site.Title }}
            </a>
          </div>
          <div class="brand">
            <h1 class="page-title">{{ $.ctx.Site.Title }}</h1>
            <p class="page-desc">{{ $.ctx.Site.Params.description }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="main {{ $.currentPage }}">
      <div class="main-wrapper">

```

在 footer.html 中写好页脚片段：

```html
        </div>
      </div>

      <div class="footer">
        <div class="footer-container clearfix">
          <p class="footer-logo"></p>
        </div>
      </div>
      <script src="https://a.alipayobjects.com/g/lark/lark-markdown/1.3.1/default.js" type="text/javascript" charset="utf-8"></script>
      <script src="js/main.js" type="text/javascript" charset="utf-8"></script>
  </body>
</html>
```

### 🐧 文档列表页

`_default/list.html`

```html
{{ partial "header.html" (dict "ctx" . "currentPage" "list") }}
<div class="main-container">
    <!-- //todo: doc list -->
</div>
{{ partial "footer.html" . }}
```

完成 header 和 footer 两个公用模板片段后，我们就可以在 list.html 中进行引用了。可以注意到我们在引用 header.html 的时候，传入了 `ctx` 和 `currentPage` 两个变量，所以在 header 中我们就可以通过 `$.ctx` 来访问全局上下文。[dict](https://gohugo.io/functions/dict) 是 hugo 模板中提供的方法。

想要获取到仓库下的文档列表，我们需要用到 `data/main.json` 这份数据，来看一下 `main.json`：

```json
{
  "sections": [
    {
      "name": "小站测试",               // 仓库名称
      "slug": "nkeowo",               // 仓库 slug
      "pages": [                      // 仓库下的目录
        {
          "title": "Home",            // 文档名称
          "slug": "gxnh4x",           // 文档 slug
          "depth": 1,                 // 文档在目录中的层级
          "isOutPath": false,         // 该文档是不是外部链接
          "isError": false,           
          "currentPath": "1",         // 该文档在目录中所处的节点，如 1.1, 1.2, 2.1……
          "rootPath": "1",            // 该文档从属的根节点
          "parent": true,             // 是否有子菜单
        },
        {
          "title": "Compatibility",
          "slug": "cofwp7",
          "depth": 1,
          "isOutPath": false,
          "isError": false,
          "currentPath": "2",
          "rootPath": "2"
        },
        ……
      ]
    }
  ]
}
```

结合 `main.json`，可以通过以下方式获取到当前仓库下的文档列表。

```html
{{/*
  doc list
*/}}

<div class="nav-section">
  <!-- 显示仓库名称 -->
  {{ range where .Site.Data.main.sections "slug" $.Params.section }}
    <h3 class="current-repo">{{ .name }}</h3>
  {{ end }}
  
  <nav class="nav-container">
    <ul class="catalog">
      <!-- 显示仓库下的文档列表 -->
      {{ range where .Site.Data.main.sections "slug" $.Params.section }}
        {{ $section := . }}

        <!-- pages 是仓库下的文档列表 -->
        {{ range .pages }}
          <li class="nav-item depth{{ .depth }} {{ if eq .slug $.Params.Slug }}current{{ end }} {{ if gt .depth 1 }}hidden{{ end }}" data-currentPath="{{.currentPath}}" data-rootPath="{{.rootPath}}">
          
          <!-- 有子菜单的一级菜单提供收起/展开按钮，交互需要自己在 js 里控制 -->
          {{ if .parent }}
            {{ if lt .depth 2 }}
              <span class="larkicon larkicon-caretdown toggle"></span>
            {{ end }}
          {{ end }}
          
          {{ if ne .slug "#" }}
            <a href="{{ if .isOutPath }}{{ .slug }}{{ else }}{{ $section.slug }}/{{ .slug }}{{ end }}" class="{{ if .isError }}error{{ end }}">
              <span class="name">{{ .title }}</span>
            </a>
          {{ else }}
            <span class="name">{{ .title }}</span>
          {{ end }}
          </li>
        {{ end }}
      {{ end }}
    </ul>
  </nav>
</div>
```

### 🐺 文档内容页

`_default/single.html`

```html
{{ partial "header.html" (dict "ctx" . "currentPage" "single") }}
<div class="main-container">
  <!-- //todo: doc content -->
</div>
{{ partial "footer.html" . }}
```

我们在前面的 [content](#content) 章节介绍过 `content/` 下每一篇 .md 文档中包含的那些变量，在这里就可以用上了。

```html
{{/*
  doc content
*/}}

<div class="artical-section larksite">
  <div class="doc-article">
    <article class="doc-article-inner">
      <div class="typo">
        {{ with .Title }}
          <h1 class="typo-title" itemprop="title"> {{ . }}</h1>
        {{ end }}
        <div class="typo-content">
          <!-- 小站在生成时已经做了 markdown to html，所以此处是直接引入了 html 内容 -->
          {{ .RawContent | safeHTML }}
        </div>
      </div>
    </article>
  </div>
</div>
```

### 🦄 搜索页

小站内支持文档搜索，当你需要单独的搜索页面时，在 `layouts/` 里添加 `section/search.html`，hugo 会自动找到这个页面作为 `yoursite.com/search` 的 layout。

```html
{{/*
  搜索页面 layout
*/}}

{{ partial "header.html" (dict "ctx" . "currentPage" "single") }}
<div class="main-container">
  <div class="search-breadcrumb">
    <a href=".">{{ .Site.Title }}</a>
    <span class="split"> / </span>
    <span>搜索结果</span>
    <span class="count">
      （<span id="search-count">0</span>
      条结果）
    </span>
  </div>
  <div class="search-results">
    <!-- 用来展示搜索结果 -->
    <ul id="result-list"></ul>
    <div class="empty-view">
      暂无搜索结果
    </div>
  </div>
</div>
{{ partial "footer.html" . }}
```

在 js 里调用我们提供的搜索接口来实现搜索：

* GET `http://yoursite.com/_search?q=keywords&offset=0&limit=20`


### 🐠 静态资源

将需要用到的静态资源存放到 `static/` 对应的目录下，在页面里引入即可，小站在发布时会自动将这些资源存放到 cdn 上。

---


至此，我们已经完成了一个最简单的站点主题。提交主题代码后，在小站后台里基于最新主题进行一次预览打包，即可预览到最新版本的站点。在此过程中如遇到任何问题，欢迎联系 @西临(xilin.zss) 咨询。 
