# Two Sum

#### Description

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

#### Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

#### Tags
* Array
* Hash Table

***

#### My original solutions

``` Java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums.length; j++) {
                if(nums[i] + nums[j] == target && i!=j){
                    return new int[]{i,j};
                }
            }
        }
        return new int[]{-1,-1};
    }
}
```
* Time Complexity: O(n^2)
* Space Complexity: O(1)

##### Analysis
To solve this problem, I used brute-force, since the array was **not notified to be sorted**, so binary search was not useful here, the time complexity is n^2 level, so the efficiency is not good.

***

#### Other people's good solution

``` Java
public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target - nums[i])) {
                result[1] = i;
                result[0] = map.get(target - nums[i]) - 1;
                return result;
            }
            map.put(nums[i], i + 1);
        }
        return result;
    }
```
* Time Complexity: O(n)
* Space Complexity: O(1)

##### Analysis
This method used the search table method, put the indexes and values into a map, significantly decrease the time complexity, and easy to understand, but pay attentation, please **regard the value of array to be the key**.
