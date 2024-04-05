# セットアップ（自宅環境）

- [はじめに](#はじめに)
- [VS Code インストール](#vs-code-インストール)
- [gcc インストール](#gcc-インストール)
- [VS Code の設定](#vs-code-の設定)

## はじめに

自宅の PC などに C/C++ 環境を設定したい人むけの文章です。

環境構築には最低限以下のものが必要になります。
- テキストエディタ
- C言語コンパイラ

ここでは、テキストエディタとして**Visual Studio Code（VS Code）**、
C言語コンパイラとして**gcc**を使えるようにします。

## VS Code インストール
Windows でも Mac でも、Visual Studio Code 本体のインストールは簡単です。
拾ってきて実行もしくは配置するだけです。

ただ、標準で C/C++ 環境などが入っているわけではないので、少し事前準備が必要です。

## gcc インストール
OSによって方法が変わります。

### Windows

まずは、gcc/g++ および gdb の手配をします。

* 方法1: mingw を利用

[mingw](http://www.mingw.org/) から download link をたどって、installer をダウンロードしてください。
実行すると、しばらくしてから、入れるパッケージを選択することになると思います。gcc, gdb を選んでください。
Basic Setup の mingw32-base-bin, mingw32-gcc-g++-bin を選べばいいでしょう（必要なものも同時に選ばれます）。Apply Change でインストール開始です。

あと、追加で、git のインストールもおこないましょう。
これは、[git for windows](https://gitforwindows.org/) をインストールすればいいかと思います。

自動で生成される launch, tasks は加筆が必要かもしれないので、標準設定ならこちら([launch.json](win/launch.json), [tasks.json](win/tasks.json))をもっていってください。

`トラブルシュート`

* VS code の挙動が変だという場合は、まず、新規ウィンドウで新規フォルダを開いて、hello.c でも作成してみてください。
* それでも、VS code が正しく動かない場合は、設定ファイルを削除してみましょう。下記 directory を削除してみてください。
  * `C:\Users\YourName\.vscode`: この directory 以下に extension などが配置されます。
  * `C:\Users\YourName\AppData/Roaming/Code/`: こちらにユーザ設定などが保存されているようです。

* 方法2: WSL を利用

WSL つかいの人は、[Remote-WSL extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) を使うほうが楽かと思います。extension から簡単にインストール可能です。
gcc, gdb などは、WSL 側で apt などでインストールすることになります。
gcc, gdb の認識は VS code が自動で認識してくれるかと。

Linux に慣れていない人にはお勧めしませんが、これを機会に使ってみたい人はどうぞ。

`注意事項`: 新しい VScode の Window を開く際は、コマンドパレットから `Remote-WSL: New Window` を選択します。Remote-WSL では、Window 下側が **紫色** です。あとは、WSL の世界でファイルを選択・実行することになります。


### Mac 

Xcode をインストールすると、gcc (という名前の clang )　と lldb（デバッガ） が入るはずです。Xcode のインストール方法は適当に各自検索してください。

ターミナルで以下のコマンドを打ってバージョンが表示されればOKです。
```bash
gcc --version
lldb --version
```

VS code が自動で認識してくれる launch.json などが上手く動かない場合は、こちら([launch.json](maclldb/launch.json), [tasks.json](maclldb/tasks.json))をもっていってください。（C/C++ 環境 0.25.1 では上手く動くみたいですが、Insider build などでは上手く動かないケースもあるようです）

`トラブルシュート`

* VS code の挙動が変だという場合は、まず、新規ウィンドウで新規フォルダを開いて、hello.c でも作成してみてください。
* それでも、VS code が正しく動かない場合は、設定ファイルを削除してみましょう。下記 directory を削除してみてください。
  * `/Users/yourName/.vscode`: この directory 以下に extension などが配置されます。
  * `/Users/yourName/Library/Application Support/Code/`: こちらにユーザ設定などが保存されているようです。

### Linux

Linux つかいのあなたは、自分で検索すれば手順はすぐわかるはず。

## VS Code の設定

C/C++ 環境

* extension ボタンの入力フォームで C/C++ を選んでインストールボタンを押しましょう。

日本語環境

* コマンドパレット経由で、いろんな設定が可能です。View->Command Palette からアクセスします。
* コマンドパレットの入力欄で、configure display language とか入力して、希望言語 (ja) を選んでおしまい。
* まだ対象言語をインストールしてない場合は、additional language を選んで、インストールしたい言語を選びましょう。


Git repository からの checkout

* コマンドパレット（メニューで）で、`git`と入力しすれば、`Git: clone` を選択できるはず。
* そこで、git repository の clone 用 location 情報を入力しましょう。github などの repository 用ページを見た際、`clone`ボタンをクリックすれば乗っている情報を copy&paste すれば OK です。

