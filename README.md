# 涂林档案

[![Netlify Status](https://api.netlify.com/api/v1/badges/a995b364-61c0-470d-802b-902ca70b34bb/deploy-status)](https://app.netlify.com/sites/tulin/deploys) [![GitHub last commit](https://img.shields.io/github/last-commit/talentedbug/tulinarchive?logo=github&color=purple)](https://github.com/talentedbug/tulinarchive)

欢迎来到涂林档案的 GitHub 仓库！

在这篇 README 中，我将主要介绍涂林档案和网站的技术细节。如果您更想了解涂林和涂林档案的由来，请查看[涂林档案网站](https://tulin.netlify.app)，或在本仓库内前往 [index.md](https://github.com/talentedbug/tulinarchive/blob/main/docs/index.md) 直接查看。

## 1. 数据集

涂林档案原件以纸质为主，整体保存情况较为复杂，如部分作品写在餐巾纸上，墨色极淡，传统复印扫描无法清晰复制信息，因此我采用了以下方案：

- 设备：Redmi K70 Pro
- 相机：5000 万像素，光影猎人 800 传感器，使用全彩文档模式初步扫描
- 排版：先物理排版，保证大小不超过 A4 尺寸，再通过软件处理
- 文件格式：JPEG（无压缩）

实际效果可见色彩饱和度偏高，但是对于不清晰的笔画捕捉较好，画质较高，但是也导致每张图片的大小达到 2 MiB 以上，总数据集信息如下：

|部分|文件格式|数量|总大小|
|-|-|-|-|
|班长|.kra，.png，.pdf，.docx|17|31.5 MiB|
|徐贼|.jpg|37|55.0 MiB|
|姚姐|.jpg|172|399.7 MiB|
|小丽|.jpg|30|66.3 MiB|

> 注：以上统计数据是根据 Dolphin 文件管理器的统计信息，与 Windows 及其他平台上的显示最多有 ±5 MiB 的误差。并且，部分作品分类不清晰，例如姚姐的分类中包含了很多其他成员作品，但是由于我比较懒，没有仔细分类。

总数据集的大小经过 .zip 打包为 585.5 MiB，经过 .tar.gz 打包为 586.1 MiB，原始数据集大小为 599.0 MiB。

## 2. 网站

由于涂林档案的根本目的是保存，我选择了 [GitHub](https://github.com) 作为代码托管平台，[Netlify](https://www.netlify.app) 作为静态页面部署平台。选择 GitHub 当然是国际惯例了，而 Netlify 的选择则是因为它在中国大陆优异的 CDN 表现。

这两家的免费服务均可以无限使用，但是 Netlify 有每月 100 MiB 的流量限制，GitHub 有 300 MiB 的单个文件大小限制，因此我将打包的数据集托管在 GitHub 的 [Release](https://github.com/talentedbug/tulinarchive/releases) 页面。

关于网站框架，我选择了 [MkDocs](https://www.mkdocs.org) 和适用于它的 [Material](https://squidfunk.github.io/mkdocs-material) 主题。它们都有广泛的用户基础，功能也相当完善。为了防止长期的开发闲置导致页面不兼容，我还用旧版的 Tulin Archive 为基础，搭建了[备份网站](https://tulin.netlify.app/bak/index.html)。

详细的搭建版本号信息，请参见以下配置介绍。

对于网站的配置，请详见仓库根目录下的配置文件。每个文件对应的配置类型是：

- mkdocs.yml：MkDocs 以及 Material for MkDocs 的配置文件。配置文件的含义请见 Material for MkDocs 的[文档](https://squidfunk.github.io/mkdocs-material/setup)。
- netlify.toml：Netlify 配置自动化，非常简单，不多解释。
- requirements.txt：Netlify 部署 Python 环境的依赖列表，包括 `mkdocs` 和 `mkdocs-material`。
- runtime.txt：Python 版本信息，Netlify 支持 3.8 和 2.7 两个版本，由于 MkDocs 只支持 3.8，因此选择。最新的 3.12 版本并不支持。

网站的目录结构如下：

```
tulinarchive
|- bak - 备份网站，拥有完整的文件索引和简单的英文介绍
|- dataset - 数据集根目录
  |- Banzhang
    |- ...
  |- Xiaoli
    |- ...
  |- Xuzei
    |- ...
  |- Yaojie
    |- ... - 分别是班长、小丽、徐贼、姚姐的作品位置
|- docs - 网站源文件，使用 Markdown 写作，由MkDocs 进行渲染
  |- Banzhang
    |- ...
  |- Xiaoli
    |- ...
  |- Xuzei
    |- ...
  |- Yaojie
    |- ...
|- ... - 以上所提到的配置文件
|- index.html - 用于重定向至生成的页面
```

## 3. 协议

涂林档案的代码部分，及除 `docs` 和 `dataset` 目录下所有文件，适用于 [The Unlicense](https://unlicense.org/)；文档部分，适用于 [CC0](https://creativecommons.org/public-domain/cc0/) 协议。放弃所有权利。

您可以自由复制、分发、修改、再发布、售卖本作品，并且没有署名的强制要求。

## 4. 致谢

作为涂林档案建立的负责人，我首先感谢与我共度初中三年的同学们，尤其是档案中提到的另三位涂林核心成员。他们与我一同创造了许许多多有趣有思考的作品，因此尽管班级上的一些同学对我不甚友好，我也能愉快地度过时光。很遗憾他们的真名在这里不便公布。

还要感谢本文中提及的所有开源软件开发者和免费服务提供者，他们的网站链接在上文已经全部提及，这里不再赘述。你们的付出让涂林档案更加稳定和持久。

当然还要感谢这个项目本身，在开发过程中我（作为纯后端）不仅学习了许许多多关于 HTML/CSS 和 JavaScript 的知识，还将自己的中文打字速度猛增到了 40 字每分钟。

## 5. 联系

关于网站技术上的问题和建议，请在仓库中提交 Issue，便于一一完成修改。

关于网站内容等其他话题，请前往涂林档案网站查看联系方式，以及一些注意事项。
