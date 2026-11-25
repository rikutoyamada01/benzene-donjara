# 運用ルール（CONTRIBUTING）

このリポジトリ（`benzene-donjara`）でチーム開発を進めるための最小限のルールです。  
Git / GitHub の一般的な仕組みは各参考リンクに任せ、ここでは**「このリポジトリでなぜそのルールにするのか」**だけをまとめています。

---

## 1. ブランチ運用（GitHub Flow）

* `main` ブランチには直接 `push` せず、作業ごとにブランチを作って **Pull Request（PR）** 経由でマージします。
* 参考: [GitHub Docs — GitHub フロー](https://docs.github.com/ja/get-started/using-github/github-flow)

**なぜこのリポジトリでそうするのか**
* 学校公開のデモ用リポジトリなので、`main` を常に「そのまま開いて動く状態」に保つためです。
* ブランチ体系が複雑な Git Flow ではなく、GitHubに慣れていないメンバーでも迷わず回せる一番シンプルな運用を選んでいます。

---

## 2. ブランチの命名規則

`<種類>/<Issue番号>-<短い内容>`（英小文字・ハイフン区切り）にします。Issueがない作業は番号を省略して構いません。

| 接頭辞（種類） | 用途 | 例 |
| :--- | :--- | :--- |
| `feat/` | 新機能の追加・UI追加 | `feat/4-title-screen` |
| `fix/` | バグ修正・表示崩れ修正 | `fix/6-turn-minus-bug` |
| `docs/` | ドキュメント・仕様書の追加や更新 | `docs/ui-spec` |
| `refactor/` | 動作を変えないコード整理 | `refactor/split-js` |

* 参考: [GitHub Docs — ブランチについて](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)

**なぜこのリポジトリでそうするのか**
* 個人名だけのブランチだと「何の作業中か」「他メンバーの作業と被っていないか」「マージ後に消していいか」が分からなくなるためです。
* Issue番号を入れることで、どの課題に対応したブランチか一目で追えます。

---

## 3. コミットメッセージの規則

`<種類>: <変更内容（日本語OK）>` の形式にします。

* 例: `fix: パス連打で残りターンが-1になるバグを修正`
* 例: `feat: タイトル画面を追加`
* 例: `docs: スコア計算式の仕様書を作成`
* 種類はブランチと同じ `feat` / `fix` / `docs` / `refactor` / `chore`（雑務・設定）を使います。
* 参考: [Conventional Commits（日本語）](https://www.conventionalcommits.org/ja/v1.0.0/)

**なぜこのリポジトリでそうするのか**
* 英語必須にすると作業のハードルが上がるため本文は日本語OKにしつつ、先頭のラベルだけ揃えることで「いつ・何の修正が入ったか」を履歴からすぐ探せるようにするためです。

---

## 4. Issue と Pull Request（PR）の進め方

1. **Issue**: 思いついた改善案やバグは気軽に Issue に書きます。仕様が曖昧なものは、実装前にコメントで認識を合わせてから着手します。
2. **PR**: 本文に `Closes #番号`（例：`Closes #6`）を書き、**見た目の変更がある場合はスクリーンショットを1枚貼ります**。
3. マージ後は不要になった作業ブランチを削除します（GitHub上の「Delete branch」ボタン）。
* 参考: [GitHub Docs — プルリクエストを Issue にリンクする](https://docs.github.com/ja/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue)

**なぜこのリポジトリでそうするのか**
* ゲームUIや演出の変更はコードの差分だけでは分かりにくいため、スクショを貼ることでコードに不慣れなメンバーでもレビュー・意見出しをしやすくするためです。
* `Closes #番号` を書くことで、マージと同時に Issue が自動で閉じられ、管理の手間が減ります。

---

## 5. ドキュメント作成の方法と配置ルール

* 形式は **Markdown（`.md`）** で作成し、用途ごとに配置場所を分けます。
  * `README.md`: プロジェクト概要・動かし方（入口）
  * `CONTRIBUTING.md`: この運用ルール
  * `docs/<テーマ>.md`: 仕様書・設計メモ（例: `docs/score-formula.md`, `docs/ui-design.md`）
* 1ファイル1テーマとし、決定事項だけでなく「なぜそう決めたか」も軽く残します。
* 参考: [GitHub Docs — Markdown の基本的な書き方](https://docs.github.com/ja/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

**なぜこのリポジトリでそうするのか**
* ルートフォルダにメモファイルが散らばるのを防ぎ、GitHub上でそのまま綺麗に閲覧・差分管理ができるためです。
* スコアの定式化やUI設計の「理由」を残しておくと、学校公開のポスター発表やゼミ発表の資料にもそのまま流用できます。

---

## 6. ファイル・コードの命名規則

* **ファイル・フォルダ名**: 英小文字＋ハイフン（`kebab-case`、例: `score-formula.md`, `molecule-sim.js`）。日本語や半角スペースは使わない。
* **HTML / CSS の ID・クラス名**: 英小文字＋ハイフン（例: `title-screen`, `btn-settings`）。
* **JavaScript の変数・関数名**: `camelCase`（例: `selectVertex`）、定数は `UPPER_SNAKE_CASE`（例: `MAX_TURNS`）。
* 参考: [MDN — ファイルの扱い方（命名の注意点）](https://developer.mozilla.org/ja/docs/Learn_web_development/Getting_started/Environment_setup/Dealing_with_files)

**なぜこのリポジトリでそうするのか**
* メンバー間で Windows / Mac が混在したり、GitHub Pages（Linux）で公開した際に、大文字・小文字の違いや日本語ファイル名によるリンク切れ・文字化けを防ぐためです。
* Web標準の命名に合わせておくと、今後ファイルを分割したり Joy-Con（WebHID）機能を追加する際も混乱せずに済みます。

---

## 7. 通知とコミュニケーションの設定

* **全員の初期設定**:
  1. リポジトリ右上の **`Watch`** → **`All Activity`** を選択する。
  2. **GitHub 公式スマホアプリ**（iOS / Android）のプッシュ通知を ON にする（または [通知設定](https://github.com/settings/notifications) でメール通知を有効にする）。
* **コメント時のルール**: 特定のメンバーに確認してほしい時は **`@ユーザー名`** でメンションする。PR作成時は右サイドバーの `Reviewers` に確認者を指定する。
* 参考: [GitHub Docs — 通知を設定する](https://docs.github.com/ja/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications)

**なぜこのリポジトリでそうするのか**
* LINE など外部チャットに議論が分散するのを防ぎ、すべてのやり取りを Issue / PR に集約して「いつ・何を決めたか」を後から追えるようにするためです。
* 初期設定のままだと他メンバーの新規 Issue やコメントに気づけないため、`All Activity`＋プッシュ通知にして見逃しを防ぎます。

