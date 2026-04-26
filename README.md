# cicd-demo

学习 GitHub Actions CI/CD 的最小 demo。

## 本地跑

```bash
uv sync --extra dev
uv run pytest
uv run ruff check .
```

## CI 做了啥

每次 push 到 `main` 或开 PR 时，`.github/workflows/ci.yml` 会自动：

1. 在 Ubuntu 上分别用 Python 3.12 和 3.13 各跑一遍（matrix 并行）
2. 装依赖
3. 跑 ruff 检查代码风格
4. 跑 pytest 跑单元测试

任何一步失败 → PR 显示红 ❌；全部通过 → 绿 ✅。

## 学习路径

1. 改 `src/calc/__init__.py` 加个 `mul` 函数
2. 在 `tests/test_calc.py` 加测试
3. commit + push，去 Actions 标签页看 CI 跑
4. 故意把测试写错，看红 ❌ 长啥样
5. 试着加一个 "tag 触发自动发 release" 的 workflow（进阶）
