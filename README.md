# Edge Profile Desk

基于 OCS Desktop 开源项目改造的本地 Microsoft Edge 配置管理器。它为每个配置创建独立的 Edge 用户数据目录，可分别登录并手动查看账户页面。

本项目当前面向 Windows，不执行搜索、任务或积分操作，不保存 Microsoft 密码，也不读取浏览器 Cookie。每个 Edge 窗口由用户手动启动。

## 开发环境

```bash
# 启用 Corepack（Node.js 自带的包管理器管理工具，会自动识别 packageManager 字段安装对应版本的 pnpm）
corepack enable

# 安装依赖
pnpm install
```

## 运行

一键启动开发环境（同时运行 common 编译、Web 开发服务器、Electron 主进程）：

```bash
pnpm dev
```

也可以单独启动各个模块（各命令已自动处理 common 编译，无需手动执行）：

```bash
pnpm dev:web   # 仅启动 Web 开发服务器
pnpm dev:app   # 仅启动 Electron 主进程
```

开发模式下会打开桌面应用窗口。

## 打包

```bash
pnpm build
```

## 配置数据

Edge 可执行文件路径和配置名称保存在应用本地数据中。各配置的浏览数据分别保存在应用数据目录下的 `edge-profiles/<id>` 文件夹。删除配置会同时删除对应的 Edge 登录状态和本地浏览数据。

Edge Stable 默认安装位置会自动检测；也可以在应用中手动选择 `msedge.exe`。打开配置会启动独立 Edge 窗口并进入 Microsoft Rewards 官方页面，登录、查看和其他操作均由用户手动完成。

## 上游项目

本项目基于 [ocsjs/ocs-desktop](https://github.com/ocsjs/ocs-desktop)，遵循 MIT License。课程自动化相关界面、启动流程和更新流程在此改造版中不启用。

