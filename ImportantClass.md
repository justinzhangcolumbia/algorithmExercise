String
----
### 在做DFS时，String不用进行deep copy,因为每次string + 操作都是产生一个新的string.
### string是不可以被替换的，只能产生一个新的string，然后所有的string都会被放在一个string pool里面，再有重复的就不会创建新的string, 比如String a = a + "123"; 这样的话就会产生一个新的string，而不是覆盖a的值
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
* contains()  可以检查一个string里面是否包含一个substring（例如abc里面是否包含bc, 如果用来检查是否含有某个character用indexOf来检查，返回-1就是不含有
* replace(char target, char replacement) replace所有的
* replaceAll(String target, String replacement)
* replaceFirst(String target, String replacement) 只replace第一个。

StringBuilder
----
### 在做DFS的时候必须要进行deep copy，因为stringbuilder在append的时候不会产生新的object
* append()
* charAt()
* delete(int startIndex, int endIndex) 返回的是stringbuilder
* deleteCharAt()
* indexOf(str)
* insert(int offset, str/char/boolean/int...)
* length()
* substring()返回的是string
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
* clear()

HashSet(hashSet不能放入重复的元素)
----
* add()
* contains()
* isEmpty()
* remove()
* size()
* clear()

ArrayList(是可以添加null的element的，但是queue不行，所以arrayList有时可以替代queue进行使用)
----
* add(e); add(index, e)
* contains(object)
* get(index)
* indexOf(Object)
* isEmpty()
* remove(index); remove(Object)
* removeRange(int startIndex, int toIndex)
* removeAll(Collection)
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

PriorityQueue
----
* add()
* clear()
* contains(Object)
* offer()
* peek()
* poll()
* remove(Object)
* size()
* toArray();

Math
----
* abs()
* max()
* min()
* sqrt()
* power(x, y) x的y次方
* random() [0.0 1.0)
* log()

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

sort, reverse
----
* Arrays.sort()
* Collections.reverse(List<?> list)
* Collections.reverseOrder(Comparator<T> cmp)
