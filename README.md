# 努力翻身 · PWA 主屏幕版

这是一个纯静态、离线可用的 iPhone PWA 记账工具。

## 最简单：Cloudflare Pages 直接拖 ZIP

1. 登录 Cloudflare → Workers & Pages。
2. Create application → Get started → Drag and drop your files。
3. 直接上传本 ZIP，或者上传解压后的整个文件夹。
4. Deploy site。
5. 用 iPhone Safari 打开生成的 `*.pages.dev` 地址。
6. Safari 分享 → 添加到主屏幕。

第一次需要联网打开；之后 Service Worker 会缓存页面，可离线使用。
记账数据保存在当前站点在这台 iPhone 上的浏览器本地存储中，不会自动上传到服务器。

## GitHub Pages

1. 新建一个 GitHub 仓库。
2. 把本文件夹中的所有内容上传到仓库根目录，默认分支使用 `main`。
3. 仓库 Settings → Pages → Build and deployment → Source 选择 `GitHub Actions`。
4. 推送后，仓库自带的 `.github/workflows/pages.yml` 会自动发布。
5. 打开 GitHub Pages 地址，然后在 iPhone Safari 中“添加到主屏幕”。

## 文件说明

- `index.html`：记账页面
- `manifest.webmanifest`：PWA 名称、图标和启动方式
- `sw.js`：离线缓存
- `icons/`：iPhone / PWA 图标
- `.github/workflows/pages.yml`：GitHub Pages 自动部署
- `.nojekyll`：GitHub Pages 静态文件兼容
- `_headers`：Cloudflare Pages 上让 Service Worker/manifest 更容易及时更新

## 数据与备份

- 日常数据仍保存在手机本地。
- 更换域名、换浏览器、清除 Safari 网站数据或删除站点数据，都可能让本地记录不可见。
- 建议定期使用页面里的“导出备份”，保存 JSON 文件。
- 恢复时使用“导入恢复”。
