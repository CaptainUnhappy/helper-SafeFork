# helper-SafeFork

[Prometheus-first/helper](https://github.com/Prometheus-first/helper) 的公开 SafeFork，保留 Git 分支、标签与提交历史。上游旧地址为 `Prometheus-first/wx-helper`。

- [main 历史归档](https://github.com/CaptainUnhappy/helper-SafeFork/tree/main) 固定保留旧历史 `a127ec91989de2eb12e5cc104ff991e94895ee03`，不再接收自动同步。
- [upstream-main 跟踪分支](https://github.com/CaptainUnhappy/helper-SafeFork/tree/upstream-main) 跟踪上游 `main` 的新历史。显式映射为 `SAFEFORK_BRANCH_MAP=main upstream-main`；建立后只允许快进，不合并或覆盖归档。
- 默认分支 `sync-control` 只保存同步工作流与说明。每小时第 17 分钟检查上游；GitHub 定时调度可能延迟或跳过，实际结果见 [Actions](https://github.com/CaptainUnhappy/helper-SafeFork/actions/workflows/safe-fork-sync.yml)。
- 只新增分支、标签或快进分支；不创建 merge commit、不强推、不删除已有引用。上游消失、再次回退/重写或出现未审核标签冲突时停止，保留已有数据。
- 采用 SafeFork `2026-10-17.1` 的 `public-fork` 模式，写入只使用任务临时 `GITHUB_TOKEN`，不需要额外 PAT、Deploy Key 或 Secret。

`SAFEFORK_PAUSED=true` 只暂停定时任务，手动运行仍可验收。`dry_run` 只检查、不写入。除 Safe Fork Sync 外，不启用继承的构建或发布工作流。

两个代码分支位于同一仓库，不是独立离线备份。标签是仓库级引用，不因分支分开而允许覆盖。Git LFS 对象、子模块仓库内容、Releases 附件、Issues、PR 与其他 GitHub 元数据不在同步范围内。同步不改变上游及第三方内容的许可；公开 Fork 也不构成永久保存保证。
