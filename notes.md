
# Windows環境

## テキストエディタ

### 起動方法
- メモ帳：Windowsキー>検索窓で `notepad`とタイプ> Enter 

### 保存
 - `Ctrl+S`: 保存
 - `Ctrl+Shift+S` : 名前を付けて保存
   
## コマンドプロンプト

### 起動方法
- Windowsキー>検索窓で`cmd` とタイプ>Enter で起動します．

### コマンド
- `dir`: カレントフォルダのファイル一覧表示
- `cd foo`: フォルダ `foo` への移動
- `where foo`: プログラム `foo`の位置を表示


## FreeFEM起動時のエラー

### FreeFEM本体にパスが通っていない場合
- FreeFEMは普通にインストールするとプログラム本体などへのパスが通るように設定されます．
もし，コマンドプロンプトで 
```
FreeFem++
```
と実行して，`プログラムまたはバッチファイルとして認識されていません`というようなメッセージが表示された
場合はパスが通っていません．

FreeFEMのプログラム本体は通常は `C:\Program Files (x86)\FreeFem++` です．

コマンドプロンプトで 次を実行するとパスの設定が表示されます（[learning.microsoft.com](https://learn.microsoft.com/ja-jp/windows-server/administration/windows-commands/path)）
```
path
```
この中に `C:\Program Files (x86)\FreeFem++` が含まれていなければパスが通っていないことになります．

この場合，自力でパスを通すか，本体をフルパスで書いて起動することになります．

### パスを通す方法
```
path %PATH%;C:\Program Files (x64)\FreeFem++
```

### フルパスで実行する方法
コマンドプロンプトで確認する方法：
```
where FreeFem++
```

例えば `foo.edp`を実行する場合，次のように本体をフルパスで書いてください．
```
C:\Program Files (x86)\FreeFem++ foo.edp
```
これで実行されるはずです．

### `ffglut.exe`にパスが通っていない場合
自力でパスを通すのが最も良い方法ですが，パスを通せない場合は，
`C:\Program Files (x86)\FreeFem++` をカレントフォルダにして実行する方法が有効かもしれません（未確認）．

## FreeFEM実行時のエラー

## Syntax Error
例えば，`syntax error` と書いてあれば，コードの文法上の誤りからエラーが発生しています．
大抵の場合は単純なミスが原因です．

よくある単純な syntax errorの例：
- カッコの閉じ忘れ
- 行末のセミコロン `;` の入力し忘れ
- ミスタイプによる余計な文字列の混入

## Segmentation Fault
- 通常はアクセスできないメモリを参照しようとしたときに発生するエラーです．
- 例えば，範囲外の配列にアクセスしようとしたときに発生します．

## FreeFem++-js
- インストールがどうしても上手く行かない人は，オンライン（ブラウザ）上で実行できる[FreeFem++-js](https://www.ljll.math.upmc.fr/lehyaric/ffjs/portable.htm)を使うという手段もあります．
- 常時使用可能かどうかはわからないので，自分の端末にインストールすることを第一に推奨します．
