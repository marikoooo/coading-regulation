## 変数の宣言

変数の宣言をする場合は、varを宣言
```
var hoge = value;
```

## 定数の宣言

定数を宣言する場合は大文字とアンダーバーを用いる
```
var HOGE = value;
```

## 文末のセミコロン

文末には必ずセミコロンを使用
```
var hoge = value;
```

## 関数のネスト

関数のネストはとても便利なので、利用して構いません
```
function hoge() {
  var huga = function() {
    /*...*/
  }
  /*...*/
}
```

## ブロック内での関数の宣言

if文などのブロック内での関数宣言はしないでください。
関数をシウようする場合には、変数に関数を代入して定義する

```
/*非推奨*/
if(x) {
  function foo() {}
}

/*推奨*/
if(x) {
  var foo = function() {};
}
```

## 例外処理

例外処理は使用しなければならない場合があります。
利用して構いません。

## メソッドとプロパティの定義

オブジェクトにメソッドとプロパティを追加するにはいくつかの方法がありますが
推奨される方法は次の通り

```
/*メソッド追加推奨例*/
hoge.prototype.bar = function() {
   /* ... */
};

/*プロパティ追加推奨例*/
/** @constructor */
function hoge() {
  this.bar = value;
}
```

## delete

プロパティを削除する場合はdeleteではなくnullを使用

```
/*非推奨*/
hoge.prototype.dispose = function() {
  delete this.property_;
};

/*推奨例*/
hoge.prototype.dispose = function() {
  this.property_ = null;
};
```

## 文字列リテラルが複数行になる場合
＋記号を用いて文字列を連結して記述する。
```
/* 推奨例 */
var myString = 'A rather long string of English text, an error message ' +
    'actually that just keeps going and going -- an error ' +
    'message to make the Energizer bunny blush (right through ' +
    'those Schwarzenegger shades)! Where was I? Oh yes, ' +
    'you\'ve got an error and all the extraneous whitespace is ' +
    'just gravy. Have a nice day.';
```

## 配列とオブジェクトモデル

使用可能です。以下の様な記述に則って使用してください。

```
/*配列の記述推奨例*/
var a = [x1, x2, x3];
var a2 = [x1, x2];
var a3 = [x1];
var a4 = [];

/*オブジェクトの記述推奨例*/
var o = {};

var o2 = {
  a: 0,
  b: 1,
  c: 2,
  'strange key': 3
};
```

----調べる　start

## クロージャ

クロージャは自身を取り囲むスコープへのポインタを保持しています。このためクロージャをDOM要素ヘ結びつけると、循環参照が発生しメモリリークとなることがあり、慎重に使用する必要があります。

## eval()

ユーザーの入力に悪意のあるスクリプトが混入していた場合、実行されてしまうおそれがあるので、ユーザーの文字列の入力に対して、evalを使用するのは避けてください。

## with(){}

ローカル変数と衝突するプロパティを持てるためプログラムの意図を大きく変える恐れがあります、使用しないでください。

## this

thisの参照先は呼び出す場所によって変化し、把握が困難になりやすいので、オブジェクトのコンストラクタ、メソッド、クロージャを設定する場合のみ使用するようにしてください。

## for in ループ

オブジェクト、マップ、ハッシュにキーを繰り返し処理する場合のみに使用してください。

## 連想配列

Array用の数字インデックス以外で配列要素にアクセスすることは許されていません。連想配列を使用したい場合はObjectにその機能が実装されているので、Objectの書式に則って記述してください

----調べる end


## 命名規則

関数の命名規則
```
functionNameLikeThis  //関数
variableNamesLikeThis  //変数
ClassNamesLikeThis  //クラス
EnumNamesLikeThis  //列挙型
methodNamesLikeThis  //メソッド
CONSTANT_VALUES_LIKE_THIS  //定数
hoge.namespaceNamesLikeThis.bar  //名前空間
filenameslikethis.js  //ファイル
```

## 独自のtoString()メソッド
独自のtoString()メソッドを追加する場合は、常に成功すること、他への影響が皆無であることが基準となります。この基準を満たさない場合は深刻な問題を引き起こす原因になります。

## 初期化の遅延
宣言した時点での初期化が常に可能というわけではないので、初期化の遅延は問題ありません。

## 明示的なスコープ
スコープを明示し、移植性の高さを保つとともに、明瞭さを向上させてください。

## コードの書式

### 波括弧

波括弧({)は宣言と同じ行に置きます。
```
/* 推奨例 */
if (something) {
  // ...
} else {
  // ...
}
```

### 配列とオブジェクトの初期化
```
/*一行で収まる場合の推奨記述例*/
var arr = [1,2,3];
var obj = {a:1,b:2,c:3};

/*複数行に渡る場合の推奨記述例*/
var inset = {
  top: 10,
  right: 20,
  bottom: 15,
  left: 12
};

this.rows_ = [
  '"Slartibartfast" <fjordmaster@magrathea.com>',
  '"Zaphod Beeblebrox" <theprez@universe.gov>',
  '"Ford Prefect" <ford@theguide.com>',
  '"Arthur Dent" <has.no.tea@gmail.com>',
  '"Marvin the Paranoid Android" <marv@googlemail.com>',
  'the.mice@magrathea.com'
];
```

### 関数の引数

可能な限り引数リストは同じ行に書かれるべきです。もし長くなり80文字を超える場合は適宜改行とインデントをつけ読みやすく整形します。

```
/* 推奨例 */
// スペース4つ分インデントし、80字で折り返します
// 関数をリネームしてもインデントの修正がありません。
goog.foo.bar.doThingThatIsVeryDifficultToExplain = function(
    veryDescriptiveArgumentNumberOne, veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy, artichokeDescriptorAdapterIterator) {
  // ...
};

// スペース4つ分インデントし、各業に1つずつ引数を記述します。
// 関数のリネームの影響がなく、引数が見やすくなります。
goog.foo.bar.doThingThatIsVeryDifficultToExplain = function(
    veryDescriptiveArgumentNumberOne,
    veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy,
    artichokeDescriptorAdapterIterator) {
  // ...
};

// 丸括弧にそろえて80字で折り返します。引数をグループ化しやすくなります。
function foo(veryDescriptiveArgumentNumberOne, veryDescriptiveArgumentTwo,
             tableModelEventHandlerProxy, artichokeDescriptorAdapterIterator) {
  // ...
}

// 丸括弧に揃えてインデントし、1行毎に引数を記述します。
//引数が見やすくなります
function bar(veryDescriptiveArgumentNumberOne,
             veryDescriptiveArgumentTwo,
             tableModelEventHandlerProxy,
             artichokeDescriptorAdapterIterator) {
  // ...
}
```

### 無名関数の引き渡し

関数の引数リスト内で無名関数を宣言する場合は、読みやすくするために、内容を文全体の左端からスペース2つ分もしくは無名関数宣言の左端からスペース2つ分インデントします。

```
/* 推奨例 */
prefix.something.reallyLongFunctionName('whatever', function(a1, a2) {
  if (a1.equals(a2)) {
    someOtherLongFunctionName(a1);
  } else {
    andNowForSomethingCompletelyDifferent(a2.parrot);
  }
});

var names = prefix.something.myExcellentMapFunction(
    verboselyNamedCollectionOfItems,
    function(item) {
      return item.name;
    });
```

### 空行

空行を論理的に関連性のあるコードをまとまりとして示すことができるので、適宜挿入するようにしてください。

### 二項・三項演算子
演算子は宣言の行に置きます。
```
/* 推奨例 */
var x = a ? b : c;  // 一行で収まる場合はこのように記述します

// 4文字分のインデントでも構いません
var y = a ?
    longButSimpleOperandB : longButSimpleOperandC;

// 最初のオペランドの位置までインデントする形でも構いません。
var z = a ?
        moreComplicatedB :
        moreComplicatedC;
This includes the dot operator.
//ドット演算子も同様です。
var x = foo.bar().
    doSomething().
    doSomethingElse();
```

## 文字列を表す引用符
二重引用符(")ではなく、単一引用符(')を使用する。
```
var msg = 'This is some HTML';
```

## 可視性の向上

JSDocを利用し、クラス、関数、プロパティの可読性を向上させます。
JSDocの詳しい解説はこちら http://www38.atwiki.jp/aias-jsstyleguide2/pages/14.html

## JavaScriptにおけるデータ型

コンパイラによる型の強制を推奨します。
JSDocへのデータ型を記述する際には具体的かつ正確に行ってください

データ型に関する詳しい解説はコチラhttp://www38.atwiki.jp/aias-jsstyleguide2/pages/17.html

## 注釈(コメント)の挿入

JSDocを使用してください。

## コンパイル

必須です。JS用のコンパイラ(Closure compilerなど)でコンパイルしておくようにしましょう。





