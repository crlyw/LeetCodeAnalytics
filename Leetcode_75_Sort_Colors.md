# Sort Colors

#### Description

Given an array with n objects colored red, white or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

##### Note:
You are not suppose to use the library's sort function for this problem.

#### Tags
* Array
* Two Pointers
* Sort

***

#### Solutions

##### Solution 1: Count Sort. (Implemented when the elements in the array are in a specific range)
```
public void sortColors(int[] nums) {
	//Count Sort
  	int redColor = 0;
   	int whiteColor = 0;
   	int blueColor = 0;
  	for (int i = 0; i < nums.length; i++) {
   		switch (nums[i]){
      		case 0:
        		redColor++;
            	break;
         	case 1:
            	whiteColor++;
            	break;
         	case 2:
            	blueColor++;
             	break;
        	default:
             	break;
       	}
  	}

    for (int i = 0; i < redColor; i++) {
        nums[i] = 0;
    }

    for (int i = redColor; i <redColor + whiteColor; i++) {
        nums[i] = 1;
    }

    for (int i = redColor + whiteColor; i < nums.length; i++) {
        nums[i] = 2;
    }
}
```
* Time Complexity: O(n)
* Space Complexity: O(1) 
* efficiency: 6.63%

##### Solution 2 : two pointers, divide the array into three parts
```
public void sortColors(int[] nums) {

    //two pointers

    int zero = -1; //nums[0...zero]==0
    int two = nums.length; //nums[two...n-1]==2
    for (int i = 0; i < two; ) {
        if (nums[i] == 1) {
            i++;
        } else if (nums[i] == 2) {
            two--;
            int temp = nums[two];
            nums[two] = nums[i];
            nums[i] = temp;
        } else {
            zero++;
            int temp = nums[zero];
            nums[zero] = nums[i];
            nums[i] = temp;
            i++;
        }
    }
}
```

* Time Complexity: O(n)
* Space Complexity: O(1)
* efficiency: 64.04%