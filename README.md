# 心动空间 · Supabase 云端版

这是一个双人情侣空间静态前端，已连接 Supabase 项目 `qingyin-v36`。

## 已接入
- Supabase Auth：邮箱/密码注册、登录、退出
- PostgreSQL：情侣空间成员、悄悄话、照片记录、页面设置
- Row Level Security：只有登录后的空间成员可读写共享内容；页面设置仅空间创建者可修改
- Supabase Storage：私有 `couple-media` Bucket，图片通过短时签名 URL 展示
- Realtime：新悄悄话和照片上传后自动刷新

## 使用
请通过 HTTP 静态服务器访问，不建议直接 `file://` 打开。例如：

```bash
python3 -m http.server 8080
```

然后访问 `http://localhost:8080`。

首次使用：输入邮箱、至少 6 位密码、昵称并注册。若 Supabase Auth 开启邮箱确认，需要先点击验证邮件，再回来登录。第一个加入固定情侣空间的账号会成为页面设置的 owner。

## 部署
可部署到任意静态托管（Cloudflare Pages、Vercel、Netlify、GitHub Pages 等）。前端只包含 Supabase publishable key；不要把 service_role/secret key 放进浏览器代码。

## 手机桌面图标 / PWA
本版本已加入 manifest、favicon 与 service worker。部署到 HTTPS 后，可在 iPhone Safari 的“添加到主屏幕”或 Android Chrome 的“安装应用”中添加到桌面。

## 自定义域名
发布到 Netlify 后，可在 Site configuration -> Domain management 中添加自定义域名。域名 DNS 按 Netlify 页面给出的记录配置即可。
