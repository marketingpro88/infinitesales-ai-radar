# InfiniteSales AI Radar

竞对爆款雷达 —— 每周自动抓竞对 IG 爆款，转口播稿，AI 拆解 Hook / 结构 / 改编角度，生成网页 dashboard。

## 每周流程（全自动，GitHub Actions 云端跑）

```
周日 08:00 (GMT+8)
  Viral Content Sync   Apify 抓 IG 爆款 → 存 Airtable
        ↓
  Transcribe Videos    Whisper 转口播逐字稿（免费）
        ↓
  Analyze Posts        GitHub Models AI 拆解（免费）
        ↓
  Build Dashboard      生成 docs/index.html → GitHub Pages
```

任一环节失败，后面就不会跑 —— 网页没更新时先去 Actions 看哪一环断了。

## 怎么用

- **看雷达**：见仓库 Settings → Pages 的网址
- **加/换竞对**：去 Airtable 的 `Competitors` 表加一行，勾 Active，下周自动生效
- **手动跑**：Actions → Viral Content Sync → Run workflow

## 费用

Apify 约 $5/月。转录、AI 拆解、网页托管全免费。

## 抓取门槛

`ig_content_sync.py` 里的 `MIN_ER = 0.03`（互动率 3%）、`MIN_COMMENTS = 50`。
抓到 0 条时看 sync log 的 `Below threshold` 计数，小账号偏高就调低。
