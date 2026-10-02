<p align="center">
  <img src="./src/assets/logo-full-transparent.svg" width="72" alt="临界微光" />
</p>

<h1 align="center">临界微光</h1>

<p align="center">
  临界有光，边界可通。<br />
  <em>Where edges meet, glimmers emerge.</em>
</p>

<p align="center">
  <a href="https://www.glimverge.com"><img alt="www.glimverge.com" src="https://img.shields.io/badge/site-www.glimverge.com-5b3ddb?style=flat-square" /></a>
  <a href="https://github.com/glimverge/website/actions/workflows/deploy.yml"><img alt="Deploy" src="https://img.shields.io/github/actions/workflow/status/glimverge/website/deploy.yml?style=flat-square&label=deploy" /></a>
  <img alt="Node.js >= 22.12" src="https://img.shields.io/badge/node-%3E%3D22.12-3c873a?style=flat-square&logo=nodedotjs&logoColor=white" />
  <img alt="Astro 7" src="https://img.shields.io/badge/Astro-7-bc52ee?style=flat-square&logo=astro&logoColor=white" />
  <img alt="Tailwind CSS 4" src="https://img.shields.io/badge/Tailwind_CSS-4-38bdf8?style=flat-square&logo=tailwindcss&logoColor=white" />
</p>

<p align="center">
  <a href="#概览">概览</a> ·
  <a href="#本地开发">本地开发</a> ·
  <a href="#目录">目录</a> ·
  <a href="#部署">部署</a>
</p>

组织官网，线上地址 [www.glimverge.com](https://www.glimverge.com)。做极简、可靠的产品，持续探索技术前沿。名字由 Glimmer 与 Verge 拼合：Verge 是临界，Glimmer 是微光。

## 概览

静态站点，用 [Astro](https://astro.build) 构建，样式走 [Tailwind CSS](https://tailwindcss.com) v4。页面文案直接写在 `.astro` 文件里，没有内容集合或后端。

当前页面：

| 路径               | 内容                                                                       |
| ------------------ | -------------------------------------------------------------------------- |
| `/`                | 首页：关于、方向、项目入口                                                 |
| `/projects`        | 项目列表                                                                   |
| `/projects/moomem` | [moomem](https://github.com/glimverge/moomem)，MoonBit 嵌入式 Agent 记忆层 |

`/moomem` 会重定向到 `/projects/moomem`。

## 本地开发

需要 [Node.js](https://nodejs.org) 22.12 或更高版本，以及 [pnpm](https://pnpm.io) 12。

```sh
pnpm install
pnpm dev
```

开发服务器默认在 `http://localhost:4321`。

```sh
pnpm build     # 输出到 dist/
pnpm preview   # 本地预览生产构建
pnpm format    # 用 vite-plus 格式化
```

> [!TIP]
> `pnpm astro -- --help` 可以查看 Astro CLI。添加页面见 [Astro 路由文档](https://docs.astro.build/en/guides/routing/)。

## 目录

```text
src/
  assets/          标志
  components/      页框、图标
  layouts/         文档头与 meta
  pages/           路由
  styles/          Tailwind 主题与全局样式
public/            favicon、CNAME
astro.config.mjs   站点地址与重定向
```

`Frame` 提供顶栏、页脚和社交链接。新页面套上 `Layout` 和 `Frame` 即可。

颜色、字体写在 `src/styles/global.css` 的 `@theme` 里。图标来自 [Hugeicons](https://hugeicons.com) 和 [Simple Icons](https://simpleicons.org)。

## 部署

推送到 `main` 会跑 [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml)：`withastro/action` 构建，再发布到 GitHub Pages。Actions 页也可以手动触发。

自定义域名写在 [`public/CNAME`](public/CNAME)，对应 [www.glimverge.com](https://www.glimverge.com)。`astro.config.mjs` 里的 `site` 用来生成 canonical 和 Open Graph 地址，改域名时两处一起改。

> [!IMPORTANT]
> 合并进 `main` 即发布线上站点。先在本地跑一遍 `pnpm build`。
