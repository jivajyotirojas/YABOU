# YABOU

戦国時代の日本を舞台にした戦略ゲーム「戦国の野望」。

| ファイル | 中身 |
|---|---|
| `sengoku_v7.html` | 参照実装（単一 HTML）。ブラウザで開けば遊べる |
| `sengoku_spec.md` | 仕様書 |

## 遊ぶ

https://jivajyotirojas.github.io/YABOU/

`main` に入ると GitHub Actions（`.github/workflows/deploy.yml`）が `gh-pages` ブランチへ出し、そこが公開される。
`index.html` は `sengoku_v7.html` へ飛ばすだけの入口。

## 事前に試す（PR プレビュー）

PR を作ると、その PR の中身だけを載せたページが別の URL に出る（`.github/workflows/preview.yml`）。

- URL は `https://jivajyotirojas.github.io/YABOU/pr-preview/pr-<PR番号>/`。PR にコメントで付く
- PR に push するたびに更新される
- PR を閉じるかマージすると消える

本番を変えずに確かめられるので、遊んで問題なければマージする。

## Issue

不具合・追加の提案・仕様書の直しの3種類の雛形がある。PR の本文に `Closes #番号` と書くと、マージしたときにその Issue が閉じる。

## ライセンス

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ja)（表示 - 非営利 - 継承）。
学術研究や趣味など非営利の範囲なら、使用・改変・再配布してよい。営利目的には使えない。
再配布するときは作者を表示し、同じライセンスで配る。詳しくは `LICENSE` を参照。
