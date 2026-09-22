# gari315-study-suggestions

# study-suggestions

「今の状態(学校/移動中/家)」に応じた勉強タスクの提案候補を管理するリポジトリ。

## 構成

- `context-tasks.json` — 提案候補データ本体。Scriptable側がこれを読みに来る
- `index.html` — このJSONをブラウザから一覧・追加・編集・保存できる管理サイト（GitHub Pages）

## セットアップ

1. このリポジトリを `gari315/study-suggestions` として作成し、3つのファイルをpush
2. リポジトリの Settings → Pages → Source を「Deploy from a branch」、Branch を `main` / `/(root)` に設定
3. 数分後、`https://gari315.github.io/study-suggestions/` で管理サイトが開けるようになる

## トークンの用意

管理サイトから保存するには、書き込み権限を持つ GitHub Personal Access Token が必要です。

1. GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token
2. Repository access は「Only select repositories」→ `study-suggestions` のみを選択
3. Permissions → Contents を **Read and write** に設定
4. 生成されたトークンを管理サイトの入力欄に貼り付ける（そのブラウザの localStorage にのみ保存され、リポジトリには含まれない）

トークンは第三者に見られると誰でもこのリポジトリを書き換えられてしまうので、他人と共有した端末には保存しないでください。

## Scriptable側の対応

`context-record.js` は `context-remote.js` 経由でこのリポジトリの `context-tasks.json` を毎回取得します。
取得に失敗した場合は、iPhone内に保存された前回取得分のキャッシュを使って動作を継続します。
