# Branch Strategy for Moto360-Embedded

主要分支：
- main
  - 用途：对外发布、展示、稳定版本（always deployable）
  - 保护：开启 branch protection（require PR review、CI pass）

- dev
  - 用途：日常集成分支，所有 feature 合并到 dev 进行测试
  - 流程：feature -> PR -> dev -> 测试通过 -> PR 合并到 main

- feature/*
  - 命名规则：feature/<短描述>（如 feature/ui-login）
  - 用途：开发单个功能，完成后发 PR 到 dev

PR 流程：
1. 在本地创建 feature 分支：`git checkout -b feature/<name>`
2. 完成开发并提交：`git commit -m "feat: ..."`
3. 推送：`git push -u origin feature/<name>`
4. 在 GitHub 上打开 Pull Request 到 dev，至少 1 次代码审查通过，CI 通过后合并。

保护规则建议（在仓库 Settings -> Branches）：
- 对 main：Require pull request reviews (至少 1)、Require status checks (CI)、Require signed commits（可选）
- 对 dev：可设置较宽松但建议保留 PR 审核流程
