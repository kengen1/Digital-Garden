*Kadane's Algorithm is a **Dynamic Programming** approach used to find the maximum sum subarray in a given array of integers.

#### Greedy Application
Kadane's Algorithm is a good fit for greedy problems because:
- at each step, it makes a greedy choice by deciding whether to extend the current subarray or start a new one
- **Linear time complexity**: provides an O(n) solution as opposed to brute force approaches that may result in O(n^2) or O(n^3) in some cases
- **Constant space complexity**: since we are only maintaining two variables to track the maximum sum and the current sum

#### Pseudocode

```
func Kadanes(arr):
	maxSum = minINT
	currentSum = 0

	for each element in arr
		currentSum = max(element, currentSum + element)
		maxSum = max(maxSum, currentSum)

	return maxSum
```

#### C++ Implementation

```cpp
int kadane(vector<int>& arr) {
    int maxSum = INT_MIN;
    int currentSum = 0;

    for (int num : arr) {
        currentSum = max(num, currentSum + num);
        maxSum = max(maxSum, currentSum);
    }

    return maxSum;
}
```