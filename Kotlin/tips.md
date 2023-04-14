## 文法
* クラス関係
  * デフォルト値を設けることで生成時に省略することができる（デフォルト値が適用される）
    * 全て同じデータ型とかだとうまく省略が認識されないので、その際は引数の名前を指定して生成するとうまく行く
        ```kotlin
        // こんな感じ
        val person = Person(age = 25)
        ```
  * getter,setterが自動生成される書き方
    ```kotlin
    // コンストラクタ引数を使う:
    class Person(val name: String, var age: Int)
    
    // クラス本体内でプロパティを宣言する:
    class Person {
    val name: String = "John Doe"
    var age: Int = 30
    }
    ```
  * data classは、主にデータを保持する目的で作成されたクラスで、自動的にいくつかの機能が生成されます。<br>
  具体的には、equals()、hashCode()、toString()、copy()、およびデータクラスのプロパティに対するcomponentN()関数が自動的に生成されます。
  <br>通常のclassでは、これらの機能は手動で実装する必要があります。
  <br>どちらを使用するかは、目的や要件に応じて選択する必要があります。データの格納と簡単な操作が目的であれば、data classが適しています。一方、複雑な振る舞いや機能が必要な場合は、通常のclassを使用する方が適切です。
  * クラス定義にopenというprefixをつけると継承可能なクラスを定義できる
    * ちなみにopenをつけたクラスのメソッドに継承させたいメソッドがあればそのメソッドへopenをつけると実現できる
  * クラス定義にsealedというprefixをつけると同一ファイルでしか継承できないシールドクラスを定義できる
  * プロパティの定義でアクセサメソッドが自動生成される
    * valで定義するとgetterのみ自動生成される（varの場合はどちらも）
  * lateinitでプロパティの初期化を遅延する
    * 初期値を設定せずにクラスへプロパティを定義することができる（varでのみ定義可能）
    * プロパティ定義時にlateinitをprefixとしてつけるだけ
    * 初期値がないので値を設定する前にgetterを呼び出そうとすると実行時にエラーとなる
* ifやwhenについては文ではなく式として定義することができる
  * つまり戻り値が必要な変数定義や関数にそのまま書くことができる
* 拡張関数や拡張プロパティは既存クラス(StringやIntなど)に対して関数やプロパティを増やせる。
  * そうすることで,String.isNotEmptyのようなことができるようになる
* enumについて
```kotlin
enum class MyEnum(val valuesList: List<String>) {
    ENUM1(listOf("A", "B", "C")),
    ENUM2(listOf("D", "E", "F"));

    companion object {
        fun containsValue(value: String): Boolean {
            return values().any { it.valuesList.contains(value) }
        }
    }
}
```
## コレクション
* 基本形は以下の3つ
  1. List
     * 重複要素を持つことができる: Listは重複する要素を含むことができます。 
     * 順序が保証される: Listは要素の順序を保証し、インデックスによって要素にアクセスできます。 
     * listOfメソッドで作成可能（イミュータブルなオブジェクトとして作成される）
     * MutableListを作りたければmutableListOfメソッドで作成する
  2. Map
      * キーは一意: Mapの各エントリは一意のキーとそれに関連付けられた値から構成されます。キーは一意であるため、重複するキーを持つことができません。しかし、異なるキーに関連付けられた値は重複しても構いません。
      * 順序が保証されない: 一般的なMapは要素の順序を保証しませんが、LinkedHashMapを使用すると挿入順序が保持されます。
      * mapOf(key to value)で作成可能（イミュータブルなオブジェクトとして作成される）
      * MutableMapを作りたければmutableMapOfメソッドで作成する
  3. Set
      * 重複要素を持たない: Setは一意の要素のコレクションで、重複する要素が存在しないことが保証されます。
      * 順序が保証されない: 一般的なSetは要素の順序を保証しませんが、LinkedHashSetを使用すると挿入順序が保持されます。
      * setOfメソッドで作成可能（イミュータブルなオブジェクトとして作成される）
      * MutableSetを作りたければmutableSetOfメソッドで作成する