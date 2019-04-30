# 作り方の解説

## カレンダーの日付と日記の入力欄をリンクする
まず、カレンダーのセルをクリックした際に、その日の日記のタイトルと本文を入力部分にセットするために、関数名を`presetDiary`とし、引き数に日付のYYYY.M.Dの文字列を渡す。

次に、日記を保存するためにボタンをクリックした際に、イベントを通して日記の日付を渡せるようにするための準備として、日記を保存するボタンを`getElementByIdメソッド`で取得し、`data-date属性`として、該当する日付を持たせる。

さらに、YYYY.M.D_title、YYYY.M.D_bodyのキーで、localStorageから日付の日記タイトルと本文を取得。

加えて、日記のタイトル入力欄と本文入力のテキストエリアを取得して、日記のデータがあればそれぞれ表示し、日記のデータがなければ空欄にする。

## 改善点
* `// 日記データがあれば 日付の下にアンバーバーを表示`この部分クラスの付与をして、少し変えよう。
* 何かもう１つ機能を追加する
* 削除機能作ろう（本当に削除しますか？ダイアログも作ろう。）
* クラス名もBEMに整理しよう

## わかってないところ
* 曜日の配列と日にちの配列をごっちゃに考えてるからわけわからなくなってる。（dateが日にち、dayが曜日）
* 全体の設計というか、どうゆう手順で作ればいいか（ブログで言うところの先に見出しを考える的な）を考えていなくて大枠を捉えれていないから、迷走してる。
* localへのデータ保存と取り出しの部分の仕組みがまだよく理解できてない。
* もう一回ゼロからこれ自分で作ってみよう。
* `\n`は改行


## 日記アプリの機能の整理
1. 日記の保存：localStorageを使う
2. 保存している日記を日別に呼び出す：イベントを使う
3. 当月の日付をテーブルで表示：Dateオブジェクトを使う
4. 日記の削除：removeItemを使う


## データの保存について
今回はデータを永続的に保存できる`localStorage`を使う。
`localStorage`は、`windowオブジェクト`の`localStorageプロパティ`でアクセスできる。
なお、JSの記述では`window.`を省略できるので、`localStorage`と記述するだけでストレージを利用できる。

```
//WebStorageへの保存

var storage = localStorage;
storage.setItem(キー,値);

//次の書き方でも同じ意味
storage.キー = 値;
storage[キー] = 値;
localStorage[キー] = 変数名;

//保存したデータの参照
var 変数名 = storage.getItem(キー);

//次の書き方でも同じ意味
var 変数名 = storage.キー;
var 変数名 = storage[キー];

//保存したデータの削除
storage.removeItem(キー);
```