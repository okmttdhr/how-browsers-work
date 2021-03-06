
# how-browsers-work

ブラウザに`google.com`を入力してからページ表示までの説明

## URLの入力

- キーボードの'g'を押す。
- キーボードへの物理的な接触が電気信号に変換される。
- OSがそれを理解してイベントを発火する。
- ブラウザがそれを理解してイベントを発火する。
- ブラウザに'g'が入力される。
- ブラウザ、もしくはOSアプリの`auto complete`のアルゴリズムによって、入力候補が表示される。
- `google.com`を入力し終えたあと、Enterキーを押す。
- (キーボードからブラウザまでのフローは前述の通り)

## TCP/IP接続の確立

- ブラウザがURLのパースを行う。
  - URLか検索語彙かの判別を行う。検索語彙の場合は今回は説明しない。
  - non-ASCIIな文字列を変換する。
  - HTTPかHTTPSかの判別を行う。
- OSがDNSによって対象IPアドレスを知る。
- ARPによって対象IPアドレスからMACアドレスを取得する。
- ブラウザが対象IPアドレスを受け取る。
- 指定されたポートで、TCP/IP接続を確立する。
- HTTPSを使用していれば、クライアントとサーバーでの鍵共有のやり取りを行う。

## HTTPによる通信

- ブラウザからHTTPリクエストを送信する。
- サーバーでHTTPリクエストを処理する。
  - メソッドを判別する。
  - 該当メソッドがサーバーに対して許可されているかを判別する。
- サーバーがページの情報を返す。
- ブラウザがサーバーからHTTPレスポンスを受け取る。

## ページの描画

- ブラウザがHTMLを解釈する。
  - DOMツリーを構築する。
  - レンダーツリーを構築する。
  - レンダーツリーとDOMツリーのリレーションを決める。
- ブラウザがCSSを解釈する。
  - 優先順位を計算する。
- レイアウトを決める。
- UIの情報を解釈し、実際にページを描画する。
