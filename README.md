# dsh-windows-build

在 GitHub Actions 上构建 deepseek-ai/deepseek-harness 的 Windows x64 安装包。

- 工作流 `build-windows.yml`：checkout 官方 tag（默认 `dsh-v0.2.1-rc.2`）→ 应用 `patches/dsh-build-fixes.patch`（低内存构建、tar --force-local、复用官方安装包中的 NSIS helper DLL，绕过本机/CI 缺少 VS C++ Build Tools 的问题）→ `pnpm run package:desktop:win:x64:unsigned` → 上传 artifact 并发布 Release。
- 产物：`deepseek-harness-<version>-win-x64-unsigned.exe`（NSIS，per-user，无自动更新，仅本地安装用途）。
- 手动触发：Actions → Build Windows installer → Run workflow（可改 source_ref / 是否发布）。
