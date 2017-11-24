# 小站帮助文档

:::danger
由于小站不稳定，目前已经停止申请内测，请勿提交申请！
:::

云雀小站是我们提供的一种站点服务。它可以快速将你的一个仓库或者多个仓库直接生成一个独立站点，发布对外。目前还在内部测试中，如果需要开通该功能，联系@子溯(xiongwei.cxw) 

### 如何新建

进入小站管理界面，在小站列表中点击 “新建小站”

![Screen Shot 2017-06-01 at 15.04.47.png | center](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/7237/30796de1c8a11199.png "")


选择 “对内站点” 或者 “对外站点”。注意, 所有新建小站都需要进行审核，审核人：子溯。内测阶段我们只开通符合小站需求的用户。  
![Screen Shot 2017-08-02 at 10.10.43.png | center | 1520x1051](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/undefined/4fca493e8a49521b.png "")


小站提供三种模式的主题，可以选择你需要的主题。

![Screen Shot 2017-08-02 at 10.10.46.png | center | 1520x1051](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/undefined/d38825723c276242.png "")


### 绑定仓库

新建小站后，进入小站的管理界面，可以添加文档的数据源，绑定云雀的仓库。我们会读取你在云雀上拥有 Owner 权限的仓库。

![Screen Shot 2017-06-01 at 15.46.14.png | center](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/7237/acb28cf8fbeee163.png "")


### 数据同步

绑定后，即可进入仓库将文档同步到小站，注意！文档同步需要手动触发，点击右上角`提交发布到小站`，即可自行同步，同步完成后，小站会自动生成预览版本。你可以查看预览版本的文档是否有误，确认后可以执行发布动作。

![db8f6896a9bd63f6.png | center](https://private-alipayobjects.alipay.com/alipay-rmsdeploy-image/skylark/png/3/db8f6896a9bd63f6.png "")


### 小站发布

点击发布后，会进入发布流程。如果是内部小站，不需要进行审核，如果是对外小站，需要进行审核通过后才能进入下一步。

### 其他问题

**如何触发预览版本更新？**

目前小站的预览版本更新逻辑是，当检测到仓库有新的文档同步过来，或者小站配置发生变更的时候会触发自动生成预览版本。

**如何绑定自定义域名？**

目前小站提供了是 `docs.alipay.com` 下的访问域名，用户可以根据自己需要绑定，将申请的到的域名 CNAME 到 `docs.alipay.com` 即可。如果遇到问题可以联系所在 BU 的运维同学协助绑定。

**如何自定义主题？**

目前小站针对三种内容类型提供了3套默认主题，如果需要自己定义，可以前往我们的官方模版库，选择一个适合自己小站的主题，根据[主题开发帮助](site-theme)进行二次开发，然后联系 @遇春 更改小站模版设置，后续可以在主题设置里自行设置。

**小站会有权限控制吗？**

会有，我们会在第二期加入权限控制。

**文档中有内网的图片链接发到小站怎么访问？**

我们会默认将这些图片做一个转换，这样外网用户也可以访问到目前的图片链接。
