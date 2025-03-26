
#### Implement **Binary Search** on a Sorted Array

```cpp

```

---

#### Reverse a Linked List

```cpp

```

---

#### Implement a **fixed-size sliding window** that maintains the sum of the last `k` elements in a stream of integers.

```cpp
int maxSumSubarray(vector<int> nums, int k) {
    int maxSum = INT_MIN;
    int currentSum = 0;
    int start = 0;

    for(int end = 0; end < nums.size(); end++) {
        // add current element to the sum 
        currentSum += nums[end];
        
        // when window reaches size k
        if(end - start + 1 == k) {
            maxSum = max(maxSum, currentSum);
            currentSum -= nums[start]; // remove first element of the window 
            start++;
        }
    }
    return maxSum;
}
```

---

#### Implement and Use a Min-Heap in C++
