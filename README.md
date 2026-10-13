# OpenD Mobile PWA V1.2

这是一个独立的手机 PWA 外壳，用来打开现有 OpenD 手机看板。

## V1.2 变化

- 保留固定 GitHub Pages 地址。
- 删除“每台手机各自保存 Tunnel 地址”的方式。
- 新增仓库根目录 `config.json`，所有手机统一读取其中的 `tunnel_url`。
- `config.json` 每次读取都使用 `no-store`，Service Worker 也明确不缓存它，减少手机读到旧 Tunnel 地址的风险。
- 点“进入5分钟看板”前会再次读取中央配置，再直接作为顶层页面打开 Cloudflare 看板。
- 点“刷新中央地址”可以手动重新读取中央配置。

## 当前中央配置

`config.json`

```json
{
  "tunnel_url": "https://flexibility-frame-madonna-indexes.trycloudflare.com"
}
```

以后 Cloudflare Quick Tunnel 地址变化时，只需要修改这一个文件里的 `tunnel_url`。所有手机下次打开 PWA 或点“刷新中央地址”时都会读取新地址，不需要逐台手机修改。

## 固定 PWA 地址

https://qq310261673.github.io/opend-mobile-pwa/

## iPhone 使用方式

1. Safari 打开固定 PWA 地址。
2. 点“分享” → “添加到主屏幕”。
3. 以后从桌面“OpenD 看板”图标进入。
4. 页面自动读取中央 Tunnel 地址。
5. 点“进入5分钟看板”直接打开当前看板。

## 安全边界

本项目不会修改：
- OpenD Desktop V1.1
- 冻结的 OpenD 扫描器 V2.13.2
- Drive
- SIGNAL-RECORDER
- 交易/模型/预测模块

PWA 只读取 GitHub Pages 上的 `config.json` 并跳转到其中配置的 HTTPS 看板地址。

## V1.2 设计限制

- 后端仍使用 Cloudflare Quick Tunnel，因此 Tunnel URL 未来仍可能变化。
- Mac、本地 8766 看板服务和 Cloudflare Tunnel 必须处于运行状态，手机才能看到实时看板。
- 如果中央配置暂时无法读取，V1.2 会停止跳转并提示刷新，不会自动使用未知或旧的地址。
