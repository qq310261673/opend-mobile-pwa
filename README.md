# OpenD Mobile PWA V1.0

这是一个独立的手机 PWA 外壳，用来打开现有 OpenD 手机看板。

## 安全边界

本项目不会修改：
- OpenD Desktop V1.1
- 冻结的 OpenD 扫描器 V2.13.2
- Drive
- SIGNAL-RECORDER
- 交易/模型/预测模块

它只在浏览器本地保存一个“手机看板 URL”，然后通过 iframe 加载该地址。

## 当前默认看板地址

https://flexibility-frame-madonna-indexes.trycloudflare.com

如果 Cloudflare Quick Tunnel 以后生成了新地址，不需要重新安装 PWA：打开 App 右上角“设置”，把新地址粘贴进去即可。

## 本地测试（Mac）

在本目录执行：

```bash
python3 -m http.server 8770 --bind 127.0.0.1
```

然后在 Mac 浏览器打开：

http://127.0.0.1:8770/

说明：localhost 可以测试 PWA shell，但 iPhone 安装 PWA 需要 HTTPS。

## iPhone 安装方式（推荐）

把本文件夹部署到一个固定 HTTPS 静态站点（例如 GitHub Pages / Cloudflare Pages），然后：

1. iPhone Safari 打开固定 HTTPS 地址。
2. 点“分享”。
3. 选择“添加到主屏幕”。
4. 开启“作为网页 App 打开”（如果系统显示该选项）。
5. 添加。

以后桌面图标固定。Cloudflare 临时 Tunnel 地址变化时，只需在 App 内点“设置”更新看板 URL。

## V1.0 设计限制

- PWA 本身需要一个固定 HTTPS 托管地址才能实现“桌面 App 图标永久不变”。
- 当前 OpenD 看板仍依赖 Cloudflare Quick Tunnel，因此后端 URL 可能变化。
- 如果看板服务未来禁止 iframe 嵌入（例如设置 X-Frame-Options / CSP frame-ancestors），PWA 需要改为同源反向代理或固定 Tunnel 域名方案。
