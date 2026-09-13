# Su-Releases

素（Su）的安装包发布页。源码不在这里。

下载请去 [then.md](https://then.md)，或者直接看 [Releases](https://github.com/Quorafind/Su-Releases/releases)。

## 每个版本有哪些文件

**Windows**

| 文件 | 说明 |
| --- | --- |
| `Su-Setup-<版本>.exe` | 安装包，装到 `%LOCALAPPDATA%\Programs\Su`，不需要管理员权限 |
| `Su-<版本>-portable.zip` | 免安装版，解压后直接运行，不会自动更新 |
| `Su-Setup.exe`、`Su-Portable.zip` | 同上两个文件，名字里不带版本号，官网的下载按钮用的是它们 |

**macOS**

| 文件 | 说明 |
| --- | --- |
| `Su-<版本>-macos-aarch64.dmg` | Apple Silicon |
| `Su-<版本>-macos-x86_64.dmg` | Intel |
| `Su-macos-aarch64.dmg`、`Su-macos-x86_64.dmg` | 同上，名字里不带版本号 |

**校验与更新**

| 文件 | 说明 |
| --- | --- |
| `*.sha256` | SHA-256 校验值，用来核对下载是否完整 |
| `*.sig` | minisign 签名，自动更新时用来确认安装包没有被改动过 |
| `latest-<平台>.json` | 更新清单：版本号、下载地址、签名和更新说明 |
| `CHANGELOG.md` | 所有版本的更新说明 |

## 自动更新

已安装的素会读取 `latest-<平台>.json`，有新版本时下载安装包，校验签名通过后再安装；签名对不上就不会安装。

Windows 安装包也可以在命令行里用：

```
Su-Setup-<版本>.exe [--dir <路径>] [--desktop] [--silent]
<安装目录>\Su-Uninstall.exe --uninstall [--silent]
```

自动更新就是用 `--silent` 运行安装包。

## 发布流程

源码仓库打 `v*` 标签后，CI 构建并上传各平台的文件。所有平台都上传完之前，这个版本一直是预发布状态，自动更新看不到它。
