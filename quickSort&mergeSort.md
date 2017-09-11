Quick Sort
----
* 平均时间复杂度是O(nlogn)
* 最坏是O(n^2)， 比如已经排序好，每次选择第一个pivot
* 空间复杂度O(1), in place
* 不具有稳定性
```
public void sortIntegers2(int[] A) {
    // Write your code here
    if (A == null || A.length == 0) {
        return;
    }
    quickSort(A, 0, A.length - 1);
}
private void quickSort(int[] A, int start, int end) {
//如果不加最前面这段if判断语句，会造成stackOverFlow
    if (start >= end) {
        return;
    }
    int left = start;
    int right = end;
    int pivot = A[(start + end) / 2];
    while (left <= right) {
    //注意，left和right这里有等号，而A[left]和pivot这里没有等号，这里是避免了Corner case，比如全是1，如果有等号的话，一直是一个point在移动
        while (left <= right && A[left] < pivot) {
            left++;
        }
        //这里的while循环内部也要写等于号，已经left++, right--都会造成left可能大于right了
        while (left <= right && A[right] > pivot) {
            right--;
        }
        if (left <= right) {
            swap(A, left, right);
            left++;
            right--;
        }
    }
    quickSort(A, start, right);
    quickSort(A, left, end);
}
private void swap(int[] A, int i1, int i2) {
    int temp = A[i1];
    A[i1] = A[i2];
    A[i2] = temp;
}
```


Merge Sort
----
* 时间复杂度是O(nlogn)，没有最好最坏
* 空间复杂度O(n)
* 稳定排序（2(a), 1, 1, 2(b)， 在排序一次，2(a)也能出现在前面）
```
//要采用一个array(temp)去记录排序结果，然后替换到A里面去
public void sortIntegers2(int[] A) {
    // Write your code here
    if (A == null || A.length == 0) {
        return;
    }
    int[] temp = new int[A.length];
    mergeSort(A, 0, A.length - 1, temp);
}
public void mergeSort(int[] A, int start, int end, int[] temp) {
    //important for this to stop, stop for the condition start >= end
    if (start >= end) {
        return;
    }
    int mid = (start + end) / 2;
    mergeSort(A, start, mid, temp);
    mergeSort(A, mid + 1, end, temp);
    merge(A, start, mid, end, temp);
}
private void merge(int[] A, int start, int mid, int end, int[] temp) {
    int left = start;
    int right = mid + 1;
    int index = start;// 注意这里：the start of index of temp is start
    while (left <= mid && right <= end) {
        if (A[left] > A[right]) {
            temp[index++] = A[right++];
        } else{
            temp[index++] = A[left++];
        }
    }
    while (left <= mid) {
        temp[index++] = A[left++];
    }
    while (right <= end) {
        temp[index++] = A[right++];
    }
    for (int i = start; i <= end; i++) {
        A[i] = temp[i];
    } 
}
```
