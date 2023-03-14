# static
* newしなくても利用可能になる、つまり静的 
* 非staticなインナークラスは親クラスのフィールドやインスタンスメソッドにもアクセスできる。
<br>このため、親クラスへの参照を保持している。
<br>(不必要な親クラスへの参照は、メモリやGCへの悪影響が懸念される。)
* インナークラスをstaticにできる状況であれば、staticにすべき 
* staticフィールドはそのフィールドはいくらインスタンスをたくさん生成したとしても、クラスに１つだけ 
* 複数のインスタンスの間で共有されつづける情報、共有資源にして欲しいフィールドに static をつけます。
<br>クラス名.フィールド名 で呼び出せる。
<br>インスタンスを生成して呼び出しても同じモノにアクセスできます。 
* 定数定義の際にfinal static で宣言することで、new する度に同じ値がインスタンスに複製されることが防止され、メモリの節約となる 
* staticメソッドについて(https://qiita.com/uhooi/items/f32e20750d2fb0f2da46)

# 内部クラス
* https://qiita.com/liguofeng29/items/6cafca5bf92e0381ee42

# abstractとinterface
* https://qiita.com/yoshinori_hisakawa/items/cc094bef1caa011cb739

# enum
* 内部的にはabstractクラスであるjava.lang.Enumクラスを継承したクラス
* フィールドはコンパイル時に定数(static final)として定義される
* staticなので、クラスに属する、つまりクラスに1つなのでシングルトン、つまり==で比較できる

# equal vs ==
* ==は同値(
変数どうしの値（参照型の場合参照アドレス）が同じこと)、equalは等価(インスタンスは違うがインスタンスの価値は同じこと)
<br>つまり、プリミティブ型の比較は==を使い、参照型の比較はequalを使う
* enumの比較は==を使うべき(https://blog1.mammb.com/entry/2013/10/03/092927)
