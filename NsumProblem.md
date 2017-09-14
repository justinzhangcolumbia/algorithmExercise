注意输出结果形势是什么？是要求index？还是要求是否存在？注意处理两个数字相等的情况（4+4=8）
----
2sum(unsorted)
----
* HashMap, if there is no two numbers' sum is target, return {0, 0}
* 时间：O(n)
* 空间：O(n)
````
public int[] twoSum(int[] numbers, int target) {
    // write your code here
    if (numbers == null || numbers.length == 0) {
        return new int[0];
    }

    int[] result = new int[2];
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < numbers.length; i++) {
    //for the condition of 4,4 and target = 8
        if (map.containsKey(numbers[i])) {
            if (numbers[i] + numbers[i] == target) {
                sortResult(map.get(numbers[i]), i, result);
                return result;
            }
        } else {
            map.put(numbers[i], i);
        }
    }

    for (int i = 0; i < numbers.length; i++) {
        int remain = target - numbers[i];
        //for the condition of 4,4 and target = 8
        if (remain == numbers[i]) {
            return new int[2];
        }
        if (map.containsKey(remain)) {
            sortResult(i, map.get(remain), result);
            return result;
        }
    }
    return result;

}
private void sortResult(int index1, int index2, int[] result) {
    result[0] = index1 + 1;
    result[1] = index2 + 1;
    Arrays.sort(result);
}
````

2sum(sorted)
----
1. binary search
* 时间：O(nlogn), 重复n次binary search
* 空间：O(1)
2. two pointers
* 时间：O(n)
* 空间：O(1)
```
public int[] twoSum(int[] nums, int target) {
    // write your code here
    int left = 0;
    int right = nums.length - 1;
    int[] result = new int[2];
    while (left < right) {
        if (nums[left] + nums[right] < target) {
            left++;
        } else if (nums[left] + nums[right] > target) {
            right--;
        } else {
            result[0] = left + 1;
            result[1] = right + 1;
            return result;
        }
    }
    return result;
}
```
