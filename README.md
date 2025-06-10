# flutter-study-notes
Flutter講座の学習記録

# 今日の日付

2025年5月20日

---

# ファイル構成の概要

## README.md

- プロジェクトの説明や使い方などを記載するファイル。
- このアプリケーションがどんなアプリケーションなのかを明記する。
- 一般的に以下のような情報が含まれる：
  - アプリの目的
  - インストール手順
  - 使用方法
  - スクリーンショットやリンクなど

## .gitignore

- Gitで管理しないファイルやフォルダを指定するためのファイル。
- 例：一時ファイル、ビルドファイル、IDEの設定ファイルなど。

---

# Flutterアプリケーションの構造と仕組み

## ウィジェットとウィジェットツリー

- Flutterでは、画面表示はすべて「ウィジェット」という部品で構成されている。
- ウィジェットの中にさらに別のウィジェットを入れることができる（再帰的構造）。
- このような構造をウィジェットツリー（Widget Tree）と呼ぶ。

## 実行の仕組み

- アプリケーションのエントリーポイント（起動点）は `main()` 関数。
- `main()` で `runApp()` を呼び出してアプリケーションを起動する。

  ```dart
  void main() {
    runApp(MyApp());
  }
  ```

## AppBarについて

- `AppBar` はアプリケーションバー（画面上部に表示されるバー）を構成するためのウィジェットクラス。
- 一般的にタイトル、戻るボタン、メニューアイコンなどを含む。
# Flutter Studio 入門：テキストの表示とスタイル設定

Flutter Studioでは、**ベーシックのTextウィジェット**をスマートフォンの画面にドラッグ＆ドロップすることで、簡単にテキストを表示できます。

## テキストのスタイル指定

Textウィジェットでは、以下のプロパティを使用してフォントの見た目を変更できます。

| プロパティ       | 説明                         | 例                                      |
|------------------|------------------------------|-----------------------------------------|
| `fontSize`       | フォントサイズ               | `fontSize: 24.0`                        |
| `fontWeight`     | フォントの太さ               | `fontWeight: FontWeight.bold`          |
| `fontFamily`     | フォントファミリー           | `fontFamily: 'Roboto'`                 |
| `fontStyle`      | フォントスタイル（斜体など） | `fontStyle: FontStyle.italic`          |
| `color`          | テキストの色                 | `color: Colors.blue`                   |

### 例：スタイル付きテキスト
```dart
Text(
  'こんにちは Flutter!',
  style: TextStyle(
    fontSize: 24.0,
    fontWeight: FontWeight.bold,
    fontFamily: 'Roboto',
    fontStyle: FontStyle.italic,
    color: Colors.blue,
  ),
)
# Flutterの基本UIウィジェットまとめ（説明＋コード付き）

Flutterでよく使うUIウィジェットを、説明とコード例とセットでわかりやすくまとめました。  
このまま丸ごとコピー＆ペーストで使えます。

---

## 1. ボタン系ウィジェット

### TextButton（テキストだけのボタン）  
シンプルに文字だけが表示されるボタン。背景は透明。押すと処理を実行。  
```dart
TextButton(
  onPressed: () {
    print('TextButtonが押された');
  },
  child: Text('TextButton'),
)
ElevatedButton（浮き出るボタン）
立体的で影が付いた背景のあるボタン。押しやすく見える。

dart
コピーする
編集する
ElevatedButton(
  onPressed: () {
    print('ElevatedButtonが押された');
  },
  child: Text('ElevatedButton'),
)
IconButton（アイコンだけのボタン）
アイコンがボタンになっている。設定画面などによく使う。

dart
コピーする
編集する
IconButton(
  icon: Icon(Icons.settings),
  onPressed: () {
    print('設定ボタンが押された');
  },
)
2. 入力ウィジェット
TextField（文字入力）
ユーザーが文字を入力できるテキストボックス。フォームなどに使う。

dart
コピーする
編集する
TextField(
  decoration: InputDecoration(
    labelText: '名前を入力',
  ),
  onChanged: (text) {
    print('入力中: $text');
  },
)
3. 選択・切り替えウィジェット
Checkbox（チェックボックス）
チェックのON/OFFを切り替える四角いボタン。

dart
コピーする
編集する
bool _checked = false;

Checkbox(
  value: _checked,
  onChanged: (bool? value) {
    setState(() {
      _checked = value!;
    });
  },
)
Switch（スイッチ）
ON/OFFをスライドで切り替えるトグルスイッチ。

dart
コピーする
編集する
bool _switchValue = false;

Switch(
  value: _switchValue,
  onChanged: (bool value) {
    setState(() {
      _switchValue = value;
    });
  },
)
Radio（ラジオボタン）
複数から1つだけ選ぶ丸い選択ボタン。

dart
コピーする
編集する
String _radioValue = 'A';

Radio<String>(
  value: 'A',
  groupValue: _radioValue,
  onChanged: (String? value) {
    setState(() {
      _radioValue = value!;
    });
  },
)
DropdownButton（ドロップダウンメニュー）
選択肢の中から1つを選ぶプルダウンリスト。

dart
コピーする
編集する
String _dropdownValue = 'One';

DropdownButton<String>(
  value: _dropdownValue,
  onChanged: (String? newValue) {
    setState(() {
      _dropdownValue = newValue!;
    });
  },
  items: <String>['One', 'Two', 'Three'].map<DropdownMenuItem<String>>((String value) {
    return DropdownMenuItem<String>(
      value: value,
      child: Text(value),
    );
  }).toList(),
)
4. その他の便利ウィジェット
Slider（スライダー）
バーをスライドして値を調整できるウィジェット。

dart
コピーする
編集する
double _sliderValue = 50.0;

Slider(
  value: _sliderValue,
  min: 0,
  max: 100,
  onChanged: (double value) {
    setState(() {
      _sliderValue = value;
    });
  },
)
FloatingActionButton（丸い浮くアクションボタン）
画面の右下に浮く丸いボタン。主に追加や新規作成などの操作に使う。

dart
コピーする
編集する
FloatingActionButton(
  onPressed: () {
    print('FABが押された');
  },
  child: Icon(Icons.add),
)
ListView（縦スクロールのリスト表示）
縦方向にスクロールできるリストを作成。大量のアイテム表示に適している。

dart
コピーする
編集する
ListView.builder(
  itemCount: 10,
  itemBuilder: (BuildContext context, int index) {
    return ListTile(
      title: Text('アイテム $index'),
    );
  },
)
Column（縦方向に並べるレイアウト）
複数のウィジェットを縦に順番に並べる。

dart
コピーする
編集する
Column(
  children: [
    Text('上のテキスト'),
    Text('下のテキスト'),
  ],
)
Row（横方向に並べるレイアウト）
複数のウィジェットを横に順番に並べる。

dart
コピーする
編集する
Row(
  children: [
    Icon(Icons.star),
    Text('スター'),
  ],
)
5. まとめ一覧表
用途	ウィジェット名	説明
ボタン	TextButton, ElevatedButton, IconButton	文字やアイコンの押せるボタン
文字入力	TextField	ユーザーの文字入力用テキストボックス
選択肢	Checkbox, Switch, Radio, DropdownButton	ON/OFFや選択肢の切り替え・選択に使う
その他UI	Slider, FloatingActionButton, ListView, Column, Row	操作やレイアウトを助ける便利なウィジェット


