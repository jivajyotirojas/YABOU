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

決めきれていない決まり・データ・描画の件は、`question` の札を付けた Issue にして、
マイルストーン「[8.3 決めごとの整理](https://github.com/jivajyotirojas/YABOU/milestone/1)」にまとめてある（`QUESTIONS.md` に一覧）。
決まったら仕様書かコードを直し、その PR で閉じる。

## 版とリリース

版は `sengoku_v7.html` の `VERSION`（`主版.副版.修正`。仕様書 §1.7）で、画面の右上・読み込み画面・タブ名に出る。
`main` の `sengoku_v7.html` が変わると GitHub Actions（`.github/workflows/release.yml`）が、その版の印（`v8.2.3` のようなタグ）を付け、
前の版からの PR をまとめた [Releases](https://github.com/jivajyotirojas/YABOU/releases) を作る。
過去の版に印を付けるときは、Actions の「Release」を手で動かして版とコミットを指定する。

## 流れ

1. 直したいことを Issue にする（既にあれば番号を控える）
2. `main` から枝を切り、直して、`VERSION` を上げ、仕様書も直す
3. PR を作る。プレビューの URL で遊んで確かめる。本文に `Closes #番号`
4. マージすると、公開ページ・リリース・Issue の閉じが全部自動で進む

## ライセンス

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ja)（表示 - 非営利 - 継承）。
学術研究や趣味など非営利の範囲なら、使用・改変・再配布してよい。営利目的には使えない。
再配布するときは作者を表示し、同じライセンスで配る。詳しくは `LICENSE` を参照。
