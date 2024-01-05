<img src="https://cdn.statically.io/gh/craigary/nobelium/main/Nobelium-Logo.svg" width="50" height="50">

# 我的Nobelium博客

通过Notion和Nextjs静态博客，部署在 [Vercel](https://vercel.com?utm_source=Craigary&utm_campaign=oss)上。

<p>
  <a aria-label="GitHub commit activity" href="https://github.com/craigary/nobelium/commits/main" title="GitHub commit activity">
    <img src="https://img.shields.io/github/commit-activity/m/craigary/nobelium?style=for-the-badge">
  </a>
  <a aria-label="GitHub contributors" href="https://github.com/craigary/nobelium/graphs/contributors" title="GitHub contributors">
    <img src="https://img.shields.io/github/contributors/craigary/nobelium?color=orange&style=for-the-badge">
  </a>
  <a aria-label="Build status" href="#" title="Build status">
    <img src="https://img.shields.io/github/deployments/craigary/nobelium/Preview?logo=Vercel&style=for-the-badge">
  </a>
  <a aria-label="Powered by Vercel" href="https://vercel.com?utm_source=Craigary&utm_campaign=oss" title="Powered by Vercel">
    <img src="https://www.datocms-assets.com/31049/1618983297-powered-by-vercel.svg" height="28">
  </a>
</p>

Demo: [https://nobelium.vercel.app/](https://nobelium.vercel.app/)

<details><summary>页面截图</summary>
<img src="https://github.com/craigary/nobelium/blob/main/desktop.png?raw=true">
</details>

## 特点 ✨
<details>
  <summary><b>🚀 &nbsp;快速、准实时响应</b></summary>
&nbsp;- Fast page render and responsive design<br>
&nbsp;- Fast static generation with efficient compiler
</details>

<details>
  <summary><b>🤖 &nbsp;快速部署</b></summary>
&nbsp;- Deploy on Vercel in minutes<br>
&nbsp;- 无需重新部署即可自动生成新增内容
</details>


<details>
  <summary><b>🚙 &nbsp;功能齐全</b></summary>
&nbsp;- Comments, full width page, quick search and tag filter<br>
&nbsp;- RSS, analytics, web vital... and much more
</details>

<details>
  <summary><b>🎨 &nbsp;易于定制**</b></summary>
&nbsp;- 丰富的配置选项, support English & Chinese interface<br>
&nbsp;- Built with Tailwind CSS, 易于定制
</details>

**🕸 &nbsp;Pretty URLs and SEO friendly**

## 快速启动（原repo）

- Duplicate [这个Notion模板](https://craigary.notion.site/866916e3b939468b9b6f1d47dce99f9c)，并通过shear设置为publish；
- Fork [这个](https://github.com/craigary/nobelium/fork)项目；
- 自定义修改 `blog.config.js`；
- _(可选)_ 替换`/publish`目录中的 `favicon.svg` 和 `favicon.ico`，这是自己的网站 logo；
-  在[Vercel](https://vercel.com)上进行部署，设置以下环境变量：
  - `NOTION_PAGE_ID` (必需): 已设置共享位web的Notion页面的ID，通常为workspace地址后的32位数字；
  - `NOTION_ACCESS_TOKEN` (可选, 不推荐): 如果你不分享这个database，你可以利用token来让Nobelium从database中抓取数据，你可以在浏览器cookies中找到它，它叫`token_v2`
    - 记住，token有效期只有180填, 需要在vercel的dashboard进行手动更新。
- **就这些**，较简单不

<details><summary>Page ID 在这里？</summary>
  <img src="https://github.com/craigary/nobelium/blob/main/pageid.png?raw=true">
</details>

## 在Docker上把玩

非官方, 感谢 [@Vaayne](https://github.com/craigary/nobelium/pull/157)的工作!

### 构建自己的Docker镜像
```
# set env
export NOTION_PAGE_ID=xxx # your NOTION_PAGE_ID
export IMAGE=nobelium:latest

# build with docker
docker build -t ${IMAGE} --build-arg NOTION_PAGE_ID .

# run with docker
docker run -d --name nobelium -p 3000:3000 -e NOTION_PAGE_ID=${NOTION_PAGE_ID} nobelium:latest
```

### 使用默认docker镜像
```
# pull image
docker pull ghcr.io/craigary/nobelium:main

# run with docker
docker run -d --name nobelium -p 3000:3000 -e NOTION_PAGE_ID=${NOTION_PAGE_ID} ghcr.io/craigary/nobelium:main
```

## 路线图

在[这里](https://craigary.notion.site/Public-Roadmap-89d184e51653445ab5b347e4efac079e)查看我们的路线图.

- [x] Better SEO
- [x] Dark mode
- [x] Open Graph support
- [x] Switch to react-notion-x
- [x] Sitemap
- [ ] ...

## 技术细节

- **Generation**: Next.js and Incremental Static Regeneration
- **Page render**: [react-notion-x](https://github.com/NotionX/react-notion-x)
- **Style**: Tailwind CSS and `@tailwindcss/jit` compiler
- **Comments**: Gitalk, Cusdis and more

## FAQ

<details>
  <summary>如何更改头像?</summary>
  Nobelium会从<a href="https://gravatar.com">Gravatar</a>获取头像，所以你需要在这儿设置你的头像，记得使用<code>blog.config.js</code>中设置的email</strong>。
</details>
<details>
  <summary>我在Notion中设置了分组后文章就消失了!</summary>
  Nobelium目前还不支持 Notion database 的分组功能. 如果想分组管理你的文章，可以尝试新建database的多个view，然后后通过filter过滤不通的分组.
</details>

## 鸣谢

<table><tr align="left">
  <td align="center"><a href="https://notion.so/cnotion" title="Notion CN Community"><img src="https://avatars.githubusercontent.com/u/4792552" width="64px;"alt="Notion CN Community"/></a><br/><a href="https://notion.so/cnotion" title="Notion CN Community">Notion CN Community</a></td>
  <td align="center"><a href="https://twitter.com/SilentDepthCN" title="SilentDepth"><img src="https://avatars.githubusercontent.com/u/7194254" width="64px;" alt="yokinist"/></a><br/><a href="https://twitter.com/SilentDepthCN" title="SilentDepth">SilentDepth</a></td>
  <td align="center"><a href="https://leerob.io/" title="Lee Robinson"><img src="https://avatars.githubusercontent.com/u/9113740" width="64px;" alt="Reynard"/></a><br/><a href="https://leerob.io" title="Lee Robinson">Lee Robinson</a></td>
  <td align="center"><a href="https://spencerwoo.com/" title="Spencer Woo"><img src="https://avatars.githubusercontent.com/u/32114380" width="64px;" alt="Niin"/></a><br/><a href="https://spencerwoo.com" title="Spencer Woo">Spencer Woo</a></td>
</tr></table>

## 贡献者

<table><tr align="left">
  <td align="center"><a href="https://github.com/craigary"><img src="https://avatars.githubusercontent.com/u/10571717" width="64px;"alt="Craig Hart"/><br/><sub><b>Craig Hart</b></sub></a><br/><a href="https://github.com/craigary/nobelium/commits?author=craigary" title="Owner" >🎫 🔧 🎨 🐛</a></td>
  <td align="center"><a href="https://github.com/yokinist"><img src="https://avatars.githubusercontent.com/u/19779874" width="64px;" alt="yokinist"/><br/><sub><b>yokinist</b></sub></a><br/><a href="https://github.com/craigary/nobelium/commits?author=yokinist" title="yokinist" >🔧 🐛</a></td>
  <td align="center"><a href="https://github.com/reycn"><img src="https://avatars.githubusercontent.com/u/11225092" width="64px;" alt="Reynard"/><br/><sub><b>Reynard</b></sub></a><br/><a href="https://github.com/craigary/nobelium/commits?author=reycn" title="Reynard" > 🎨 🐛</a></td>
  <td align="center"><a href="https://github.com/Niinjoy"><img src="https://avatars.githubusercontent.com/u/39721307" width="64px;" alt="Niin"/><br/><sub><b>Niin</b></sub></a><br/><a href="https://github.com/craigary/nobelium/commits?author=Niinjoy" title="Niin" >🔧 🐛</a></td>
  <td align="center"><a href="https://github.com/ruter"><img src="https://avatars.githubusercontent.com/u/8568876" width="64px;" alt="Ruter"/><br/><sub><b>Ruter</b></sub></a><br/><a href="https://github.com/craigary/nobelium/commits?author=ruter" title="Ruter" >🔧 🐛</a></td>
</tr></table>

## 许可

The MIT License.
