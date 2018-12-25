# 配列

## 配列の基本

配列の宣言
```java
String[] week = new String[7];
```
```
week ==> String[7] { null, null, null, null, null, null, null }
```

配列への代入
```java
String[] week = new String[7];
week[0] = "Sun";
```
```
$2 ==> "Sun"
```

配列の参照
```java
String[] week = new String[7];
week[0] = "Sun";
System.out.println(week[0]);
System.out.println(week[1]);
```
```
Sun
null
```

配列の長さ
```java
String[] week = new String[7];
int length = week.length;
```
```
length ==> 7
```

長さを超えたアクセス
```java
String[] week = new String[7];
week[7] = "Sun";
```
```
|  例外java.lang.ArrayIndexOutOfBoundsException: Index 7 out of bounds for length 7
|        at (#2:1)
```

## 配列の宣言 / 初期化 / まとめて代入

値を伴う配列の宣言
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
```
```
week ==> String[7] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" }
```

宣言済み配列への代入
```java
String[] week;
week = new String[]{ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
```
```
week ==> null
week ==> String[7] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" }
```

配列を同じ値で埋める
```java
String[] week = new String[7];
Arrays.fill(week, "Sun");
System.out.println(Arrays.toString(week));
```
```
[Sun, Sun, Sun, Sun, Sun, Sun, Sun]
```

配列のindexを用いた値の代入（8+）
```java
int[] numbers = new int[10];
Arrays.setAll(numbers, i -> i * 2);
System.out.println(Arrays.toString(numbers));
```
```
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

配列のindexを用いた並列での値の代入（8+）
```java
int[] numbers = new int[10];
Arrays.parallelSetAll(numbers, i -> i * 2);
System.out.println(Arrays.toString(numbers));
```
```
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

配列の長さを指定したコピー（6+）
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
String[] newWeek1 = Arrays.copyOf(week, 3);
String[] newWeek2 = Arrays.copyOf(week, 8);
```
```
newWeek1 ==> String[3] { "Sun", "Mon", "Tue" }
newWeek2 ==> String[8] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat", null }
```

配列の範囲を指定したコピー（6+）
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
String[] newWeek = Arrays.copyOfRange(week, 2, 4);
```
```
newWeek ==> String[2] { "Tue", "Wed" }
```

## 引数としての配列

引数に渡す配列
```java
void outputArray(String[] strings) {
    System.out.println(Arrays.toString(strings));
}

outputArray(new String[]{ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" });
```
```
[Sun, Mon, Tue, Wed, Thu, Fri, Sat]
```

可変長引数に渡す配列 (5+)
```java
void outputVarArgs(String... strings) {
    System.out.println(Arrays.toString(strings));
}

outputVarArgs("Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat");
```
```
[Sun, Mon, Tue, Wed, Thu, Fri, Sat]
```

## 配列全体に対する処理

配列全体の処理 (旧)
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
for (int i = 0; i < week.length; i ++) {
    System.out.println(week[i]);
}
```
```
Sun
Mon
Tue
Wed
Thu
Fri
Sat
```

配列全体の処理 (5+)
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
for (String day : week) {
    System.out.println(day);
}
```
```
Sun
Mon
Tue
Wed
Thu
Fri
Sat
```

配列全体の処理 (8+)
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
Arrays.stream(week).forEach(System.out::println);
```
```
Sun
Mon
Tue
Wed
Thu
Fri
Sat
```

配列の文字列化
```java
String[] week = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
String result = Arrays.toString(week);
```
```
result ==> "[Sun, Mon, Tue, Wed, Thu, Fri, Sat]"
```

## 配列の利用

配列の検索
```java
int[] numbers = {3, 1, 4, -1, 5, 9, -2, 6, 5 };
int index = Arrays.binarySearch(numbers, 4);
```
```
index ==> 2
```

配列の検索（見つからない場合）
```java
int[] numbers = {3, 1, 4, -1, 5, 9, -2, 6, 5 };
int index = Arrays.binarySearch(numbers, 2);
```
```
index ==> -3
```

2つの配列の比較
```java
int[] numbers1 = {1, 2, 3};
int[] numbers2 = {1, 2, 3};
boolean result = Arrays.equals(numbers1, numbers2);
```
```
result ==> true
```

2つの配列の最初に異なった場所の検索（9+）
```java
int[] numbers1 = {1, 2, 5, 4};
int[] numbers2 = {1, 2, 3, 4};
int result = Arrays.mismatch(numbers1, numbers2);
```
```
result ==> 2
```

2つの配列の最初に異なった場所の大小比較（9+）
```java
int[] numbers1 = {1, 2, 5, 4};
int[] numbers2 = {1, 2, 3, 4};
int result = Arrays.compare(numbers1, numbers2);
```
```
result ==> 1
```

## 配列の加工

配列のソート
```java
int[] numbers = {3, 1, 4, -1, 5, 9, -2, 6, 5 };
Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers));
```
```
[-2, -1, 1, 3, 4, 5, 5, 6, 9]
```

配列の並列ソート（8+）
```java
int[] numbers = {3, 1, 4, -1, 5, 9, -2, 6, 5 };
Arrays.parallelSort(numbers);
System.out.println(Arrays.toString(numbers));
```
```
[-2, -1, 1, 3, 4, 5, 5, 6, 9]
```

配列の要素を蓄積した計算（8+）
```java
int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
Arrays.parallelPrefix(numbers, (x, y) -> x + y);
System.out.println(Arrays.toString(numbers));
```
```
[1, 3, 6, 10, 15, 21, 28, 36, 45, 55]
```

## 紹介しなかったメソッド

- asList
    - Listの章で紹介
- compareUnsigned
    - 符号なし整数の紹介は割愛
- deepEquals / deepHashCode / hashCode / deepToString
    - オブジェクトの扱いは割愛
- spliterator
    - Streamの章で紹介    
