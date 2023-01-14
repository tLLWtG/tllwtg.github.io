# tllwtg.github.io

Hi! This is my personal website **[tLLWtG Blog](https://tllwtg.github.io)**.

> The Jekyll theme is based on Hux Blog.

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

## UPD

* 2022.12.22

1. Sidebar 中添加了**一言**模块。
2. 引入了**百度统计**的脚本用于分析访问数据。
3. 使用**百度搜索资源平台**方便进行 SEO。
   
* 2022.12.23
  
1. 增加了 **robots.txt** 文件以禁止不必要的内容爬取。
2. 安装了 **jekyll-sitemap** 插件用于自动生成 sitemap.xml，方便搜索引擎抓取内容。
3. 增加主页 intro-header 随机选择背景图的脚本

* 2022.12.24

1. 修复主页 intro-header 随机背景图显示不完全的 Bug (主页自适应背景图


* 2022.12.26

1. 加入busuanzi的访客统计功能

* 2022.01.08

1. 给**一言**模块添加刷新按钮
2. 加入动画效果

## License

This project is licensed under the [Apache License 2.0](https://github.com/tLLWtG/tLLWtG.github.io/blob/main/LICENSE).
