*A prefix sum array, also known as a cumulative sum array, is a derived array that stores the cumulative sum of elements in a given array. 
Each element in the prefix sum array represents the sum of all elements up to that index in the original array.*

Commonly used in:
- Array-based problems
- Cumulative frequency counting
- Dynamic programming optimizations

### Example

Given an array:
A=[3,2,7,1,8,4]

Its **prefix sum array P** is:
P=[3,5,12,13,21,25]


### Code Implementation

```cpp
	vector<int> computePrefixSum(const std::vector<int>& A) { 
		int n = A.size(); 
		vector<int> P(n); P[0] = A[0]; 
		// Base case 
		for (int i = 1; i < n; ++i) { 
			P[i] = P[i - 1] + A[i]; // Cumulative sum 
		} 
		return P; 
	}
```