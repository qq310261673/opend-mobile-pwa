# OpenD Mobile PWA V1.1

这是一个独立的手机 PWA 外壳，用来打开现有 OpenD 手机看板。

## V1.1 变化

- 保留固定 GitHub Pages 地址。
- 保留“设置 Tunnel 地址”。
- 删除 iframe 嵌入。
- 增加“进入5分钟看板”按钮。
- 点击按钮后，把当前 Cloudflare 看板地址作为顶层页面直接打开，规避部分 iPhone Safari 对跨站 iframe / Cookie 的限制。
- Cloudflare Quick Tunnel 地址变化时，只需在 PWA 内更新地址，不需要重新安装桌面图标。

## 安全边界

本项目不会修改：
- OpenD Desktop V1.1
- 冻结的 OpenD 扫描器 V2.13.2
- Drive
- SIGNAL-RECORDER
- 交易/模型/预测模块

它只在浏览器本地保存一个“手机看板 URL”，并在用户点击“进入5分钟看板”后直接跳转到该地址。

## 当前默认看板地址

https://flexibility-frame-madonna-indexes.trycloudflare.com

## 固定 PWA 地址

https://qq310261673.github.io/opend-mobile-pwa/

## iPhone 使用方式

1. Safari 打开固定 PWA 地址。
2. 点“分享” → “添加到主屏幕”。
3. 以后从桌面“OpenD 看板”图标进入。
4. 点“进入5分钟看板”直接打开当前看板。
5. 如果 Cloudflare Quick Tunnel 地址变化，返回 PWA，点“设置 Tunnel 地址”，粘贴新地址并保存。

## V1.1 设计限制

- PWA 固定入口不变，但当前后端仍使用 Cloudflare Quick Tunnel，因此 Tunnel URL 未来仍可能变化。
- Mac、本地 8766 看板服务和 Cloudflare Tunnel 必须处于运行状态，手机才能看到实时看板。
- PWA 不自动修改、重启或控制 OpenD、扫描器、Drive 或任何交易程序。
