title: Hexo and GitHub Pages as a blogging platform
date: 2014-04-18 12:57:24
tags:
---

这里记录下如何结合 Hexo 和 GitHub Pages 来写博客。Hexo 允许你用 markdown 写作，最后生成静态的 HTML 内容。Github Pages 允许你提交静态的网站，它帮你托管。二者结合，正好完成从写作到托管一整套博客流程。

以当前我的博客为例。我注册了两个源码库：https://github.com/tylerlong/blog 和 https://github.com/tylerlong/tylerlong.github.io。第一个源码库用来写作 markdown, 第二个用来托管最终的博客网站。为什么不用一个源码库的两个分支呢？ 因为第二个源码库的内容都是自动生成的，不想它和自己写作的内容混在一起。另外注意第二个源码库的名称，正好是我的博客的地址。

新建博客：

```shell
hexo init blog && cd blog
git init
git add .
git commit -a -m "Initial commit"
git remote add origin git@github.com:tylerlong/blog.git
git push -u origin master
```

修改 _config.yml 文件：

```yaml
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: github
  repository: git@github.com:tylerlong/tylerlong.github.io.git
  branch: master
```

修改 .gitignore 文件，添加：

```
public/
.deploy/
```

新建文章：

```shell
hexo new "Hexo and GitHub Pages"
```

生成文件的地址在 source/_posts/hexo-and-github-pages.md，撰写文章内容。


发布博客：

```shell
hexo generate
hexo deploy
```

浏览博客内容： [http://tylerlong.github.io/](http://tylerlong.github.io/)
