# 活动提醒助手 - 转为 Android 应用

## 文件结构
```
index.html       ← 主应用
manifest.json    ← PWA 配置
sw.js            ← 离线缓存 Service Worker
icon-192.png     ← 应用图标 192x192
icon-512.png     ← 应用图标 512x512
```

## 方案一：安装为 PWA（推荐，最快）

### 步骤：
1. 在电脑上启动本地服务器：
   - 安装 Python 后，在此文件夹打开命令行，运行：
     ```
     python -m http.server 8080
     ```
   - 或使用 Node.js：`npx serve .`

2. 手机和电脑连接同一个 WiFi

3. 查看电脑的局域网 IP（命令行运行 `ipconfig`，找 IPv4 地址）

4. 手机浏览器访问 `http://电脑IP:8080`

5. Chrome 会自动弹出"添加到主屏幕"提示，点击即可安装
   - 如果没有弹出，点击浏览器菜单 → "添加到主屏幕"

安装后，活动提醒助手就像普通 App 一样出现在手机桌面，点击图标即可打开。

## 方案二：打包为 APK 安装包

### 方式 A：使用 PWABuilder（最简单）
1. 将整个文件夹打包成 ZIP
2. 上传到 https://pwabuilder.com
3. 网站自动生成 APK 文件
4. 下载 APK 传输到手机安装

### 方式 B：使用 Bubblewrap（Google 官方工具）
需要安装 Node.js，然后：
```
npm install -g @bubblewrap/cli
bubblewrap init --manifest=https://你的网址/manifest.json
bubblewrap build
```

## 注意事项
- PWA 需要 HTTPS 或 localhost 才能触发安装提示
- file:// 协议不支持 Service Worker
- 数据存储在手机浏览器的 localStorage 中，卸载浏览器数据会丢失
- 如需云同步，可部署到 GitHub Pages 等免费静态托管
