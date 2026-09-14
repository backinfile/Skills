# 我的日常 Skills

集中保存、维护和版本管理日常使用的 Codex skills。

## 已收录

| Skill | 用途 | 依赖 |
| --- | --- | --- |
| [grill](skills/grill/SKILL.md) | 通过逐轮追问澄清计划、设计、取舍与验收标准 | 无 |
| [worktree-task](skills/worktree-task/SKILL.md) | 在独立 Git worktree 中完成任务、验证并整合变更 | Git |

## 目录结构

```text
skills/
  grill/
    SKILL.md
    agents/
  worktree-task/
    SKILL.md
    agents/
```

每个 skill 使用独立目录，入口文件为 `SKILL.md`。相关的 `agents/`、脚本、参考资料和资源文件与 skill 一起保存。

## 安装到本机

在仓库根目录运行以下 PowerShell 命令，将尚未安装的 skill 复制到本机 Codex skills 目录。已存在的目录会跳过，避免覆盖本机修改。

```powershell
$skillHome = if ($env:CODEX_HOME) {
    Join-Path $env:CODEX_HOME 'skills'
} else {
    Join-Path $env:USERPROFILE '.codex\skills'
}
New-Item -ItemType Directory -Path $skillHome -Force | Out-Null
Get-ChildItem -LiteralPath '.\skills' -Directory | ForEach-Object {
    $destination = Join-Path $skillHome $_.Name
    if (Test-Path -LiteralPath $destination) {
        Write-Host "跳过已安装的 skill：$($_.Name)"
    } else {
        Copy-Item -LiteralPath $_.FullName -Destination $destination -Recurse
    }
}
```

更新已安装的 skill 前，先比较仓库版本与本机版本并备份需要保留的修改。`grill` 已合并原 `grill-me` 和 `grilling` 的功能，无需额外依赖。

## 维护约定

- 新增 skill 放入 `skills/<skill-name>/`，并更新上面的目录表。
- 保留 `SKILL.md` 中的名称、用途及其引用的依赖文件。
- 不提交密钥、令牌、个人配置或运行产生的临时文件。
- 当前收录内容来自本机已有 skills；如对外发布，应先核对各 skill 的来源和授权。
