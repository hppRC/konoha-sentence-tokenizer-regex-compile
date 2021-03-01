# Konoha 検証用リポジトリ

## 動作環境


```
MacBook Pro (16-inch, 2019)
2.4 GHz 8-Core Intel Core i9
32 GB 2667 MHz DDR4
Macintosh HD
```

```
Python 3.8.2 (default, Apr 13 2020, 16:24:13)
[Clang 11.0.3 (clang-1103.0.32.29)] on darwin
```

## 評価方法

for文で100,000回文の改行区切りを行う。
評価対象は以下の通り。

- do_nothing: オーバーヘッドの確認のため、ループを回すだけのスクリプト
- compile_alwasy: SentenceTokenizer#tokenize()が呼ばれるたびにコンパイルを行う
- no_compile: コンパイルをせず、raw文字列を渡す
- pre_compile: 事前にコンパイル済みの正規表現オブジェクトを格納しておく


実行コマンド

```bash
time python do_nothing.py
time python compile_always.py
time python no_compile.py
time python pre_compile.py
```

## 実行時間

### do_nothing

| Executed in | 90.23 millis |          fish |     external |
| ----------- | -----------: | ------------: | -----------: |
| usr time    | 45.31 millis | 105.00 micros | 45.20 millis |
| sys time    | 38.16 millis | 479.00 micros | 37.68 millis |

### compile_always

| Executed in | 879.63 millis |          fish |      external |
| ----------- | ------------: | ------------: | ------------: |
| usr time    | 826.11 millis | 115.00 micros | 826.00 millis |
| sys time    |  41.67 millis | 707.00 micros |  40.97 millis |

### no_compile

| Executed in | 743.88 millis |          fish |      external |
| ----------- | ------------: | ------------: | ------------: |
| usr time    | 642.70 millis | 136.00 micros | 642.57 millis |
| sys time    |  52.06 millis | 550.00 micros |  51.51 millis |

### pre_compile

| Executed in | 573.41 millis |          fish |      external |
| ----------- | ------------: | ------------: | ------------: |
| usr time    | 525.01 millis | 158.00 micros | 524.85 millis |
| sys time    |  41.56 millis | 755.00 micros |  40.81 millis |

