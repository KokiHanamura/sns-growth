# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# sns-growth

SNS 運用アカウントを立ち上げ、フォロワー・エンゲージメントを伸ばすプロジェクト。
ハーネス構成は `~/Introduction` をテンプレート元とする。

## Scope

- 対象プラットフォーム: X / Instagram / TikTok / YouTube Shorts
- ジャンル: **未定** — Phase 0 のリサーチで決定し `strategy/positioning.md` に記録する

## Phases

| Phase | 目的 | 主な成果物 |
|-------|------|-----------|
| 0. リサーチ | ジャンル選定・競合調査 | `strategy/research.md`, `strategy/positioning.md` |
| 1. 立ち上げ | アカウント作成・プロフィール整備 | `accounts/<platform>.md` |
| 2. 初期運用 | 投稿の型を作り、毎日投稿を回す | `content/`, `strategy/content_pillars.md` |
| 3. 改善 | 数値計測 → 仮説 → 検証のループ | `analytics/` |

## Architecture

```
sns-growth/
  .claude/                  # ハーネス設定（Introduction から継承）
  strategy/                 # ジャンル・ペルソナ・KPI・投稿方針
  accounts/                 # プラットフォーム別のプロフィール設定・運用ルール
  content/
    ideas/                  # ネタ帳
    drafts/                 # 下書き（1投稿1ファイル、frontmatter に platform/status）
    published/              # 投稿済み（投稿URL・日時を追記して移動）
  analytics/
    snapshots/              # 週次の数値スナップショット（CSV/MD）
    reports/                # 週次・月次振り返り
  docs/plans/               # 日次作業フォルダ
  scripts/
```

## Rules

- **アカウント作成・ログイン・投稿の実行は人間が行う**（Claude は下書き・分析・計画まで）
- API キー・パスワードは `.env` に置き、絶対にコミットしない
- 数値の記録は `analytics/snapshots/YYYYMMDD.md` に週1回
- 下書きの frontmatter: `platform`, `pillar`, `status: idea|draft|ready|published`, `hook`

## Workflow

- セッション開始: `python3 scripts/create_daily_plan.py "<作業内容>"`
- `ai_todo.md` は Claude のみ編集（Humans: read-only）
- コミット: 変更の意図（why）を中心に記述
