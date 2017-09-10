String
----
* charAt()
* compareTo()
* concat(); +
* equals()
* indexOf()
* length()
* split(), 返回值是String[]
* substring(), substring(int beginIndex),可以定义一个参数也可以定义两个
* toCharArray()
* toLowerCase()
* toUpperCase()
* toString()
* valueOf()

StringBuilder
----
* append()
* charAt()
* delete(int startIndex, int endIndex)
* deleteCharAt()
* indexOf(str)
* insert(int offset, str/char/boolean/int...)
* length()
* substring()
* toString()

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

ArrayList(是可以添加null的element的，但是queue不行，所以arrayList有时可以替代queue进行使用)
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
* 交换arrayList的两个变量用set
```
int temp1 = nums.get(index1);
int temp2 = nums.get(index2);
nums.set(index1, temp2);
nums.set(index2, temp1);
```
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

