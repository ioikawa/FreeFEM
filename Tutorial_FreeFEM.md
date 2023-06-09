# FreeFEM による有限要素法の数値計算
Poisson方程式に対して，FreeFEMで有限要素解を計算するところまでを解説する．

## はじめに

### FreeFEM とは
- FreeFEM（[公式](https://freefem.org/)）は有限要素法の数値計算を行うためのプログラミング言語である．
- FreeFEMはその名の通り，open sourceのフリーソフトウェアである．
- 言語仕様はC++風．以前はFreeFem++という名前だった．
  
- FreeFEMでは偏微分方程式の弱形式を記述し，有限要素空間を設定するだけで有限要素解が得られるので大変便利．C++などの汎用言語で0から有限要素法のプログラムを書くのは，労力と時間がかかる．


### 他の有限要素ソフトウェア
- [FEniCSx](https://fenicsproject.org/)もFreeFEMと同様に有名なフリーな有限要素ソフトウェアである．
- FreeFEMよりも機能豊富であるが，その分コマンドが複雑でありFreeFEMよりも敷居が高い．

## FreeFEMの準備

### インストール
[GitHubのページ](http://github.com/FreeFem/FreeFem-sources/releases) 
からOSにあった最新バージョンのインストーラーをダウンロードして実行する．
例えば，Windowsの場合は \texttt{FreeFEM-4.12-win64.exe}が執筆時点では最新である．

### FreeFEM-cs に関する注意
- FreeFEM-cs (https://www.ljll.math.upmc.fr/lehyaric/ffcs/index.htm) 
というFreeFEM用のIDE(統合開発環境)もかつてはよく利用されていた．IDEはエディタやデバッガなどのプログラムの開発に必要なツール群がひとまとめになったGUIソフトウェアのことである．
- 公式サイトを見た印象ではFreeFEM-csはもはやメンテナンスされていないようなので，FreeFEM-csの使用は非推奨である．少なくとも macOSでは動作しない．Windows 10 では一応動作するようだが，ファイルが保存できない事例があった．

### 実行確認

`コマンドプロンプト` あるいは `PowerShell` を（以下，ターミナルと呼ぶ）を起動する．
- `コマンドプロンプト`はWindowsメニューあるいは検索ボックスからかんたんに見つかる
- 「Windowsキー+R」→「ファイル名を指定して実行」→「cmdと入力してOK押下」で確実に起動できる．

適当なフォルダ（ここでは`fftest`）を作成し，移動する．
```@bash
mkdir fftest
cd fftest
```
適当なテキストエディタを起動する．ここでは「メモ帳」を起動する：
```
 Notepad hello.edp
``` 
以下の内容をコピペして（名前を変更せずに）保存する．
```@bash
cout << "Hello" << endl;
```
（`cout` は「ターミナルの画面」を表す変数というぐらいの認識で問題ない． `cout` に 
`<<` 演算子で文字列や数値，変数を流し込むとターミナルに表示される．
`endl` は改行を意味する．
末尾のセミコロンはプログラムの終端に必ずつける．
このあたりは C++ の書き方と同じである．）

ターミナルに戻って，先程保存したソースファイルを実行しよう．
```@bash
FreeFem++ hello.edp 
```
入力コードなど色々表示されるがその中に `Hello` という文字列が確認できればOKである．

表示内容を抑制するには `-ne` オプションを付けて実行する．
```@bash
FreeFem++ -ne hello.edp 
```

