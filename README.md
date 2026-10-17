# hellolpk-lzcapp

`cloud.lazycat.app.hellolpk`（环境探针）的 LPK 打包工程，用
[ca-x/lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 做构建与商店更新。

- 工程类型：自研源码（Vue 3 + Vite），**无上游镜像**
- 版本来源：`version_source.type: git` —— 推 tag `v*` 决定版本，tag `v1.0.1` 即产出 `1.0.1`
- Action 固定提交：`3dabca95f6eb0c3a6c4fc889631b13a055852912`

## 自动更新怎么走

1. 推 tag：`git tag v1.0.1 && git push origin v1.0.1`
2. Action 把 `package.yml` 的 version 改成 tag 的版本
3. 执行 `lzc-build.yml` 的 buildscript（`npm install && npm run build`）产出 `dist/`
4. 打 LPK 到 `out/hellolpk.lpk`，发 GitHub Release（资产名 `<package-id>-v<version>.lpk`）
5. 提交官方商店审核单（`stores.official.enabled: true`）

也可以在 Actions 页面手动触发，`operation` 选 `check` / `build` / `publish-official`。

## 前提

- 仓库 Secret `LAZYCAT_TOKEN`：lzc-cli 会话 token（走 `X-User-Token`），不是开发者中心 PAT。
  上游两种凭据不要同时映射。
- 应用必须已建档；本仓库 `create_if_missing: false`，不带 `application` 元数据块。

## 与本工程其它仓库的差别

tracearr / twikoo / defectdojo / bar-assistant 走的是 `version_source: image`（跟随上游镜像标签）。
本仓库没有镜像，所以用 `git` 版本源，`images: []`。
