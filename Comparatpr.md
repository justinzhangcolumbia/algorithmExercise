重新定义Arrays.sort()的comparator
----
如果要从小到大排序，就是返回a-b的值就可以，前面减去后面
```
Arrays.sort(Pair, new Comparator<Pair>(){
  @Override
  public int compare(Pair a, Pair b) {
    return a.sum - b.sum;
  }
});
```

重新定义PriorityQueue(heap)
----
这里的排序要求是先按照离origin的远近排序，如果一样就按照x坐标排序，如果x坐标也一样，那就按照y坐标排序
```
PriorityQueue<Point> pq = new PriorityQueue<Point>(k, new Comparator<Point>() {
    @Override
    public int compare(Point a, Point b) {
        int diff = distance(a, globalOrigin) - distance(b, globalOrigin);
        if (diff == 0) {
            diff = a.x - b.x;
        }
        if (diff == 0) {
            diff = a.y - b.y;
        }
        return diff;
    }
});
```

在外面定义Comparator，然后可以重复调用
```
public Comparator<Element> newComparator = new Comparator<Element>() {
    public int compare(Element a, Element b) {
        if (a.count != b.count) {
            return a.count - b.count;
        }
        return b.word.compareTo(a.word);
    }
};
```
先按照a和b的count进行排序，如果一样，就按照a和b的字母进行排序。
```
PriorityQueue<Element> pq = new PriorityQueue<Element>(k, newComparator);
```
