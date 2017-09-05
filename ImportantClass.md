
HashMap
----
* containsValue()
* get(key)
* isEmpty()
* keySet()
* put(key, value)
* remove(key)
* size()

HashSet(hashSet不能放入重复的元素)
----
* add()
* contains()
* isEmpty()
* remove()
* size()

ArrayList
----
* add(e); add(index, e)
* contains(object)
* get(index)
* indexOf(Object)
* isEmpty()
* remove(index); remove(Object)
* set(index, element)
* size()
* subList()
* toArray()

Stack
----
* empty()
* peek()  empty报错
* pop() empty报错
* push()
* search(Object)

Queue
----
* isEmpty()
* peek()  empty return null
* poll() empty return null
* offer()
* element() empty报错
* remove() empty报错
* size()

Math
----
* abs()
* max()
* min()
* sqrt()
* power(x, y) x的y次方
* random() [0.0 1.0)

Integer
----
* MIN_VALUE: -2147483648
* MAX_VALUE: 2147483647

数据类型之间的转换
----
* String --> int:     Integer.parseInt() (return int); Integer.valueOf() (return Integer)
* other  --> String:  String.valueOf()
* char   --> int:     Character.getNumericValue(); 'a' - '0'
* int    --> char:    (char)
* 判断String等价性要用equals而不能用==

