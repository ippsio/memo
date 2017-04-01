# Swift入門
## 1
- 概要
  - 公式ドキュメントのありか
    - https://developer.apple.com/swift/
- Swift実行するためのPlayGroundの作成方法
  - Swift試したいだけであれば、PlayGroundで作成すればOK
- 学習するのに都合の良いエディタの設定方法について
  - Preferences> TextEditing
    - 行番号の表示
    - エディタのフォントサイズをちょっと大きくすると見やすい。
    - コンソールも同様。そのやりかたについて。

## 2
- 初めてのプログラムを書く
- 最終的にはHello Worldが画面表示できるようになる。
  - Swiftの文字列はダブルクォート。
  - 行末のセミコロンは省略できる
  - プログラムの実行の方法
  - プログラムを自動実行する方法
    - 三角ボタンを長押し。
  - print("xxx")は末尾に改行がつくよ。
  - コメントは Javaと一緒。
    - // や /* */
    - Command＋／で行をコメントできるよ。
  - エディタの右側には、メソッドが評価された結果を表示する領域がある（灰色のところ）

## 3 定数と変数
- 定数
  - 値の再代入ができない
    - 再代入しようとするとエディタ上でコンパイルエラーが表示される。
  - 宣言
    - let msg: string = "hogehoge"
    - 基本的にはletは型を指定してあげないといけない。
    - ただし "hogehgoe"は文字列であることが自明なので let msg = "hogehoge"と省略することができる（型推論）。

- 変数
  - 値の再代入ができる
  - 宣言
    - var msg = "hogehoge"と書く。

## 4 基本的なデータ型
- 基本的な型
  - Int
    - let i: Int = 10
    - let i = 10（型推論）
  - Float/ Double
    - let d = 53.8（型推論）
  - String
    - let s = "hello"
  - Bool
    - let flag = true
  - 一度宣言した型は変えられない。
    - let x = "abc" としたあとに、 count = 5 という型変更はできない。
    - ただし、x = String(5)という操作はできる（この時、x="5"となる）

## 5 データの演算
- 10/3 -> 3
- 10.0/3 -> 3.3333
- 10%3->1
- 文字列の演算
  - ＋で連結できる。
- 文字列の中に変数を埋め込む
  - "y is  \(y)" のように、変数をカッコで囲い、先頭にバックスラッシュをつける。
- 論理値
  - javaで使い慣れたものが使える。
  - && || !

## 6 if条件分岐
- Swiftのif分岐はこのルールで書く
```
if score >  80 {
  print("great")
} else if score > 60 {
  print("good")
} else {
  print("so so")
}
```

- 三項演算子も使える
```
let result = score>80? "great":"so so"
```

## 7 Switch条件分岐
- 書き方
  - 一般的なswitchみたいに、各caseに```break;``` を置かなくても、swiftはよしなにやってくれる。
```
switch i {
  case 0:
    print("zero")
  case 1, 2, 3:
    print("１か２か３");
  case 4...6:
    print("４か５か６")
  case 7..<9:
    print("7から9を含まない数まで")
  case let n where n > 20:
    print("\(n) is big.")
  default:
    print("omg")
}
```

## 8 while文
- 書き方
```
while n < 3 {
  print(n)
  n += 1
}
```

- repeat - while
- javaでいうdo-whileです。
```
repeat {
  print(n)
  n += 1
} while n <  3
```

## 9 forループ
- 書き方
```
for i in 0...5 { // 0,1,2,3,4,5
  print(i)
}
```

- break と continue
```
for i in 0...5 { // 0,1,2,3,4,5
  if i == 1 {
    continue
  }
  if i == 3 {
    break
  }
  print(i)
}
```

## 10 オプショナル型
- nil とは、nullのこと
- nilになれる型となれない型がある。
- nilになりえそうな型は特殊な型として宣言する必要がある
  - これがオプショナル型
-宣言方法
  - let s: Optionnal<String> = nil
  - let s: String? = nil
- オプショナル型から値を取り出す方法
  - この行為を「unwrap（アンラップ）」という
```
let s: String? = nil
if s != nil {
  print(s!) // !をつけるとunwrap
}
```
- 毎回!でunwrapするのは面倒。そんなときに使うのがOptional Binding
  - sがnilじゃなかったらifの中に入る
```
let s: String? = nil
if let value = s { // Optional Binding
  print(value)
}
```

- 「??」を使う方法
  - sがnilならメッセージを、そうでなければsの値を表示するには
```
let s: String? = nil
print(s ?? "oh, s is nil..")
```


## 11 配列
- 配列、タプル
    - 順序付きデータ
      - 配列```var items = ["apple", "orange"]```（型推論だけどStringの配列）
      - タプル```var items = ("apple", 15)```
        - タプルは色々な型のデータを入れられる。
- 集合
  - 順序なし、重複を許さない
- 辞書
  - キーと値でデータを管理

- 配列の宣言
```
var scores: [Int] = [1, 2, 3]
var scores = [1, 2, 3] （型推論）
```

- 配列のメソッド
```
var scores = [1, 2, 3]
print(scores.count) ：3
print(scores.isEmppty)　： false
```

- 空のString配列の定義して、要素を追加する例
```
var namesss = [String]()
names.append("hoge")
names.append("fuga")
names += ["moge"] // この書き方もできる
```

## 12 タプル
- タプルは、配列とは違い、異なる肩のデータを入れることができる。
  - 配列はStringの配列とか数値の配列とか。
- タプルはちょっとしたデータを取り回すのによく使う。
```
var items = ("apple", 1)
let (product, amount) = items とすると
product = "apple"が入る。
/*amount = には1が入る。“”*/
```

- amountは使わないよ、という場合、_を使うとその値を安全に破棄できるとのこと。
- [ ] 破棄というのがなんだかよくわからないが。
```
var items = ("apple", 1)
let (product, _) = items とすると
product = "apple"が入る。
```

## 13 集合
- javaで言うjava.util.Setのこと。
```
var itemss: Set<String> = ["a", "b", "b", "c"]
items.insert("d")
items.remove("a")
print(items)   ===> 結果："b", "c", "d"
print(items.isEmpty) ===> false
```

- 集合演算
```
let a: Set = [1,3,5,8]
let b: Set = [3,5,8,9]
// 和集合
print(a.union) ===> [1,3,5,8,9]
// 積集合
print(a.intersection) ===> [3,5,8]
// 差集合
print(a.subtracting) ===> [1]
```

## 14 辞書
- javaで言うjava.util.Mapのこと。
```
var items: Dictionary<String, Int> = ["apple":1, "orange":2]
または
var items = ["apple":1, "orange":2]（型推論）
```

- 要素の取り出し
  - キーに対する値は存在しない場合がある＝Optional型である。
```
var items = ["apple":1, "orange":2]
print(items["apple"]) ===> コンパイルエラー
print(items["apple"] ?? "nil") ===> 1
```

- 要素の追加
  - こう書けばいい
```
var items = ["apple":1, "orange":2]
items["new_item"] = 50
print(items.count) ===>  3
```

- タプルを使った取り出し
```
var items = ["apple":1, "orange":2]
for (key, value) in items {
  print("キー\(key)は、値は\(value)")
}
```

- 空の辞書の作成
```
let hoge = [String: Int]()
print(hoge.isEmpty) ===> true
```

## 15 関数
```
func sayHello() {
  print("hello")
}
func sayHi() -> String {
  return "Hi"
}
sayHello()
print(sayHi())
```

## 16 引数
- **Swiiftでは引数は、定数として扱われる**
- 基本となる書き方
```
func sayHi(name: String) {
  print("Hi \(name)")
}
sayHi(name: "tom")
```

- 引数名fromという名前で引数を渡す
```
func sayHi(from name: String) {
  print("Hi \(name)")
}
sayHi(from: "tom")
```

- 引数名を省略したい時は _ を使う
```
func sayHi(_ name: String) {
  print("Hi \(name)")
}
sayHi("tom")
```

- 関数側で初期値を設定
```
func sayHi(_ name: String = tom) {
  print("Hi \(name)")
}
sayHi()
```

## 17 inoutキーワード
- **Swiiftでは引数は、基本的に定数として扱われる**
- 再代入しようとするとコンパイルエラーになる
- が、引数を定数として渡さない（参照渡ししたい）場合は inoutキーワードを使う。

- ○　値の再代入する時の正しい書き方
```
func add(x: inout Int) {
  x = x + 10
}
var i = 10
add(x: &i)
print(i) ===> 20
```

- ☓　inoutキーワードをつけないと再代入できない
```
func add(x: Int) {
  x = x + 10 ===> コンパイルエラー
}
var i = 10
add(x: i)
print(i)
```

- ☓　再代入する時は関数呼び出し時に &をつけないといけない
```
func add(x: inout Int) {
  x = x + 10
}
var i = 10
add(x: i)  ===> コンパイルエラー
print(i)
```

## 18 クラスで型を作る
```
class User {
  let name: String // 値を変更しなくても良いと思ったら定数で定義
  var score: Int   // 値を変更したかったら変数として定義
  init() { // イニシャライザ
    self.name = "my name"
    sellf.score = 23;
  }
}
// インスタンス化
//let user: User = User()
let user = User() // 型推論でもOK
```

## 19 イニシャライザを使う
- javaで言うコンストラクタ
```
class User {
  let name: String
  var score: Int
  //init(name: String, score Int) {   // イニシャライザ
  init(_ name: String, _ score Int) { // 呼び出し側で変数名を省略したい場合
    self.name = name
    sellf.score = score
  }
}
// インスタンス化
//let tom = User(name: "tom", score: 23)
let tom = User("tom", 23) // initで _ を使えば、変数名を省略することもできる。
```

## 20 計算プロパティ
- 動的に計算してくれるプロパティのことを計算プロパティと呼ぶ
- プロパティとはjavaで言うインスタンス変数のこと。
```
class User {
  var score: Int
  var level: Int {
    get {
      return Int(score / 10)
    }
    set {
      // 渡された値は  newValue という名前で受け取ることができる！
      if 0 <= newValue
        score = newValue * 10 // self.scoreはレベルの10倍とする場合
      }
    }
    init(_ name: String, _ score: Int) {
      self.name = name
      self.score = score
    }
  }
}
let tom = User("tom", 23
print(tom.level) ===> 2.3 -> 2
tom.level = 5
print(tom.score) ===> 50
tom.level = -3
print(tom.score) ===> 50
```

## 21 プロパティの値を監視する
- 値が変わった時に何らかの処理を噛ませたい時に、willSet, didSetというものを使うことができる。　
```
class User {
    let name: String
    var score: Int {
        willSet {
            // before change
            print("\(score) -> \(newValue)")
        }
        didSet {
            // after change
            print("Changed: \(score - oldValue)")
        }
    }
    init(_ name: String, _ score: Int) {
        self.name = name
        self.score = score
    }
}
let tom = User("tom", 23)
tom.score = 53
tom.score = 40
```

## 22
- メソッド＝クラスに定義された関数
```
class User {
    let name: String
    var score: Int
    init(_ name: String, _ score: Int) {
        self.name = name
        self.score = score
    }
    // method
//    func sayHi() {
//        print("hi \(name)")
//    }
//    func sayHi(msg: String) {
    func sayHi(_ msg: String) {
        print("\(msg) \(name)")
    }
}
let tom = User("tom", 23)
//tom.sayHi()
//tom.sayHi(msg: "hola")
tom.sayHi("hola")
```
## 23 クラスの継承
- クラスの継承
  - ```class AdminUser: User {``` とすると、Userを継承したAdminUser クラスを作れる
- メソッドのオーバーライドしたい時は、
  - 子クラスのメソッド定義で overrideと書く
- メソッドをオーバーライドしたくない場合
  - 親クラスのメソッドにfinalをつける
```
class User {
    let name: String
    var score: Int
    init(_ name: String, _ score: Int) {
        self.name = name
        self.score = score
    }
    final func sayHi() {
        print("hi \(name)")
    }
}
class AdminUser: User {
    func sayHello() {
        print("hello \(name)")
    }
    override func sayHi() {
        print("[admin] hi \(name)")
    }
}
let tom = User("tom", 23)
let bob = AdminUser("bob", 33)
print(bob.name)
print(bob.score)
bob.sayHi()
bob.sayHello()
```

## 24 型プロパティ、型メソッド
- javaで言うstaticな変数、staticなメソッド（みたいなもの）
```
class User {
    let name: String
    var score: Int
    static var count = 0
    init(_ name: String, _ score: Int) {
        self.name = name
        self.score = score
        User.count += 1
    }
    func sayHi() {
        print("hi \(name)")
    }
    class func getInfo() {
        print("\(count) instances")
    }
}
//
class AdminUser: User {
    func sayHello() {
        print("hello \(name)")
    }
    override func sayHi() {
        print("[admin] hi \(name)")
    }
    override class func getInfo() {
        print("[admin] \(count) instances")
    }
}
User.getInfo()
let tom = User("tom", 23)
User.getInfo()
//
AdminUser.getInfo()
let bob = AdminUser("bob", 33)
AdminUser.getInfo()
```

## 25 型キャスト
- javaで言うinstanceof は、Swiftでは is
- Optional Bindingで扱うという方法もある。
```
// 型キャスト

class User {
    let name: String
    init(_ name: String) {
        self.name = name
    }
}
class AdminUser: User {}

let tom = User("tom")
let bob = AdminUser("bob")

let users: [User] = [tom, bob]

for user in users {
//    if let u = user as? AdminUser {  // Optional Binding
//        print(u.name)
//    }
    if user is AdminUser {
        let u = user as! AdminUser
        print(u.name)
    }
}
```
## 26 プロトコルの適合
- protocolとは、javaで言うinterface。
  - あるメソッドを実装することを強制させる
  - interface同士は継承できる（javaと一緒）
  - interfaceは、クラスに複数適合することができる（javaと一緒）

```
// Protocol

protocol Printable {
    var type: String { get }
    var count: Int { get set }
    func printout()
}

class User: Printable {
    let type = "Laser"
    var count = 0
    let name: String
    init(_ name: String) {
        self.name = name
    }
    func printout() {
        count += 1
        print("\(type): \(count)")
    }
}

let tom = User("tom")
tom.printout()
tom.printout()
tom.printout()
```

## 27 エクステンションで型を拡張する
- 既存の型に新しいプロパティやメソッドを追加することができる仕組み
- protocol（javaで言うinterface）は通常メソッドの実装を持たないが、extensionを使うとprotocolに実装を持たせることもできる。

```
// extension

//extension String {
//    var length: Int {
//        return self.characters.count
//    }
//}
//
//let msg = "hello"
//print(msg.characters.count)
//print(msg.length)

protocol Printable {
    func printout()
}

extension Printable {
    func printout() {
        print("now printing...")
    }
}

class User: Printable {
    let name: String
    init(_ name: String) {
        self.name = name
    }
}

let tom = User("tom")
tom.printout()
```



## 28 値型と参照型
- Classは参照型
- Int, Double, Array ... は値型

- 値型の挙動
```
var original = 10
var copy = original
original = 20
print(original) ===> 20
print(copy) ===> 10
```

- 参照型の挙動
```
class User {
  var name: String
  init(_ name: String) {
    self.name = name
  }
}
var original = User("tom")
var copy = original
original.name = "bob"
print(original.name) === "bob"'
print(copy.name) ===> こちらも"bob"
```

## 29 構造体
- 構造体は
  - クラスに似ているが、値型である。
  - 継承ができない
  - うっかり変更されたくない値を扱うのに良い。
```
struct User {
  var name: Stringinit(_ name: String) {
    self.name = name
  }
  // 構造体内の値を変更するようなメソッドを作成したい時は
  // 先頭に'mutating'をつけないとコンパイルエラーが出る
  mutating func rename() {
    self.name = name.uppercased()
  }
}
var original = User("tom")
var copy = original
original.name = "bob"
print(original.name) === "bob"'
print(copy.name) ===> こちらは"tom"
```

## 30 列挙型
- 関連する値をまとめて型にした場合のもの
- enuですな。

```
enum Direction: Int {
  case right = 1
  case left  = -1
}
var dir: Direction
dir = .right

switch (dir) {
  case .left:
    print("左")
  case .right:
    print("右")
}
print(Direction.right.rawValue) ===> 1
```

## 31 ジェネリクス
- 汎用化されたデータ型
```
//func getThree(x: Int) {
func getThree<T>(x: T) {
  print(x)
  print(x)
  print(x)
}
getThree(x: 5) ===> 5 5 5
getThree(x: 1.3) ===> 1.3 1.3 1.3
getThree(x: "Hello") ===> Hello Hello Hello
```

## 32 サブスクリプト
- subscript
  - インスタンスに対して、配列と同じようにインデックスを付けられるようにするもの。
  - クラス（のインスタンス）だけではなく、構造体や列挙型にも使える。
```
// subscript

class Team {
    var members = ["taguchi", "fkoji", "dotinstall"]
    subscript(index: Int) -> String {
        get {
            return members[index]
        }
        set {
            members.insert(newValue, at: index)
        }
    }
}

var giants = Team()
//giants[0] = "taguchi"
print(giants[1]) // fkoji
giants[3] = "tanaka"
print(giants[3]) // tanaka
```

## 33 guard（ガード）
- 異常処理をわかりやすく書くための仕組み
- 入力値チェックなどで、おかしな入力値だった場合だった場合なら、すぐにreturnする仕組み。

```
func sayHi(_ msg: String?) {
  if let s = msg {
    print(s)
  } else {
    print("value not set!")
  }
}
sayHi(nil)
sayHi("hello")
```

- Early return ,Early exit
```
func sayHi(_ msg: String?) {
  if msg == nil {
    print("value not set!")
    return
  }
  print(msg!) // unwrapしてmsgを表示
}
sayHi(nil)
sayHi("hello")
```

- guardを使った書き方。
- guardを使うと「これは異常処理のためのロジックを書いているんだ」と読み手にわかりやすい。
```
func sayHi(_ msg: String?) {
  guard let s = msg else {
    print("value not set!")
    return
  }
  print(s) // guardの後なら「！」でunwrapしなくて良い
}
sayHi(nil)
sayHi("hello")
```

## 34 例外処理
```
enum LoginError: Error {
    case emptyName
    case shortName
}

class User {
    let name: String
    init(_ name: String) {
        self.name = name
    }
    func login() throws {
        guard name != "" else {
            throw LoginError.emptyName
        }
        guard name.characters.count > 5 else {
            throw LoginError.shortName
        }
        print("login success")
    }
}

//let tom = User("tom")
//let tom = User("takahashi")
let tom = User("")

do {
    try tom.login()
} catch LoginError.emptyName {
    print("please enter your name")
} catch LoginError.shortName {
    print("too short")
}
```

## 35 Optional Chaining
- Optional Chaining
  - Optinal型が複数つながるときに安全にnilチェックできる仕組み
```
class User {
  var name: String? = "" // nameはnilかもしれないことを示唆
}
let user: User? // ?でOptional型に＝Userはnullかもしんないことを示唆
user = User()
user?.name = "him"

// まともにnilチェックしようとすると面倒臭いの、Optional Chainingしてみる
if let s = user?.name?.uppercased() {
  ~~~~~~~~~~~~~~~~~~~~~ Optional Chaining
  print(s)
} else {
  // userかuser.nameがnilなら、こちらにくる
  print("user or user.name is nil")
}
```

## 36 暗黙的アンラップオプショナル型
- Implicitly Unwrapped Optional
- 暗黙的アンラップオプショナル

```let msg: String?
msg = "hello"

if msg != nil {
  print(msg!)
}
```

- 暗黙的アンラップオプショナル型を使うと、いちいちnilチェックする必要がなくなる
- 暗黙的アンラップオプショナル型は、絶対にnilではないことを保証されている値にだけ使うべし！
- ただしぬるぽが出る可能性が発生する
```let msg: ImplicitlyUnwrappedOptional<String>
msg = "hello"
print(msg) // この場合、末尾の！も不要
```

- 上記の書き方は長いので、省略表記するとこうなる
```
let msg: String!
msg = "hello"
print(msg);　// こちらも、末尾の！不要

− なんでこんな型が必要なのか？
  - iOS開発などで使われる型の中では、初期化の時だけnilだけど、その後は必ず値がちゃんと入っているようなものがある。
  - そういうものを扱う時に、暗黙的アンラップオプショナル型は都合が良い、とのこと。
