---
tags:
    - Javaメモ
    - C++メモ
---

# Java

## ウェブアプリ
<details>インスタンスの生成、インスタンスのライフサイクル管理を行う
<summary>DI(Dependency Injection) @がつくやつ
</summary>
</details>

#### スコープ
デフォルトではsingletonになり、インスタンスが一つしか作られないため注意が必要

各スコープの有効期限は以下の通り
<details>ユーザがログインしてからログアウトするまでが有効期限。ユーザ情報やそれに紐づく権限などの情報をSessionスコープとして持っておく
<summary>Sessionスコープ
</summary>
</details>

<details>HTTPの1リクエストが有効期限。ユーザ登録画面から登録結果画面までがRequestスコープの範囲
<summary>Requestスコープ
</summary>
</details>

# C++

<details>
ビットxorして代入
<summary>^=
</summary>
</details>

<details>クラス、構造体、POD(int等のいわゆるプレーンな古い型)を複数入れることが出来る"入れ物"のことである
<summary>コンテナクラス </summary>
</details>


<details>
<div>

staticメンバ変数は、クラス定義内に記述しただけでは定義したことにならず、実体となる定義を別の所に書く必要がある


staticメンバ変数の型が、constな整数型か、constなenum型の場合に限っては、宣言と同時に初期化子を与えられる

```C++:static.cpp
class X {
private:
    enum E { e1, e2 };

    static const int ci = 100;     // OK
    static const E ce = e1;        // OK
    static const double cf = 1.0;  // コンパイルエラー
    static int i = 100;            // コンパイルエラー
    static E e = e1;               // コンパイルエラー
};
```

</div>
<summary>staticメンバ変数</summary>
</details>

***

## const
**constがアスタリスクの左にあるときはポインタが指し示すデータが不変**

**constがアスタリスクの右にあるときはポインタそのものが不変**

```C++:const.cpp
char greeting[] = "Hello";
const char *p = greeting;       //ポインタは非constでデータはconst
char *const p = greeting;       //ポインタはconstでデータは非const
const char *const p = greeting; //ポインタもデータもconst
```
<details>
constなメンバ関数で、メンバ変数を変更しようとするとエラーになる

そこで、**mutable修飾子**をメンバ変数につけるとconstなメンバ関数内でも変更可能になる
<summary>constなメンバ関数(関数名の後ろにconstを指定)
<summary>
</details>


<details>参照先を書き換えることができない
<summary>const& </summray>
</details>

***
参照

* 参照は必ず初期化しなければならない
* 参照は参照する変数を途中から変更することができない

*** 

コンパイラが自動生成することを望まない関数の使用を禁止する方法

* 対応するメンバ関数をprivateに宣言し、定義を書かない
* Uncopyableのようなクラスを使う
