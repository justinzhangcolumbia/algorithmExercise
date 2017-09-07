HashTables:
----
* key is unique

ArrayList(Dynamically Resizing Array)
---
* 容量满了以后就double，每次double话费O(n)时间

StringBuilder
----
* 直接使用String + String的时间复杂度是O(n^2*x) (假设x个相同长度为n的字符串相连)
* 用S同日那个Builder的时间复杂度是O(n*x)


## 1.1 
1. ask: String是ASCII还是Unicode，如果是ASCII，那么每个字符都由8位二进制构成，是一个字节(byte), 一共有256种组合，而unicode的数量更加大。

## 1.3 permutation['pɝmjʊ'teʃən]排列
1. ask: permutation comparison is case senstive?(dog & Dog)
   ask: whilespace is significant? ("dog" & "dog    ")
   ask: ASCII ?
2. solution: 一开始想到的是sort，然后比较等价性，还可以统计每个字符的出现的数量，两个string该数量相等就是可以等价的

## 1.4
1. 题目规定了只能用char array, 用两边走的方法，第一遍得到有多少个空格，计算真实长度应该是多少，第二遍从后往前进行，能实现in place。
