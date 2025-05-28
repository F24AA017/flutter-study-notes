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
