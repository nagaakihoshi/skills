# Zenn Markdown Reference

## Zenn-specific syntax

### Callout boxes

```
:::message
メモや補足情報
:::

:::message alert
警告・注意事項
:::
```

### Collapsible section

```
:::details タイトル
折りたたまれる内容
:::
```

### Code block with filename

````
```js:filename.js
const x = 1;
```
````

### Inline code diff

```diff js
- const x = 1;
+ const x = 2;
```

## Setup prerequisites

Before using zenn-cli, verify:

- **Node.js** — `node -v`. If missing, install from https://nodejs.org
- **zenn-cli** — `npx zenn --version`. If missing:
  ```bash
  npm install zenn-cli
  npx zenn init
  ```
- **GitHub integration** — repository must be connected at https://zenn.dev/dashboard/deploys

## Common issues

| Problem | Solution |
|---|---|
| プレビューで画像が表示されない | `images/` ディレクトリに置き、`/images/filename.png` で参照 |
| スラッグが重複エラー | ファイル名（スラッグ）を変更する |
| トピックが反映されない | Zenn上の正式なトピック名（小文字）を使う |
| GitHub pushしても反映されない | `published: true` になっているか、連携リポジトリへ pushしているか確認 |
