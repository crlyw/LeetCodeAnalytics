# Two Sum II - Input array is sorted

#### Description

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

Input: numbers={2, 7, 11, 15}, target=9

Output: index1=1, index2=2y.

#### Tags
* Array
* Two Pointers
* Binary Search

***

#### Solutions

##### Solution 1: brute-force
```
 public int[] twoSum(int[] numbers, int target) {
    int[] result = new int[2];
    for (int i = 0; i < numbers.length; i++) {
        for (int j = i+1; j < numbers.length; j++) {
            if(numbers[i] + numbers[j] == target){
                result[0] = i+1;
                result[1] = j+1;
                break;
            }
        }
    }
    return result;    
}
```
* Time Complexity: O(n^2)
* Space Complexity: O(1)

##### Solution 2: Binary Search, use binary search to find target-nums[i] behind numbers[i], pay attention here, you should only search target-numbers[i] behind numbers[i] because target-nums[i] shall never appear in front of numbers[i]
```
public int BST(int left, int right, int[]numbers, int target){
    if(left > right){
        return -1;
    }
    int middle = (right -left )/2 + left;
    if(numbers[middle] == target) {
        return middle;
    }else if(numbers[middle] > target){
        return BST(left, middle-1, numbers,target);
    }else{
        return BST(middle+1, right, numbers,target);
    }
}

public int[] twoSum(int[] numbers, int target) {
    int[] result = new int[2];
    int i = 0;
    while(i< numbers.length){
        int temp = BST(i+1, numbers.length-1, numbers, target - numbers[i]);
        if(temp != -1){
            result[0] = i+1;
            result[1] = temp +1;
            break;
        }else if(temp == -1){
            while(numbers[i+1]==numbers[i]){
                i++;
            }
            i++;
        }
    }
    return result;
    
}
```
* Time Complexity: O(nlogn)
* Space Complexity: O(1)
* efficiency: 44.34%

##### Solution 2: Two Pointers
```
public int[] twoSum(int[] numbers, int target) {
    int left = 0;
    int right = numbers.length - 1;

    int[] result = new int[2];
    while (left < right) {
        if (numbers[left] + numbers[right] == target) {
            result[0] = left + 1;
            result[1] = right + 1;
            return result;
        }else if(numbers[left] + numbers[right] < target){
            left++;
        }else{
            right--;
        }
    }
    return result;
}
```
* Time Complexity: O(n)
* Space Complexity: O(1)
* efficiency: 44.34%