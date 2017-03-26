# Move Zeroes

#### Description

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

##### Note:
1. You must do this in-place without making a copy of the array.

2. Minimize the total number of operations.

#### Tags
* Array
* Two Pointers

***

#### Solutions

##### Solution 1: get all the non-zero number and put them in the front, later on put all 0s in the end.
```
public void moveZeroes(int[] nums) {
	ArrayList<Integer> nonZeroElements = new ArrayList<Integer>();
   	for (int i = 0; i < nums.length; i++) {
   		if(nums[i] != 0){
       	nonZeroElements.add(nums[i]);
       }
   	}

   	for (int i = 0; i < nonZeroElements.size(); i++) {
  		nums[i] = nonZeroElements.get(i);
   	}

 	for (int i = nonZeroElements.size(); i < nums.length; i++) {
    	nums[i] = 0;
  	}
}
```
* Time Complexity: O(n)
* Space Complexity: O(n) [Array will open n-space]
* efficiency: 14.08%

##### Solution 2 (my solution): find the 0 and swap with the nonzero behind it, no extra space will be created.

```
public void moveZeroes(int[] nums) {
	int length = nums.length;
   	for(int i = length-1; i >=0; i--){
   		if(nums[i]==0) {
         	for (int j =i; j<length-1;j++){
           	if(nums[j+1]!=0){
                 int temp = nums[j+1];
                 nums[j+1] = nums[j];
                 nums[j] = temp;
				}
         	}
      	}
 	}
}
```

* Time Complexity: O(n^2)
* Space Complexity: O(1)
* efficiency: 4.01%

##### Solution 3: Two pointers, one pointer represents the literation of the array and one pointer represents the zero

```
public void moveZeroes(int[] nums) {

	int k = 0; //in nums, [0...k)has no zero element

  	//When traverse i-th element, make sure[0...i] has no zero element
  	//All the elements keep the order in [0...k)
  	//[k...i) shall be all zeros
  	for (int i = 0; i < nums.length; i++) {
   		if(i!=k){
     		int temp = nums[k];
      		nums[k] = nums[i];
    		nums[i] = temp;
         	k++;
      	}else{
         	k++;
    	}
  	}
}
```

* Time Complexity: O(n)
* Space Complexity: O(1)
* efficiency: 69.67%