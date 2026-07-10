# 大謝名区自治会サイト 引き継ぎメモ

最終更新: 2026-07-10

## プロジェクト概要
沖縄県宜野湾市・大謝名区自治会の公式サイト。眞志喜徹也さん(絵描き)が運営。
元は3.7MBの単一HTML(画像がBase64埋め込み)だったものを、画像を外部ファイル化して軽量化した。

## 公開情報
- リポジトリ: https://github.com/tetsuyamashiki/ojana-jichikai
- 公開URL: https://tetsuyamashiki.github.io/ojana-jichikai/ (GitHub Pages, mainブランチ)
- Google Search Console: 登録・所有権確認・インデックス登録リクエスト済み(2026-07-10)
  - 確認ファイル `googlea8d5873df68729b9.html` は削除しないこと

## ファイル構成(Desktop/claude)
- `index.html` — 公開用メインページ(SEO用metaタグ・構造化データ入り)
- `ojajna_map.html` — 自治会範囲マップ(Leaflet使用)。indexの「自治会加入のご案内」からリンク
- `images/` — 画像。image1〜10は元HTMLから抽出、image11.JPG(祭り観客・トップ背景)、image4.5.png(キャラクター透過版)
- `ojana_jichikai_23_skeleton.html` — 作業用の旧ファイル(公開対象外)
- `googlea8d5873df68729b9.html` — Search Console確認用(公開に含める)

## これまでの主な修正
- SKIPボタンを画面中央上部に配置
- イントロ/トップの文言を「大謝名アイデンティティ、アップデート中…」に変更
- トップ背景をimage11.JPGに変更。170%ズーム・位置62% 68%(中央の少年を強調)・opacity 0.55・brightness 1.25
- キャラクター画像をimage4.5.png(透過PNG)に統一
- 役員欄は自治会長のみ(書記は削除済み)
- スマホ表示時、トップページのヒーロー写真が縦長になりすぎる問題を修正(#homeのpadding調整)
- スマホ表示時、「大謝名区自治会」のタイトルが改行してしまう問題を修正
  (キャラクター画像とタイトルを縦積みに変更、white-space:nowrap、フォントサイズをclampで調整)
- スマホ表示時、ヒーロー写真の被写体(男の子)が中心に来るよう #home::before の
  background-size/background-positionを調整(暫定値、実機確認しながら微調整が必要)
- スマホ表示時にインスタ・noteのボタンが消えていた問題を修正。
  アイコン+短縮ラベル(IG/note)のピル型ボタンとして常時表示に変更

## 更新の流れ(ユーザーの好みのやり方)
1. Claudeがindex.html等をフォルダ内で直接編集
2. ユーザーがMacのターミナルで実行:
   ```
   cd ~/Desktop/claude
   git add <ファイル>
   git commit -m "変更内容"
   git push
   ```
3. 大きな更新時はSearch Consoleで「URL検査→インデックス登録をリクエスト」

## 技術メモ(Claude向け)
- このフォルダはbashサンドボックスにマウントできない → Read/Write/Edit/Glob(ホストパス)を使う
- バイナリ(画像等)はClaudeから直接書き込めない。画像はユーザーがimagesフォルダに追加する運用
- 画像追加時は拡張子の大文字小文字に注意(例: image11.JPG)

## 未対応・今後の予定
- 画像を追加しながら随時修正予定
- Instagram・noteのプロフィールにサイトURL掲載(SEO対策、ユーザー作業)
- スマホでのヒーロー写真の被写体位置(background-position)は暫定値のため、
  実機で確認しながら追加調整が必要

## 作業ログ

### 2026-07-10
- 自治会だより・4コマ・ポスターの過去データを「自治会だより他」フォルダに追加し、種類ごとに整理済み
- 今後の対応: 現在の4コマ漫画セクションを「自治会だより」セクションへ統合・拡張する予定。号ごとにだよりと4コマを対応させて見せる構成を検討中
- 実装前にまず構成案(表示方法:タブ切り替え/スクロール/ページめくり風など)をすり合わせてから着手する
