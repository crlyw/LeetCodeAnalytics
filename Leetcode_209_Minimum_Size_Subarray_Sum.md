# Minimum Size Subarray Sum

#### Description

Given an array of **n** positive integers and a positive integer s, find the minimal length of a **contiguous** subarray of which the sum ≥ s. If there isn't one, return 0 instead.

For example, given the array [2,3,1,2,4,3] and s = 7,
the subarray [4,3] has the minimal length under the problem constraint.

#### Tags
* Array
* Two Pointers
* Binary Search

***

#### Solutions

##### Use two Pointers to make a scrollable window, in this case the word "contiguous" is very important, because if it is not contiguous, the window shall not work because it could also not be contiguous.

```
public int minSubArrayLen(int s, int[] nums) {
    int l = 0, r = -1; //nums[l...r] two pointer
    int len = nums.length + 1;
    int sum = 0;
    while (l < nums.length) {
        if (r + 1 < nums.length && sum < s) {
            r++;
            sum = sum + nums[r];
        } else {
            sum = sum - nums[l];
            l++;
        }
        if (sum >= s) {
            len = r - l + 1 > len ? len : r - l + 1;
        }
    }
    return len == nums.length + 1 ? 0 : len;
}
```
* Time Complexity: O(n)
* Space Complexity: O(1)
* efficiency: 17.15%

#### Other people's good solution

```
public int minSubArrayLen(int s, int[] a) {
    if (a == null || a.length == 0)
        return 0;

    int i = 0, j = 0, sum = 0, min = Integer.MAX_VALUE;

    while (j < a.length) {
        sum += a[j++];

        while (sum >= s) {
            min = Math.min(min, j - i);
            sum -= a[i++];
        }
    }

    return min == Integer.MAX_VALUE ? 0 : min;
}
```
* Time Complexity: O(n)
* Space Complexity: O(1)
* efficiency: 73.45%