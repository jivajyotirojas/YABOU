# YABOU

戦国時代の日本を舞台にした戦略ゲーム「戦国の野望」。

| ファイル | 中身 |
|---|---|
| `sengoku.html` | 参照実装（単一 HTML）。ブラウザで開けば遊べる |
| `sengoku_spec.md` | 仕様書 |

## 遊ぶ

https://jivajyotirojas.github.io/YABOU/

`main` に入ると GitHub Actions（`.github/workflows/deploy.yml`）が `gh-pages` ブランチへ出し、そこが公開される。
`index.html` は `sengoku.html` へ飛ばすだけの入口。

## 動作環境（WebGL2）

地図は WebGL2 で描く。ブラウザが WebGL2 を使えないと、起動しても地図が出ず、
下端に「この環境では地図を描けません（WebGL2 が使えません）」と出る（保存・読込は動く）。

- 使えるブラウザ：Chrome・Edge（56 以降）、Firefox（51 以降）、Safari（15 以降）。
  いずれも最近の版なら、ふつうは何もしなくてよい
- ファイルを手元に保存して直接開いてもよい（`file://` で動く）。
  チャットやメールのアプリの中のプレビューでは WebGL が使えないことが多いので、ブラウザで開く

それでも出ないときは、ブラウザ側で WebGL が止められている。確かめ方と直し方は次のとおり。

| ブラウザ | 確かめる所 | 直し方 |
|---|---|---|
| Chrome | アドレス欄に `chrome://gpu`。「WebGL2」の行が Hardware accelerated なら使える | 設定 → システム →「グラフィック アクセラレーションが使用可能な場合は使用する」を入にして再起動。GPU が遮断一覧に入っていて Software only・Disabled のときは `chrome://flags/#ignore-gpu-blocklist` を Enabled にする |
| Edge | `edge://gpu`。見方は Chrome と同じ | 設定 → システムとパフォーマンス →「利用可能な場合はグラフィックス アクセラレータを使用する」を入にして再起動。遮断されているときは `edge://flags/#ignore-gpu-blocklist` を Enabled |
| Firefox | `about:support` →「グラフィック」の「WebGL 2 ドライバー レンダラー」。失敗・blocked と出ていれば止められている | `about:config` で `webgl.disabled` を `false`、`webgl.force-enabled` を `true` にして再起動。ほかの `webgl.*` は触らない |
| Safari | 15 以降は最初から使える | 14 以前は メニュー「開発」→「実験的な機能」→「WebGL 2.0」を入にする（「開発」メニューは 設定 → 詳細 → 「メニューバーに"開発"メニューを表示」で出す） |

企業や学校の端末では、設定で WebGL が切られていて上の操作ができないことがある。その場合は管理者に相談する。

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

版は `sengoku.html` の `VERSION`（`主版.副版.修正`。仕様書 §1.7）で、画面の右上・読み込み画面・タブ名に出る。
`main` の `sengoku.html` が変わると GitHub Actions（`.github/workflows/release.yml`）が、その版の印（`v8.2.3` のようなタグ）を付け、
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
