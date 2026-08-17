# Su-Releases

素（Su）的发布页 —— 只放安装包，不放源码。

每个 release 有四个文件：

| 文件 | 是什么 |
| --- | --- |
| `Su-Setup-<版本>.exe` | Windows 安装包，编辑器打包在里面。装到 `%LOCALAPPDATA%\Programs\Su`（或已有的安装目录），不需要管理员 |
| `Su-Setup-<版本>.exe.sig` | minisign 签名。编辑器自动更新时校验它，签名不对就不安装 |
| `Su-Setup-<版本>.exe.sha256` | 手工核对下载用 |
| `latest-windows-x86_64.json` | 更新清单。已安装的 素 在「关于」页里读 `releases/latest/download/latest-windows-x86_64.json` |

安装包的命令行参数：

```
Su-Setup-<版本>.exe [--dir <路径>] [--desktop] [--silent]
<安装目录>\Su-Uninstall.exe --uninstall [--silent]
```

自动更新走的就是 `--silent`：安装包把正在运行的 `Su.exe` 改名挪开，把新的写在旁边，所以更新和安装是同一条路径。

发布由源码仓库里 `v*` tag 触发的 CI 上传，资产齐全后才从 prerelease 转正 —— 中途失败的发布不会被更新器看见。
