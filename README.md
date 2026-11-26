# NPA Plugins（插件仓库）

本仓库是 NPA 的**公开插件仓库**（plugin registry）。NPA 主体通过它发现、安装与升级插件。

- 索引文档：[`registry.json`](registry.json)（schema_version = 1）
- 构件：以 GitHub Release 附件形式发布，按平台区分
- 源码：NPA 主体 <https://github.com/dahaioup/npa>；远程桌面插件 <https://github.com/dahaioup/npa-remote>

## 在 NPA 中使用

Web 管理面 → **插件** 页 → 「插件仓库」填入：

```
https://github.com/dahaioup/npa-plugins/raw/main/registry.json
```

这是 NPA 的默认地址，也可通过环境变量 `NPA_PLUGIN_REGISTRY_URL` 覆盖。

## registry.json 字段

| 字段 | 说明 |
|---|---|
| `schema_version` | 索引格式版本，目前为 `1` |
| `plugins[]` | 插件条目列表 |
| `plugins[].id` / `name` / `version` | 标识与版本 |
| `plugins[].kind` | `plugin`（可执行插件）或 `dependency`（依赖组件） |
| `plugins[].capabilities` | 声明的能力位 |
| `plugins[].install.dir` / `install.executable` | 安装到数据目录下的位置与入口文件名 |
| `plugins[].artifacts[]` | 各平台构件：`os` / `arch` / `url` / `sha256` / `size` / `format` |

安装器会校验 `sha256` 后落盘到 NPA 数据目录。

## English

This repository hosts the public NPA plugin registry. `registry.json` is the index
document; platform binaries are published as GitHub release assets and verified by
sha256 before installation.

Default registry URL used by NPA:

```
https://github.com/dahaioup/npa-plugins/raw/main/registry.json
```
