# humanizer-vi

A Claude skill that rewrites Vietnamese text so it reads like a real person wrote it: it removes the tells of AI-generated and machine-translated writing (sáo ngữ, văn dịch, lạm dụng từ Hán Việt, từ nối dày đặc, "Hy vọng bài viết hữu ích"...).

See [SKILL.md](SKILL.md) for the full list of patterns and examples.

## Install

**Claude Code**

```bash
git clone https://github.com/VAGaming/humanizer-vi ~/.claude/skills/humanizer-vi
```

**claude.ai:** zip this folder and upload it under Settings → Capabilities → Skills.

## Use

> Viết lại đoạn này cho tự nhiên, bớt giọng AI: ...

or ask "Đoạn này có giống AI viết không?" to get a check without a rewrite.
