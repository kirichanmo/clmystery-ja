# コマンドラインチートシート

CLMysteryを解くために必要なコマンドをまとめました。

> 本チートシートは [veltman/clmystery](https://github.com/veltman/clmystery/blob/master/cheatsheet.md) を参考に日本語化・追加したものです。
> 原著: Noah Veltman (MIT License)

---

## ターミナルを開く

| OS | 方法 |
|----|------|
| Mac | `アプリケーション` → `ユーティリティ` → `ターミナル` |
| Windows | Git Bashをインストールして使用 |
| Linux | Ctrl + Alt + T |

---

## ディレクトリ操作

### `pwd` - 現在地を確認
```bash
pwd
```
今いるディレクトリのパスを表示します。

### `ls` - ファイル一覧を表示
```bash
ls              # 現在のディレクトリ
ls mystery/     # 指定したディレクトリ
ls -la          # 隠しファイルも含めて詳細表示
```

### `cd` - ディレクトリを移動
```bash
cd mystery/logs    # 指定したディレクトリへ移動
cd ..              # 一つ上のディレクトリへ
cd                 # ホームディレクトリへ
```

---

## ファイルを読む

### `cat` - ファイル全体を表示
```bash
cat filename.txt
cat file1.txt file2.txt    # 複数ファイルを連結して表示
```

### `head` - ファイルの先頭を表示
```bash
head filename.txt          # 先頭10行
head -n 20 filename.txt    # 先頭20行
```

### `tail` - ファイルの末尾を表示
```bash
tail filename.txt          # 末尾10行
tail -n 20 filename.txt    # 末尾20行
```

### `less` - スクロールしながら読む
```bash
less filename.txt
```
- `スペース` で次のページ
- `b` で前のページ
- `q` で終了
- `/検索語` で検索

---

## 検索する

### `grep` - テキストを検索
```bash
grep "検索語" filename.txt           # ファイル内を検索
grep "検索語" *.txt                  # 複数ファイルを検索
grep -i "検索語" filename.txt        # 大文字小文字を区別しない
grep -r "検索語" directory/          # ディレクトリ内を再帰的に検索
grep -c "検索語" filename.txt        # マッチした行数を表示
```

---

## 比較する

### `diff` - ファイルの差分を表示
```bash
diff file1.txt file2.txt
```
2つのファイルの違いを表示します。証言とログの矛盾を見つけるのに便利です。

出力の読み方:
- `<` は1つ目のファイルにのみある行
- `>` は2つ目のファイルにのみある行
- `1c1` は「1行目が変更されている」という意味

---

## パイプとリダイレクト

### `|` - パイプ（コマンドをつなげる）
```bash
cat filename.txt | grep "検索語"     # ファイルの中身を検索
grep "ERROR" *.log | head -n 5       # 検索結果の先頭5件だけ表示
```

### `>` / `>>` - 出力をファイルに保存
```bash
grep "検索語" file.txt > result.txt    # 上書き保存
grep "検索語" file.txt >> result.txt   # 追記
```

---

## ワイルドカード

```bash
ls *.txt           # .txtで終わるファイル全て
cat log_*.txt      # log_で始まるtxtファイル全て
grep "ERROR" *     # 全ファイルから検索
```

---

## 行数を数える

### `wc` - 行数・単語数・文字数をカウント
```bash
wc filename.txt         # 行数、単語数、文字数
wc -l filename.txt      # 行数だけ
grep "ERROR" *.log | wc -l   # マッチした行数を数える
```

---

## Tips

- **Tab補完**: ファイル名やディレクトリ名を途中まで入力してTabキーを押すと補完されます
- **履歴**: 上下の矢印キーで過去に入力したコマンドを呼び出せます
- **中断**: Ctrl + C でコマンドを中断できます
- **クリア**: `clear` でターミナルの表示をクリアできます
