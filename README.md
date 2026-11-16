# 截图贴图（Android）

截图后把图片钉在屏幕上、随时拖动缩放的轻量工具。纯 Java、手工命令行构建（aapt2 → javac → d8 → zipalign → apksigner）。

## 功能
- 悬浮球常驻：点一下把最新截图钉在屏幕上
- 贴图支持单指拖动、双指缩放、长按半透明、双击关闭
- 从相册选图直接贴图，长按贴图保存到相册
- 状态栏快捷开关一键截屏 / 进入选图
- 截屏后可框选区域再贴图
- 应用内在线更新：读取签名清单 → 校验 sha256 → 安装

## 目录
```
pinshot/                  Android 工程
  src/com/example/pinshot/ 主界面、悬浮服务、框选、OTA
  build.sh                手工构建脚本（release 密钥库在 ../secrets，不进仓库）
dist/                     OTA 分发目录
  update.json            单文件自包含签名清单 {"payload","sig"}
  app-<版本>.apk         每版独立文件名，避免缓存拿旧包
```

## 签名
独立 release 密钥，证书 SHA-256：`8710795f38a3d1a81ca9a7371d1c3eb25a119461f271d7197069313ebbbeb57c`
密钥库不随源码公开；换签名后首装需卸载旧版。

- 包名：`com.example.pinshot`
- 当前版本：v1.9.6（versionCode 16）
