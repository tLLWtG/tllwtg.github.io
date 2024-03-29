# tllwtg.github.io

Hi! This is my personal website **[tLLWtG Blog](https://tllwtg.top)**.

> The Jekyll theme is derived from [Hux Blog](https://github.com/Huxpro/huxpro.github.io).

## Deploy

1. You will need [Ruby](https://www.ruby-lang.org/en/) and [Bundler](https://bundler.io/) to use [Jekyll](https://jekyllrb.com/). Following [Using Jekyll with Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/) to fullfill the enviromental requirement.

2. Installed dependencies in the `Gemfile`:

```sh
$ bundle install 
```

3. Serve the website (`localhost:4000` by default):

```sh
$ bundle exec jekyll serve  # alternatively, npm start
```

#### Mirrors

You can also get this repo from gitee.

```sh
$ git clone https://gitee.com/tllwtg/tllwtg.github.io.git
```

#### Offline version

1. You can simply build a static website with the content of `gh-pages` branch.
> Besides, it's also a good choice to just download "tLLWtG_Blog.zip" in Releases(usually out of date though).

```sh
$ git clone https://github.com/tLLWtG/tllwtg.github.io.git -b gh-pages
```

2. After cloning the repo or decompression, start a http server with the following commands.

```sh
$ cd tllwtg.github.io  # or, cd tLLWtG_Blog
$ python -m http.server
```

3. If you started your http server successfully, you will see something like this in you terminal:

```sh
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```

Now you can visit tLLWtG_Blog through the url shown in your terminal.
> Sometimes you have to replace `0.0.0.0:` with `localhost:`.  
> And if your port `8000` is occupied, please set andother port like this `python -m http.server 1234`.

## Development

**[User Manual of Blog](_doc/Manual.md)**

#### GitHub Action

Since tLLWtG Blog uses [**action-build-deploy-ghpages**](https://github.com/EdricChan03/action-build-deploy-ghpages) to **build and deploy** on GitHub Pages, you have to fork that repo, and modify `.github/workflows/main.yml`, where you are supposed to substitute `- uses: tLLWtG/action-build-deploy-ghpages@main` with `- uses: <yourusername>/action-build-deploy-ghpages@main`.  
Otherwise, you should delete the folder `.github`, and deploy according to the normal steps suggested by GitHub Pages.

## UPD

* 2023.01..29

1. 开通基于 Vercel 的镜像站 **mirror.tllwtg.top**
2. 修改侧边栏样式
3. 增加新的**友链**页面

* 2023.01.28

1. 打开 **RSS** 订阅
2. 开通 **giscus** 的评论系统

* 2023.01.27

1. URL 由 tllwtg.github.io 更改为 **tllwtg.top**
2. 更新 Google 和百度的网站工具设置

* 2023.01.16

1. 引入 **Google Analytics** 的脚本用于分析访问数据
2. 引入 **Google Search Console** 进行 SEO
3. 添加 **Google Adsense**

* 2023.01.14

1. 取消 GitHub Pages 的默认 Jekyll-Build-Pages action
2. 使用 **action-build-deploy-ghpages** 自动构建 gh-pages 分支，并在 gh-pages 分支上直接部署静态网站(方便后续添加不在 GitHub 白名单上的插件，同时能自动更新 gh-pages)

* 2023.01.08

1. 给**一言**模块添加刷新按钮
2. 加入动画效果

* 2022.12.26

1. 加入 **busuanzi** 的访客统计功能

* 2022.12.24

1. 修复主页 intro-header 随机背景图显示不完全的 Bug (主页自适应背景图)

* 2022.12.23
  
1. 增加了 **robots.txt** 文件以禁止不必要的内容爬取。
2. 安装了 **jekyll-sitemap** 插件用于自动生成 sitemap.xml，方便搜索引擎抓取内容。
3. 增加主页 intro-header 随机选择背景图的脚本

* 2022.12.22

1. Sidebar 中添加了**一言**模块。
2. 引入了**百度统计**的脚本用于分析访问数据。
3. 使用**百度搜索资源平台**方便进行 SEO。

## License

This project is licensed under the [Apache License 2.0](https://github.com/tLLWtG/tllwtg.github.io/blob/main/LICENSE).
