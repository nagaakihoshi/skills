# skills

Agent skills for Tessl.

## Setup

### Tessl CLI のインストール

```bash
curl -fsSL https://get.tessl.io | sh
```

## Development Cycle

### 1. 新しいSkillを作成

`tessl skill new` のバグ（skill-first構造が生成されない）が修正されるまでは手動で作成する。

```
skills/<名前>/
├── tile.json
└── SKILL.md
```

**tile.json のテンプレート：**

```json
{
  "name": "nagaakihoshi/<名前>",
  "version": "0.1.0",
  "summary": "<スキルの概要>",
  "private": true,
  "skills": {
    "<名前>": {
      "path": "SKILL.md"
    }
  }
}
```

### 2. SKILL.md に手順を記述

`skills/<名前>/SKILL.md` にSkillの手順・説明を書く。

### 3. ローカルでレビュー・最適化

```bash
TESSL_API_TOKEN=<token> tessl skill review --optimize skills/<名前>
```

CIではCLIの認証ができないため、review・optimize はローカルでのみ実行する。

### 4. PR を作成

PRを作成・更新すると GitHub Actions が自動で実行：

- `tessl skill lint` — フォーマット・構文チェック

### 5. マージ → 自動公開

`main` へのマージで GitHub Actions が `tesslio/publish@main` を実行し、Tessl Registry に公開。

### GitHub Secrets

GitHub リポジトリの Settings > Secrets に以下を追加：

| Secret | 説明 |
|--------|------|
| `TESSL_API_TOKEN` | Tessl の認証トークン（[アカウント設定](https://tessl.io)で生成） |
