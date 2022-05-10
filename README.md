# データ解析のためのvscode-R環境

## 初期設定

*univ_dataAnalysis_env* がクローンなりzip→展開なりでローカルに存在していて、カレントディレクトリになってる前提
### 拡張機能まわり

1. ワークスペースの推奨拡張機能"R"をインストール
2. [windowsの場合のみ] *./.vscode/settings.json* の *r.rterm.windows* にRのパスを記入

### rMarkdownまわり

3. *./.vscode/report.code-snippets* の *[YOUR_STUDENT_ID]* と *[YOUR_FULL_NAME]* を自分の学籍番号とフルネームに書き換える
4. ユーザーの *keybindings.json* に
```json
	{
		"description": "render docx",
		"key": "ctrl+i",
		"command": "r.runCommandWithEditorPath",
		"when": "editorTextFocus",
		"args": "rmarkdown::render(\"$$\", output_dir = \".\", clean = TRUE)"
	}
```
を追記  
※ *keybindings.json* は *cmd(ctrl)+shift+P* を押して *key* って入力すると出てくる *Preferences: Open Keyboard Shortcuts (JSON)* っていうのを選択すれば開ける  
5. 出力するレポートのテンプレートとなるwordファイルを *report-style.docx* という名前で作成し、*./templates/report-style* と置き換え(第3回講義の教材倉庫にあったはず)

## 使い方
### 拡張機能
拡張機能の作者さんのQiita  
https://qiita.com/Ikuyadeu/items/edf1ddc733f4d1770d5a  
https://qiita.com/Ikuyadeu/items/ac8f0852a953829151dd  
見るなりググるなりで

ほとんどRstudioと同じ使用感で使えるのでそこまで躓きそうな部分はないかな
### スクリプト/レポート作成
ワークスペース直下に *part1* みたいな感じで授業ごとのディレクトリ作って、その中に *.R* と *.Rmd* 形式でスクリプト/レポートを作成
(例としてpart0ディレクトリ作ってあるのでそれ参照)

ファイル内で *init* って打ってTAB押すと *.Rmd* のファイル頭に必要なyamlを挿入してくれるので便利

*.Rmd* 形式のファイル内で *ctrl+i* を押すとワークスペース直下に *.docx* ファイルとして出力してくれる(*ctrl+i* のショートカットが他のショートカットと競合してる場合は別の組み合わせに変更することを推奨)